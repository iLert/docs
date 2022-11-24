---
description: >-
  With the ilert Zammad integration, you can create alerts in ilert based on
  Zammad tickets.
---

# Zammad Inbound Integration

## In ilert <a href="#in-ilert" id="in-ilert"></a>

### Create a Zammad alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "Zammad" as the **Integration Type** and click on **Save**.

![](../../.gitbook/assets/Screenshot\_07\_02\_21\_\_13\_11.png)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the hook in Zammad.

![](<../../.gitbook/assets/Screenshot\_07\_02\_21\_\_13\_11 (1).png>)

## In Zammad <a href="#in-topdesk" id="in-topdesk"></a>

### Create ticket triggers <a href="#create-action-sequences" id="create-action-sequences"></a>

1. Go to Zammad and then to **Trigger**

![](../../.gitbook/assets/Screenshot\_07\_02\_21\_\_13\_13.png)

1. Click on **New Trigger.** On the modal window, in the **Conditions for effected objects** section choose the condition **State is new,** name the trigger e.g. **ilert Trigger - New Ticket** , in the **Execute changes on object** section choose **Webhook** and paste the **Webhook URL** that you generated in ilert then click on **Submit**

![](../../.gitbook/assets/Screenshot\_07\_02\_21\_\_13\_18.png)

1. Click on **New Trigger.** On the modal window, in the **Conditions for effected objects** section choose the condition **State is open,** name the trigger e.g. **ilert Trigger - Open Ticket** , in the **Execute changes on object** section choose **Webhook** and paste the **Webhook URL** that you have generated in ilert and then click on **Submit**

![](../../.gitbook/assets/Screenshot\_07\_02\_21\_\_13\_24.png)

1. Click on **New Trigger.** On the modal window, in the **Conditions for effected objects** section choose the condition **Owner has changed,** name the trigger e.g. **ilert Trigger - Owner changed** , in the **Execute changes on object** section choose **Webhook** and paste the **Webhook URL** that you have generated in ilert and then click on **Submit**

![](../../.gitbook/assets/Screenshot\_07\_02\_21\_\_13\_26.png)

1. Click on **New Trigger.** On the modal window, in the **Conditions for effected objects** section choose the condition **State has changed,** name the trigger e.g. **ilert Trigger - Ticket changed** , in the **Execute changes on object** section choose **Webhook** and paste the **Webhook URL** that you have generated in ilert and then click on **Submit**

![](../../.gitbook/assets/Screenshot\_07\_02\_21\_\_13\_27.png)

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
