---
description: >-
  GitLab is a web-based Git repository that provides free open and private
  repositories, issue-following capabilities, and wikis. It is a complete DevOps
  platform that includes CI/CD.
---

# GitLab Integration

## In iLert

* Go to the "**Alert sources**" tab and click on "**Create new alert source**"
* Enter a name and select your desired escalation policy.  &#x20;
* Select "**GitLab**" as the **Integration Type** and click **Save**.
* On the next page a **GitLab Integration URL** is generated. You will need the URL for the webhook configuration

## In GitLab

* From your Project Page, navigate to **"Settings"** -> **"Webhooks"**

![](../.gitbook/assets/gitlab\_settingswebhook.png)

* Select the events that should be send to iLert, in this case any **Issues events** or **Confidential issues events** activity will be send to iLert.

![](../.gitbook/assets/gitlab\_webhookselections.png)

* Select "**Add Webhooks**"&#x20;
* and if it is added successfully it will be shown at the bottom of the page.

![](../.gitbook/assets/gitlab\_savewebhook.png)

Your GitLab integration is set up.
