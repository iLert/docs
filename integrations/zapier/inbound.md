---
description: >-
  User iLert as a Zapier Action and create / acknowledge / resolve an alert for
  any trigger from Zapier.
---

# Zapier Inbound Integration

## In iLert <a id="in-ilert"></a>

### Create a Zapier alert source \(optional\) <a id="create-alert-source"></a>

{% hint style="info" %}
You can connect Zapier with an existing alert source of any integration type. Skip this step, if you'd like to connect Zapier with an existing alert source.
{% endhint %}

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "Zapier" as the **Integration Type** and click on **Save**.

![](../../.gitbook/assets/screenshot_29_10_20__16_20.png)

## In Zapier <a id="in-topdesk"></a>

### Create a Zap <a id="create-action-sequences"></a>

1. Go to Zapier and click on **Make a Zap**

![](../../.gitbook/assets/screenshot_29_10_20__16_22.png)

1. On the next page, search for a trigger source, e.g. Jira

![](../../.gitbook/assets/screenshot_29_10_20__16_35.png)

1. Choose your account and customize the settings of you trigger source, then click on the **Done Editing** button
2. Click on the **Choose an Action** button to add iLert action

![](../../.gitbook/assets/screenshot_29_10_20__16_39.png)

1. Enter **iLert** into the search field and click on the **iLert app**

![](../../.gitbook/assets/screenshot_29_10_20__16_40%20%281%29.png)

1. In the **Action Event** section choose the **Create Alert** action **\*\*to create an alert when a Jira issue is created. Then click on the** Continue\*\* button.

![](../../.gitbook/assets/screenshot_29_10_20__16_45.png)

1. On the next slide, choose your iLert account. Then click on the **Continue** button.

![](../../.gitbook/assets/screenshot_29_10_20__16_47.png)

1. On the next slide, in the **Integration Key** section, choose the Alert Source that you created before. In the **Alert key** section, we recommend to enter an alert key, so you can accept or resolve an alert in other Zaps. In the **Summary** section, enter or insert an alert summary. You can optionally enter or insert **Details**, **Priority** and **URL**. Then click on the **Continue** button.

![](../../.gitbook/assets/screenshot_29_10_20__23_15.png)

1. On the next slide, click on **Test & Continue** to test alert creation.

![](../../.gitbook/assets/screenshot_29_10_20__23_22.png)

1. On the next slide, click on **Turn On Zap** to activate your confugation.

![](../../.gitbook/assets/screenshot_29_10_20__23_25.png)

## FAQ <a id="faq"></a>

**Will alerts in iLert be resolved automatically?**

Yes, you need to configure an **Accept Alert** action with **Alert Key** for this in your Zap

**Will alerts in iLert be accepted automatically?**

Yes, you need to configure an **Resolve Alert** action with **Alert Key** for this in your Zap

**Can I connect Zapier with multiple alert sources from iLert?**

Yes, simply create more Zaps in Zapier.

