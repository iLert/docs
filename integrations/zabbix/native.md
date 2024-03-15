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

## In ilert: Create a Zabbix alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Zabbix** in the search field, click on the Zabbix tile and click on **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Zabbix <a href="#zabbix" id="zabbix"></a>

<details>

<summary>Import ilert media type (optional as of Zabbix 5.0.4)</summary>

<mark style="background-color:yellow;">**Are you using Zabbix 5.0.4 or higher?**</mark> <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">You can skip this section, if you're using Zabbix 5.0.4+, because as of Zabbix 5.0.4, the ilert media type is included in the distribution Zabbix.</mark>

1\. Download the ilert Zabbix Media Type file from the Zabbix repository

```
curl -o media_ilert.xml \
   https://raw.githubusercontent.com/iLert/ilert-zabbix/master/media_ilert.xml
```

2\. Go to the **Administration → Media types** tab and click the **Import** button.

<img src="../../.gitbook/assets/zbn4.png" alt="" data-size="original">

3\. Select import file `media_ilert.xml` and click the **Import** button at the bottom to import the ilert media type.

<img src="../../.gitbook/assets/zbn5.png" alt="" data-size="original">

4\. **Optional**: Go to **Media types** and open the imported **iLert** media type. You can overwrite the default alert summary with a custom template using the `.ILERT.INCIDENT.SUMMARY` variable e.g. `{TRIGGER.NAME}: {TRIGGER.STATUS} for {HOST.HOST}`

<img src="../../.gitbook/assets/6 (2).png" alt="" data-size="original">

5\. Click on the **Update** button to save the media type.

</details>

### Create ilert user and group

1\. Go to the **Administration → User groups** tab and click on the **Create user group** button.

![](../../.gitbook/assets/zbn7.png)

2\. Set the name for the ilert group (eg. "ilert group").

![](../../.gitbook/assets/zbn8.png)

3\. Switch to the **Permissions** tab and select the **host groups** that the ilert group should have read access to, for sending notifications. Without read access, ilert cannot receive notifications for the hosts in the group (see also [here](https://www.zabbix.com/documentation/4.4/manual/quickstart/notification)).

4\. Click the **Add** button to save the group.

![](../../.gitbook/assets/zbn9.png)

5\. Switch to the Users tab and click on the **Create user** button.

![](../../.gitbook/assets/zbn10.png)

6\. Assign an **alias** and **name** and add the user to the ilert group. No further details such as a password are required as this user will not log in to Zabbix.

![](../../.gitbook/assets/zbn11.png)

7\. Switch to the **Media** tab and click on the **Add** link

8\. In the **media** window, select ilert as **Type**

9\. In the **Send to** field enter the alert source api key that you generated in ilert

10\. Click the **Add** button

![](<../../.gitbook/assets/9 (1) (1).png>)

11\. Click the **Add** button in the **Users** tab to save the user.

![](../../.gitbook/assets/zbn13.png)

### Create an alert action

1\. Switch to the **Configuration → Actions** tab and click the **Create action** button

![](../../.gitbook/assets/zbn14.png)

2\. Give the action a name, eg "ilert notifications".

![](../../.gitbook/assets/zbn15.png)

3\. Perform the following actions on the **Operations**, **Recovery operations** and **Acknowledgment operations** tabs

![](../../.gitbook/assets/zbn16.png)

4\. Change the default subject and default message if you want.

5\. Click on the **New** link under **Operations** and select the **iLert** group created above under Send to User groups.

![](../../.gitbook/assets/zbn17.png)

6\. Click the **Add** button to save the action

## Optional: Mapping Zabbix problem severity to alert priority <a href="#faq" id="faq"></a>

ilert supports a mapping configuration for your Zabbix alert source that allows you to map the standard Zabbix severities to ilert priorities. Just enable the checkbox for **Priority mapping** under Zabbix settings.

![](<../../.gitbook/assets/image (55) (2).png>)

## Optional: Bidirectional sync (acknowledges alerts in Zabbix) <a href="#faq" id="faq"></a>

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
