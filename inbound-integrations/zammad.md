---
description: >-
  With ilert's integration you can easily connect Zammad with ilert, create
  alerts from tickets and vice versa.
---

# Zammad Integration

[Zammad](https://zammad.com/en) is an open-source helpdesk and customer support platform designed to help businesses manage communications and interactions with their customers.

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Zammad Outbound Integration</strong></td><td>Create tickets in Zammad from ilert alerts</td><td><a href="../outbound-integrations/zammad.md">zammad.md</a></td></tr></tbody></table>

## In ilert: Create a Zammad alert source <a href="#in-ilert" id="in-ilert"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Zammad** in the search field, click on the Zammad tile and click on **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Zammad: Create ticket triggers <a href="#in-topdesk" id="in-topdesk"></a>

1. Go to Zammad and then to **Trigger**

![](../.gitbook/assets/Screenshot\_07\_02\_21\_\_13\_13.png)

2. Click on **New Trigger.** On the modal window, in the **Conditions for effected objects** section choose the condition **State is new,** name the trigger e.g. **ilert Trigger - New Ticket** , in the **Execute changes on object** section choose **Webhook** and paste the **Webhook URL** that you generated in ilert then click on **Submit**

![](../.gitbook/assets/Screenshot\_07\_02\_21\_\_13\_18.png)

3. Click on **New Trigger.** On the modal window, in the **Conditions for effected objects** section choose the condition **State is open,** name the trigger e.g. **ilert Trigger - Open Ticket** , in the **Execute changes on object** section choose **Webhook** and paste the **Webhook URL** that you have generated in ilert and then click on **Submit**

![](../.gitbook/assets/Screenshot\_07\_02\_21\_\_13\_24.png)

4. Click on **New Trigger.** On the modal window, in the **Conditions for effected objects** section choose the condition **Owner has changed,** name the trigger e.g. **ilert Trigger - Owner changed** , in the **Execute changes on object** section choose **Webhook** and paste the **Webhook URL** that you have generated in ilert and then click on **Submit**

![](../.gitbook/assets/Screenshot\_07\_02\_21\_\_13\_26.png)

5. Click on **New Trigger.** On the modal window, in the **Conditions for effected objects** section choose the condition **State has changed,** name the trigger e.g. **ilert Trigger - Ticket changed** , in the **Execute changes on object** section choose **Webhook** and paste the **Webhook URL** that you have generated in ilert and then click on **Submit**

![](../.gitbook/assets/Screenshot\_07\_02\_21\_\_13\_27.png)

Your Zammad triggers are now in place and will trigger appropriate ilert alert actions of your created alert source.

## Mapping of Zammand Ticket Priority to Alert Priority

The Zammad ticket priority is mapped to the ilert alert priority according to the following table:

| Zammand ticket priority | ilert alert priority |
| ----------------------- | -------------------- |
| **High (id: 3)**        | High                 |
| Any other               | Low                  |

## FAQ <a href="#faq" id="faq"></a>

### **Will alerts in ilert be resolved automatically?**

Yes

### **Can I connect Zammad with multiple alert sources from ilert?**

Yes, simply create more action sequences in Zammad.

### Will Zammad comments be synced to ilert?

Yes, Zammad comments will automatically be attached to ilert alerts.
