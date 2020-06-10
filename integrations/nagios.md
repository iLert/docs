---
title: Nagios Integration
seoTitle: 'iLert: Nagios Integration for Alerting | Incident Response | Uptime'
description: The iLert Nagios Integration helps you to easily connect iLert with Nagios.
date: '2018-12-29T05:02:05.000Z'
weight: 1
---

# Nagios Integration

With the iLert Nagios Notification Plugin, you can easily integrate Nagios with iLert and extend your existing Nagios system \(and other Nagios forks\) with advanced alerting by SMS, phone calls, and push notifications as well as on-call schedules.

## System requirements <a id="requirements"></a>

* Nagios 2 \(or higher\)
* Python 2.7.3 \(or higher\)

## In iLert: create Nagios alert source <a id="create-alarm-source"></a>

1. Create a new alert source in iLert
2. From the tool integration menu, select the type Nagios and click save.
3. An API key is generated. You will need the API key below when setting up the plugin.

## In Nagios: install the notification plugin <a id="installation-guide"></a>

Download the [iLert Nagios plugin](https://github.com/iLert/ilert-nagios) and unzip it:

```text
> wget https://github.com/iLert/ilert-nagios/archive/v1.5.zip
> unzip ilert-nagios-1.5.zip
```

Put the plugin file `nagios_ilert.py` in the directory `/usr/local/bin`. The file must be executable by both Nagios and the cron daemon:

```text
 > mv ilert_nagios.py /usr/local/bin > chmod 755 /usr/local/bin/ilert_nagios.py
```

In Nagios, enable the macro [`enable_environment_macros`](http://nagios.sourceforge.net/docs/3_0/configmain.html#enable_environment_macros) \(if not already active\). Open your Nagios configuration file `nagios.cfg` and set the value to 1:

```text
enable_environment_macros=1
```

If you have a larger Nagios installation and don't want to enable the macro `enable_environment_macros`, see the `ilert_nagios.cfg` configuration file for further information on how to this.

Open the plugin configuration file `ilert_nagios.cfg` and enter the API key in the pager field of the contact definition, eg:

```text
define contact {
    contact_name                    ilert
    alias                           iLert
    service_notification_period     24x7
    host_notification_period        24x7
    service_notification_options    w,u,c,r
    host_notification_options       d,r
    service_notification_commands   notify-ilert
    host_notification_commands      notify-ilert
    pager                           <YOUR-API-KEY>
}
```

Copy the file into the Nagios configuration directory \(varies depending on the Nagios installation\).

```text
 > cp ilert_nagios.cfg /etc/nagios/conf.d/
```

Depending on the installation of Nagios, there is a `nagios.cfg` file in which you must integrate the iLert configuration file. The entry in `nagios.cfg` would look like this for this example:

```text
 cfg_file=/etc/nagios/conf.d/ilert_nagios.cfg
```

Add the iLert contact to your Nagios contact group. If you are using the Nagios defaults, open the `contacts.cfg` file for the iLert contact:

```text
define contactgroup{
    contactgroup_name admins
    alias Nagios Administrators
    members nagiosadmin, ilert
}
```

Edit the crontab file from the nagios user

```text
 > crontab -u nagios -e
```

Add the following entry:

```text
 * * * * * /usr/local/bin/ilert_nagios.py -m send
```

Via this cron job, events are sent to iLert every minute that failed in the first send attempt \(e.g. due to a network error\).

Restart Nagios:

```text
 > /etc/init.d/nagios restart
```

## FAQ <a id="faq"></a>

**Which Nagios** [**Notification Types**](http://nagios.sourceforge.net/docs/3_0/notifications.html) **are processed by the plugin?**

The plugin processes the notification types `PROBLEM` , `ACKNOWLEDGEMENT` and `RECOVERY` . The notification types `FLAPPING*` and `DOWNTIME*` are ignored.

**What happens if my internet connection is interrupted? Are the events generated in Nagios lost?**

No, events won't be lost. The plugin stores the events locally in a temporary directory \(by default in /tmp/ilert\_nagios\) and tries to send them to iLert every minute. This means that as soon as your connection is available again, cached events will be sent to iLert. In addition, we recommend that you monitor your Internet connection using our uptime monitoring feature.

**The plugin does not work. What can I do?**

Please take a look at the log first. The plugin uses the Unix / Linux system log for logging \(e.g. under `/var/log/messages` or `/var/log/syslog` \). If you cannot find the error, please contact our support at [support@ilert.com](mailto:support@ilert.com).

