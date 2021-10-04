---
description: >-
  User iLert as the trigger in Zapier and perform any action in Zapier for new
  or updated alerts in iLert.
---

# Zapier Outbound Integration

## In Zapier <a id="in-ilert"></a>

### Create a Zap <a id="create-action-sequences"></a>

1. Go to Zapier and click on **Make a Zap**

![](../../.gitbook/assets/screenshot_29_10_20__16_22.png)

1. On the next page, search for **iLert** trigger source and choose it:

![](../../.gitbook/assets/edit_a_step___zapier.png)

1. In the section **Trigger Event** choose **New or Updated Alert** and click on the **Continue** button

![](../../.gitbook/assets/edit_a_step___zapier%20%282%29.png)

1. On the next slide, choose your iLert account. Then click on the **Continue** button.

![](../../.gitbook/assets/edit_a_step___zapier%20%284%29.png)

1. On the next slide, choose **an alert source** and **trigger types** e.g. Alert Created. Then click on the **Continue** button.

{% hint style="warning" %}
NOTE: you can't use an Zapier alert source here, as it will lead to an infinite loop
{% endhint %}

![](../../.gitbook/assets/edit_a_step___zapier%20%283%29.png)

1. On the next slide, click on the **Test Trigger** button to see example data. Then click on the **Continue** button.

![](../../.gitbook/assets/edit_a_step___zapier%20%281%29.png)

1. Now you can **add any action** available in Zapier, e.g. Jira to create a ticket on your Jira board

![](../../.gitbook/assets/edit_step___zapier.png)

## FAQ <a id="faq"></a>

**Why the Zapier connector is in my alert source?**

Every time you create a Zap with an iLert trigger, the Zapier connector in iLert is created automatically for the alert source you selected in the trigger.

