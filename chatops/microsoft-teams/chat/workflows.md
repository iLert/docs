---
description: >-
  The ilert Microsoft Teams Integration helps you to bring alerts into your
  channels without installing the app.
---

# Microsoft Teams Integration via Workflows

{% hint style="warning" %}
If possible we suggest to use [iLert's Microsoft Teams Bot](./) for the setup, this guide and integration is only suggested in case you do not want to grant any permissions to ilert
{% endhint %}

## In Microsoft Teams: Add a workflow to a channel <a href="#add-to-channel" id="add-to-channel"></a>

{% hint style="info" %}
**Admin permission required**

To set up the integration, you must have admin rights in ilert.
{% endhint %}

1. Select the channel in which you want to publish ilert Alerts and click **...** -> **Connectors**

<figure><img src="../../../.gitbook/assets/Screenshot 2024-07-19 at 14.06.56.png" alt=""><figcaption></figcaption></figure>

2. Type webhook in the search field and click on the **Webhook Template**

<figure><img src="../../../.gitbook/assets/Screenshot 2024-07-19 at 14.08.10.png" alt=""><figcaption></figcaption></figure>

3. Name your workflow and click on **Next**

<figure><img src="../../../.gitbook/assets/Screenshot 2024-07-19 at 14.08.26.png" alt=""><figcaption></figcaption></figure>

4. Review details and click on **Add workflow**.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-07-19 at 14.08.39.png" alt=""><figcaption></figcaption></figure>

5. On the next page copy the **workflow URL** and click **Done**.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-07-19 at 14.08.46.png" alt=""><figcaption></figcaption></figure>

7. Your connector has now been set up. You will need the URL from step 4 in ilert.

## In ilert: Create the Microsoft Teams Alert Action and link it to the alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1. Go to the **Alert Sources → Alert Actions** page and click on the **Create new alert action** button

<div data-full-width="false">

<figure><img src="../../../.gitbook/assets/Screenshot 2024-07-19 at 14.38.07.png" alt=""><figcaption></figcaption></figure>

</div>

2. Select **Microsoft Teams** as **Type** and choose **Use webhook** option. Then click on the **Next** button.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-07-19 at 14.38.29.png" alt=""><figcaption></figcaption></figure>

4. On the next page choose the alert source whose alerts you want to publish to Microsoft Teams, choose Trigger Events and click on the **Next** button

<figure><img src="../../../.gitbook/assets/Screenshot 2024-07-19 at 14.39.06.png" alt=""><figcaption></figcaption></figure>

5. On the next page name the alert action, enter the **URL** from [above](workflows.md#add-to-channel) and click on the **Save** button.

<figure><img src="../../../.gitbook/assets/Screenshot 2024-07-19 at 14.40.16.png" alt=""><figcaption></figcaption></figure>

7. Finished! Your Microsoft Teams via Workflows integration is set up.

## FAQ <a href="#faq" id="faq"></a>

**Can I link multiple Microsoft Teams Spaces to an ilert account?**

Yes.

**Are updates to an alert published on the Microsoft Teams channel?**

Yes, the following updates to an alert are currently being released:

* **Escalations** : An alert is assigned to another user through an automatic escalation.
* **Manual Assignments** : An alert is manually assigned to someone.
* **Actions** : An alert is accepted or resolved.
