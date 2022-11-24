---
description: >-
  User ilert as a Zapier Action and create / acknowledge / resolve an alert for
  any trigger from Zapier.
---

# Zapier Inbound Integration

## In ilert <a href="#in-ilert" id="in-ilert"></a>

### Create a Zapier alert source (optional) <a href="#create-alert-source" id="create-alert-source"></a>

{% hint style="info" %}
You can connect Zapier with an existing alert source of any integration type. Skip this step, if you'd like to connect Zapier with an existing alert source.
{% endhint %}

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "Zapier" as the **Integration Type** and click on **Save**.

![](../../.gitbook/assets/Screenshot\_29\_10\_20\_\_16\_20.png)

## In Zapier <a href="#in-topdesk" id="in-topdesk"></a>

### Create a Zap <a href="#create-action-sequences" id="create-action-sequences"></a>

1. Go to Zapier and click on **Make a Zap**

![](../../.gitbook/assets/Screenshot\_29\_10\_20\_\_16\_22.png)

1. On the next page, search for a trigger source, e.g. Jira

![](../../.gitbook/assets/Screenshot\_29\_10\_20\_\_16\_35.png)

1. Choose your account and customize the settings of you trigger source, then click on the **Done Editing** button
2. Click on the **Choose an Action** button to add ilert action

![](../../.gitbook/assets/Screenshot\_29\_10\_20\_\_16\_39.png)

1. Enter **iLert** into the search field and click on the **ilert app**

![](<../../.gitbook/assets/Screenshot\_29\_10\_20\_\_16\_40 (1).png>)

1. In the **Action Event** section choose the **Create Alert** action **\*\*to create an alert when a Jira issue is created. Then click on the** Continue\*\* button.

![](../../.gitbook/assets/Screenshot\_29\_10\_20\_\_16\_45.png)

1. On the next slide, choose your ilert account. Then click on the **Continue** button.

![](../../.gitbook/assets/Screenshot\_29\_10\_20\_\_16\_47.png)

1. On the next slide, in the **Integration Key** section, choose the Alert Source that you created before. In the **Alert key** section, we recommend to enter an alert key, so you can accept or resolve an alert in other Zaps. In the **Summary** section, enter or insert an alert summary. You can optionally enter or insert **Details**, **Priority** and **URL**. Then click on the **Continue** button.

![](../../.gitbook/assets/Screenshot\_29\_10\_20\_\_23\_15.png)

1. On the next slide, click on **Test & Continue** to test alert creation.

![](../../.gitbook/assets/Screenshot\_29\_10\_20\_\_23\_22.png)

1. On the next slide, click on **Turn On Zap** to activate your confugation.

![](../../.gitbook/assets/Screenshot\_29\_10\_20\_\_23\_25.png)

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, you need to configure an **Accept Alert** action with **Alert Key** for this in your Zap

**Will alerts in ilert be accepted automatically?**

Yes, you need to configure an **Resolve Alert** action with **Alert Key** for this in your Zap

**Can I connect Zapier with multiple alert sources from ilert?**

Yes, simply create more Zaps in Zapier.
