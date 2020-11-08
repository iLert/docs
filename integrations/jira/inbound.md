---
description: >-
  The iLert Jira Inbound Integration helps you to easily connect iLert with
  Jira.
---

# Jira Inbound Integration

With the iLert Jira integration you can create incidents in iLert based on Jira events.

## In iLert <a id="in-ilert"></a>

### Create a Jira alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**

2. Enter a name and select your desired escalation policy. Select "Jira" as the **Integration Type** and click on **Save**.

![](../../.gitbook/assets/ilert%20%2812%29.png)

3. On the next page, a Webhook URL is generated. You will need this URL below when setting up the Webhook in Jira.

![](../../.gitbook/assets/ilert%20%2813%29.png)

## In Jira <a id="in-topdesk"></a>

### Create webhook <a id="create-action-sequences"></a>

> NOTE: You need admin permissions to manage Jira webhooks.

1. Go to Jira and then to **System** **Settings:**

![](../../.gitbook/assets/projects_-_jira.png)

2. Click on the **WebHooks** and then on the **Create a WebHook** button to add a new webhook for iLert

![](../../.gitbook/assets/webhooks_-_jira.png)

3. On the next page,  in the section **Name** field, enter a name \(e.g. iLert\). In the section **URL** field, paste the **Webhook URL** that you generated in iLert. In the section **Issue** choose **created**, **updated** and **deleted** events.

![](../../.gitbook/assets/webhooks_-_jira%20%281%29.png)

4. Scroll to bottom and click on the **Create** button

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

Yes

**Will incidents in iLert be accepted automatically?**

No, unfortunately Jira events is not compatible with iLert accepted event.

**Can I connect Jira with multiple alert sources from iLert?**

Yes, simply create more webhooks in Jira.

