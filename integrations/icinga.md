---
title: Icinga Integration
seoTitle: 'iLert: Icinga Integration for Alerting | Incident Response | Uptime'
description: The iLert Icinga Integration helps you to easily connect iLert with Icinga.
date: '2020-05-19T04:02:05.000Z'
weight: 1
---

# Icinga Integration

With the iLert Icinga Notification Plugin, you can easily integrate Icinga with iLert and extend your existing Icinga with advanced alerting by SMS, phone calls, and push notifications as well as on-call schedules.

## System requirements <a id="requirements"></a>

* Icinga 2.x.
* Python 2.7.3 \(or higher\)

> Are you using Icinga 1.x? Please refer to our [Nagios integration guide](nagios.md).

## In iLert: create Icinga alert source <a id="create-alarm-source"></a>

1. Go to the "Alert sources" tab and click "Add a new alert source"

![](../.gitbook/assets/ici1.png)

1. Enter a name and select your desired escalation policy. Select "Icinga 2.x" as the **Integration Type** and click **Save**.

![](../.gitbook/assets/ici2.png)

1. On the next page, an API Key is generated. You will need this **API Key** below when setting up the Icinga Plugin.

![](../.gitbook/assets/ici3.png)

## In Icinga: install notification plugin <a id="in-icinga"></a>

1. Download the [iLert Icinga plugin](https://github.com/iLert/ilert-icinga) and unzip it

```bash
wget https://github.com/iLert/ilert-icinga/releases/latest/download/ilert-icinga.zip
unzip ilert-icinga.zip
```

1. Move the plugin file `ilert-icinga.py` into the `/usr/local/bin` directory 

```bash
mv ilert-icinga.py /usr/local/bin > chmod 755 /usr/local/bin/ilert-icinga.py
```

> The file must be executable by both Icinga and the cron daemon

1. Open the plugin configuration file `ilert-icinga.conf` and paste the **API Key** in the pager field of the user definition, e.g.

```text
object User "ilert" {
  display_name = "iLert"
  groups = [ "icingaadmins" ]
  states = [ OK, Warning, Critical, Unknown]
  types = [ Problem, Recovery, Acknowledgement ]
  vars.additional_notes = "This user maps to an alert source in iLert."
  pager = "12345678-abcd-efgh-ijkl-87654321"
}
```

1. Copy the file to the Icinga configuration directory \(varies depending on the installation\)

```bash
mv ilert-icinga.conf /etc/icinga2/conf.d/
```

5: _Optional:_ You can enable iLert as a notification contact using `vars.notification.enable_ilert = true` attribute in host and service definitions. To enable iLert for all hosts and services, add the attribute to the template `/etc/icinga2/conf.d/templates.conf`

```text
template Host "generic-host" {
 max_check_attempts = 5
 check_interval = 1m
 retry_interval = 30s 
 check_command = "hostalive"  

 vars.notification.enable_ilert = true
} 

template Service "generic-service" {
 max_check_attempts = 3
 check_interval = 1m
 retry_interval = 30s  

 vars.notification.enable_ilert = true 
}
```

1. Edit the crontab file from the icinga user

```bash
crontab -u icinga -e
```

1. Add the following entry:

```bash
* * * * * /usr/local/bin/ilert-icinga.py -m send
```

> Via this cron job, events are sent to iLert every minute that failed in the first send attempt \(e.g. due to a network error\).

1. Restart Icinga:

```bash
/etc/init.d/icinga restart
```

1. After server restart you should see the iLert user in Icinga

![](../.gitbook/assets/ici4.png)

## FAQ <a id="faq"></a>

**Which Icinga** [**Notification Types**](https://icinga.com/docs/icinga2/latest/doc/09-object-types/#notification) **are processed by the plugin?**

The plugin processes the notification types `PROBLEM` , `ACKNOWLEDGEMENT` and `RECOVERY` . The notification types `FLAPPING*` and `DOWNTIME*` are ignored.

**What happens if my internet connection is lost? Are the events generated in Icinga lost?**

There are no events lost. Because the plugin stores the events locally in a temporary directory \(by default in /tmp/ilert-icinga \) and tries to send them to iLert every minute. This means that as soon as your connection is available again, cached events will be sent to iLert. In addition, we recommend that you monitor your Internet connection using our uptime monitoring feature.

**Can I override the alert source default alert priority via the Icinga plugin?**

Yes, use `ICINGA_PRIORITY` variable in the notification command template and set it to `LOW` or `HIGH` e.g.

```text
object NotificationCommand "ilert-notification" {
  import "plugin-notification-command"

  command = "/usr/local/bin/ilert-icinga.py --mode save"

  env = {
    ICINGA_PRIORITY = "LOW"
    ...
  }
}
```

**Does the plugin also support Icinga 1.x?**

No, you should use the [iLert Nagios Integration](nagios.md).

**The plugin does not work. How do I find the mistake?**

Please look first in the log file. The plugin uses the Unix / Linux system log for logging \(eg under `/var/log/messages` or `/var/log/syslog` \). If you can not find the error, please contact our support at [support@ilert.com](mailto:support@ilert.com).

