---
description: The ilert Icinga Integration helps you to easily connect ilert with Icinga.
---

# Icinga Integration

[Icinga](https://icinga.com/) is an open-source, scalable, and extensible monitoring system that checks the availability of your network resources, notifies users of outages, and generates performance data for reporting. With the ilert Icinga Notification Plugin, you can easily integrate Icinga with ilert and extend your existing Icinga with advanced alerting by SMS, phone calls, and push notifications as well as on-call schedules.

## System requirements <a href="#requirements" id="requirements"></a>

* Icinga 2.x.
* Python >= 3.7 (alternatively Python >= 2.7.9, we suggest 2.7.10)

{% hint style="warning" %}
Python 2.x is EOL (end of life) we suggest to use Python >= 3.7
{% endhint %}

> Are you using Icinga 1.x? Please refer to our [Nagios integration guide](nagios.md).

## In ilert: Create an Icinga alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Icinga** in the search field, click on the Icinga tile and click on **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Icinga: Install notification plugin <a href="#in-icinga" id="in-icinga"></a>

1. Download the [ilert Icinga plugin](https://github.com/iLert/ilert-icinga) and unzip it

```bash
wget https://github.com/iLert/ilert-icinga/releases/latest/download/ilert-icinga.zip
unzip ilert-icinga.zip
```

2. Move the plugin file `ilert-icinga.py` into the `/usr/local/bin` directory

{% tabs %}
{% tab title="Python 3.7 (or higher)" %}
```bash
mv ilert-icinga.py /usr/local/bin > chmod 755 /usr/local/bin/ilert-icinga.py
```
{% endtab %}

{% tab title="Python 2.7.9 (or higher)" %}
```bash
cd python2
mv ilert-icinga.py /usr/local/bin > chmod 755 /usr/local/bin/ilert-icinga.py
```
{% endtab %}
{% endtabs %}

> The file must be executable by both Icinga and the cron daemon

3. Open the plugin configuration file `ilert-icinga.conf` and paste the **API Key** in the pager field of the user definition, e.g.

```
object User "ilert" {
  display_name = "iLert"
  groups = [ "icingaadmins" ]
  states = [ OK, Warning, Critical, Unknown]
  types = [ Problem, Recovery, Acknowledgement ]
  vars.additional_notes = "This user maps to an alert source in ilert."
  pager = "12345678-abcd-efgh-ijkl-87654321"
}
```

4. Copy the file to the Icinga configuration directory (varies depending on the installation)

{% tabs %}
{% tab title="Python 3.7 (or higher)" %}
```bash
mv ilert-icinga.conf /etc/icinga2/conf.d/
```
{% endtab %}

{% tab title="Python 2.7.9 (or higher)" %}
```bash
cd python2
mv ilert-icinga.conf /etc/icinga2/conf.d/
```
{% endtab %}
{% endtabs %}

5. _Optional:_ You can enable ilert as a notification contact using `vars.notification.enable_ilert = true` attribute in host and service definitions. To enable ilert for all hosts and services, add the attribute to the template `/etc/icinga2/conf.d/templates.conf`

```
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

6. Edit the crontab file from the icinga user

```bash
crontab -u icinga -e
```

7. Add the following entry:

{% tabs %}
{% tab title="Python 3.7 (or higher)" %}
```bash
* * * * * python3 /usr/local/bin/ilert-icinga.py -m send
```
{% endtab %}

{% tab title="Python 2.7.9 (or higher)" %}
```bash
* * * * * /usr/local/bin/ilert-icinga.py -m send
```
{% endtab %}
{% endtabs %}

> Via this cron job, events are sent to ilert every minute that failed in the first send attempt (e.g. due to a network error).

8. Restart Icinga:

```bash
/etc/init.d/icinga restart
```

9. After server restart you should see the ilert user in Icinga

![](../../.gitbook/assets/ici4.png)

## FAQ <a href="#faq" id="faq"></a>

**Which Icinga** [**Notification Types**](https://icinga.com/docs/icinga2/latest/doc/09-object-types/#notification) **are processed by the plugin?**

The plugin processes the notification types `PROBLEM` , `ACKNOWLEDGEMENT` and `RECOVERY` . The notification types `FLAPPING*` and `DOWNTIME*` are ignored.

**What happens if my internet connection is lost? Are the events generated in Icinga lost?**

There are no events lost. Because the plugin stores the events locally in a temporary directory (by default in /tmp/ilert-icinga ) and tries to send them to ilert every minute. This means that as soon as your connection is available again, cached events will be sent to ilert. In addition, we recommend that you monitor your Internet connection using our [Heartbeats ](../../alerting/heartbeat-monitoring/)feature.

**Can I override the alert source default alert priority via the Icinga plugin?**

Yes, use `ICINGA_PRIORITY` variable in the notification command template and set it to `LOW` or `HIGH` e.g.

{% tabs %}
{% tab title="Python 3.7 (or higher)" %}
```
object NotificationCommand "ilert-notification" {
  import "plugin-notification-command"

  command = "python3 /usr/local/bin/ilert-icinga.py --mode save"

  env = {
    ICINGA_PRIORITY = "LOW"
    ...
  }
}
```
{% endtab %}

{% tab title="Python 2.7.9 (or higher)" %}
```
object NotificationCommand "ilert-notification" {
  import "plugin-notification-command"

  command = "/usr/local/bin/ilert-icinga.py --mode save"

  env = {
    ICINGA_PRIORITY = "LOW"
    ...
  }
}
```
{% endtab %}
{% endtabs %}

**Does the plugin also support Icinga 1.x?**

No, you should use the [ilert Nagios Integration](nagios.md).

**The plugin does not work. How do I find the mistake?**

Please look first in the log file. The plugin uses the Unix / Linux system log for logging (eg under `/var/log/messages` or `/var/log/syslog` ). If you can not find the error, please contact our support at [support@ilert.com](mailto:support@ilert.com).

**I received the following error: `import urllib.request ImportError: No module named request.`**\
\
This error message indicates that you are using the Python 3 script with Python 2. Please make sure that you are using the correct Python 2 script:

```
> cd python2 
> mv ilert-icinga.py /usr/local/bin > chmod 755 /usr/local/bin/ilert-icinga.py
```
