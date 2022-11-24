---
title: Zabbix Native Integration
seoTitle: 'iLert: Zabbix Integration for Alerting | Incident Response | Uptime'
date: '2020-07-02T08:02:05.000Z'
weight: 1
description: The ilert Zabbix Integration helps you to easily connect ilert with Zabbix.
---

# Zabbix 4.4+ Integration

## System Requirements <a href="#requirements" id="requirements"></a>

{% hint style="info" %}
Are you using Zabbix 4.3 or lower? Please refer to our [Zabbix 2.2 - 4.3 Integration](script.md) guide.
{% endhint %}

* Zabbix 4.4+

## In ilert: Create an alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1. Go to **Alert sources** and click on **Add a new alert source**.

![](../../.gitbook/assets/zbn1.png)

1. Set a name (e.g. "Zabbix") and select your desired escalation policy.
2. Set the **Integration type** to Zabbix.

![](../../.gitbook/assets/zbn2.png)

1. An API key is generated on the next page. You will need the API key below when creating an ilert user in Zabbix.

![](../../.gitbook/assets/zbn3.png)

## In Zabbix <a href="#zabbix" id="zabbix"></a>

### Import ilert media type (optional as of Zabbix 5.0.4)

{% hint style="info" %}
**Are you using Zabbix 5.0.4 or higher?**

You can skip this section, if you're using Zabbix 5.0.4+, because as of Zabbix 5.0.4, the ilert media type is included in the distribution Zabbix.
{% endhint %}

1. Download the ilert Zabbix Media Type file from the Zabbix repository&#x20;

```
curl -o media_ilert.xml \
   https://raw.githubusercontent.com/iLert/ilert-zabbix/master/media_ilert.xml
```

1. Go to the **Administration → Media types** tab and click the **Import** button.

![](../../.gitbook/assets/zbn4.png)

1. Select import file `media_ilert.xml` and click the **Import** button at the bottom to import the ilert media type.

![](../../.gitbook/assets/zbn5.png)

1. **Optional**: Go to **Media types** and open the imported **iLert** media type. You can overwrite the default alert summary with a custom template using the `.ILERT.INCIDENT.SUMMARY` variable e.g. `{TRIGGER.NAME}: {TRIGGER.STATUS} for {HOST.HOST}`

![](../../.gitbook/assets/6.png)

1. Click on the **Update** button to save the media type.

### Create ilert user and group

1. Go to the **Administration → User groups** tab and click on the **Create user group** button.

![](../../.gitbook/assets/zbn7.png)

1. Set the name for the ilert group (eg. "ilert group").

![](../../.gitbook/assets/zbn8.png)

1. Switch to the **Permissions** tab and select the **host groups** that the ilert group should have read access to, for sending notifications. Without read access, ilert cannot receive notifications for the hosts in the group (see also [here](https://www.zabbix.com/documentation/4.4/manual/quickstart/notification)).
2. Click the **Add** button to save the group.

![](../../.gitbook/assets/zbn9.png)

1. Switch to the Users tab and click on the **Create user** button.

![](../../.gitbook/assets/zbn10.png)

1. Assign an **alias** and **name** and add the user to the ilert group. No further details such as a password are required as this user will not log in to Zabbix.

![](../../.gitbook/assets/zbn11.png)

1. Switch to the **Media** tab and click on the **Add** link
2. In the **media** window, select ilert as **Type**
3. In the **Send to** field enter the alert source api key that you generated in ilert
4. Click the **Add** button

![](../../.gitbook/assets/9.png)

1. Click the **Add** button in the **Users** tab to save the user.

![](../../.gitbook/assets/zbn13.png)

### Create alert action

1. Switch to the **Configuration → Actions** tab and click the **Create action** button

![](../../.gitbook/assets/zbn14.png)

1. Give the action a name, eg "ilert notifications".

![](../../.gitbook/assets/zbn15.png)

1. Perform the following actions on the **Operations**, **Recovery operations** and **Acknowledgment operations** tabs

![](../../.gitbook/assets/zbn16.png)

1. Change the default subject and default message if you want.
2. Click on the **New** link under **Operations** and select the **iLert** group created above under Send to User groups.

![](../../.gitbook/assets/zbn17.png)

1. Click the **Add** button to save the action

## Mapping Zabbix problem severity to alert priority <a href="#faq" id="faq"></a>

ilert supports a mapping configuration for your Zabbix alert source that allows you to map the standard Zabbix severities to ilert priorities. Just enable the checkbox for **Priority mapping** under Zabbix settings.

![](<../../.gitbook/assets/image (55) (2).png>)

## Bidirectional sync (acknowledges alerts in Zabbix) <a href="#faq" id="faq"></a>

As the Zabbix API allows for problems to be acknowledged, ilert offers a setting to configure your Zabbix alert source in bidirectional mode. This will automatically create a connector and alert action for your alert source that will pipe accept events from ilert to Zabbix and acknowledge the problem related to the ilert alert.

![](<../../.gitbook/assets/image (56) (2).png>)

Enable the **Bidirectional** checkbox during your alert sources creation.\
The **Url** and **Api key** will show up under Zabbix settings, please provide both and create your alert source. You will see that a connector and alert action have been setup automatically for your alert source.

{% hint style="info" %}
You cannot add bidirectional mode after an alert source has already been created. You will have to create a new alert source. Bidirectional mode cannot be enabled through the API.
{% endhint %}

## FAQ <a href="#faq" id="faq"></a>

**Are alerts automatically resolved in ilert?**

Yes, as soon as the status of an alert is OK in Zabbix, the associated alert will be resolved in ilert.

**Can I link Zabbix to multiple alert sources in ilert?**

Yes, create several **ilert users** in Zabbix and store the corresponding **API key** in the user **Send To** field.

**What if my internet connection is lost? Are the events generated in Zabbix lost?**

No events are lost. The zabbix server tries to send the events to ilert every 30 seconds with 10 attempts (can be configured in media type settings). As soon as your connection is available again, all events are sent to ilert. We also recommend that you monitor your Internet connection with an external monitoring service. You can then send these alerts to ilert too.

**The plugin does not work. How do I find the issue?**

Please look at the **Problems View** in Zabbix under the actions column first. If you can not find the error, please contact our support at [support@ilert.com](mailto:support@ilert.com).

**Will problems in Zabbix be acknowledged if I accept the alert in ilert?**

If you have enabled the bidirectional setup during your alet source creation in ilert, yes. See [Bidectional sync](native.md#faq-1).

**Zabbix links in ilert alerts are invalid, what's wrong?**

This is probably because the URL of your Zabbix interface is not configured in the media type settings. Go **Administration** --> **Media types** and open ilert. In the Parameters sections, make sure that the value for `ZABBIX.URL` is correct. Example:

<figure><img src="../../.gitbook/assets/Screenshot 2022-11-23 at 11.03.28.png" alt=""><figcaption></figcaption></figure>

## Further References <a href="#faq" id="faq"></a>

This blog post in the Zabbix blog outlines how to use Zabbix and ilert with multiple on-call teams, where each team is responsible for a set of host groups in Zabbix, and therefore, will only receive alerts for the services it is responsible for:

[Working with multiple on-call teams using Zabbix and ilert](https://blog.zabbix.com/working-with-multiple-on-call-teams-using-zabbix-and-ilert/11847/)
