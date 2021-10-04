---
description: >-
  With the iLert Zammad integration, you can create alerts in iLert based on
  Zammad tickets.
---

# Zammad Inbound Integration

## In iLert <a id="in-ilert"></a>

### Create a Zammad alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "Zammad" as the **Integration Type** and click on **Save**.

![](../../.gitbook/assets/screenshot_07_02_21__13_11.png)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the hook in Zammad.

![](../../.gitbook/assets/screenshot_07_02_21__13_11%20%281%29.png)

## In Zammad <a id="in-topdesk"></a>

### Create ticket triggers <a id="create-action-sequences"></a>

1. Go to Zammad and then to **Trigger**

![](../../.gitbook/assets/screenshot_07_02_21__13_13.png)

1. Click on **New Trigger.** On the modal window, in the **Conditions for effected objects** section choose the condition **State is new,** name the trigger e.g. **iLert Trigger - New Ticket** , in the **Execute changes on object** section choose **Webhook** and paste the **Webhook URL** that you generated in iLert then click on **Submit**

![](../../.gitbook/assets/screenshot_07_02_21__13_18.png)

1. Click on **New Trigger.** On the modal window, in the **Conditions for effected objects** section choose the condition **State is open,** name the trigger e.g. **iLert Trigger - Open Ticket** , in the **Execute changes on object** section choose **Webhook** and paste the **Webhook URL** that you have generated in iLert and then click on **Submit**

![](../../.gitbook/assets/screenshot_07_02_21__13_24.png)

1. Click on **New Trigger.** On the modal window, in the **Conditions for effected objects** section choose the condition **Owner has changed,** name the trigger e.g. **iLert Trigger - Owner changed** , in the **Execute changes on object** section choose **Webhook** and paste the **Webhook URL** that you have generated in iLert and then click on **Submit**

![](../../.gitbook/assets/screenshot_07_02_21__13_26.png)

1. Click on **New Trigger.** On the modal window, in the **Conditions for effected objects** section choose the condition **State has changed,** name the trigger e.g. **iLert Trigger - Ticket changed** , in the **Execute changes on object** section choose **Webhook** and paste the **Webhook URL** that you have generated in iLert and then click on **Submit**

![](../../.gitbook/assets/screenshot_07_02_21__13_27.png)

Your Zammad triggers are now in place and will trigger appropriate iLert alert actions of your created alert source.

## Mapping of Zammand Ticket Priority to Alert Priority

The Zammad ticket priority is mapped to the iLert alert priority according to the following table:

| Zammand ticket priority | iLert alert priority |
| :--- | :--- |
| **High \(id: 3\)** | High |
| Any other | Low |

## FAQ <a id="faq"></a>

### **Will alerts in iLert be resolved automatically?**

Yes

### **Can I connect Zammad with multiple alert sources from iLert?**

Yes, simply create more action sequences in Zammad.

### Will Zammad comments be synced to iLert?

Yes, Zammad comments will automatically be attached to iLert alerts.

