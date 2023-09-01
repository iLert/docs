---
description: >-
  Create ilert alerts from JIRA issues and get alerted through ilert for high
  priority issues.
---

# Jira Inbound Integration

With the ilert Jira integration you can create alerts in ilert based on Jira issues.

## In ilert: Create a Jira alert source <a href="#in-ilert" id="in-ilert"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Jira** in the search field, click on the Jira tile and click on **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Jira <a href="#in-topdesk" id="in-topdesk"></a>

### Create webhook <a href="#create-action-sequences" id="create-action-sequences"></a>

{% hint style="info" %}
You need admin permissions to manage Jira webhooks.
{% endhint %}

1. Go to Jira and then to **System** **Settings:**

![](../../.gitbook/assets/Projects\_-\_Jira.png)

2. Click on the **WebHooks** and then on the **Create a WebHook** button to add a new webhook for ilert

![](../../.gitbook/assets/WebHooks\_-\_Jira.png)

3. On the next page, in the section **Name** field, enter a name (e.g. ilert). In the section **URL** field, paste the **Webhook URL** that you generated in ilert. In the section **Issue** choose **created**, **updated** and **deleted** events.

![](<../../.gitbook/assets/WebHooks\_-\_Jira (1).png>)

4. Scroll down and make sure that the request body is **not excluded**

![](../../.gitbook/assets/Screenshot\_23\_09\_21\_\_13\_18.png)

5. Scroll to bottom and click on the **Create** button

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes

**Will alerts in ilert be accepted automatically?**

No, unfortunately Jira events are not compatible with ilert accepted event.

**Can I connect Jira with multiple alert sources from ilert?**

Yes, simply create more webhooks in Jira.
