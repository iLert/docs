---
description: >-
  GitLab is a web-based Git repository that provides free open and private
  repositories, issue-following capabilities, and wikis. It is a complete DevOps
  platform that includes CI/CD.
---

# GitLab Integration

In ilert

1. Go to the "**Alert sources**" tab and click on "**Create new alert source**"
2. Enter a name and select your desired escalation policy.
3. Select "**GitLab**" as the **Integration Type** and click **Save**.
4.

    <figure><img src="../.gitbook/assets/Screenshot 2023-04-23 at 17.15.14.png" alt=""><figcaption></figcaption></figure>
5. Now click on **GitLab Settings** to show the advanced settings
6.

    <figure><img src="../.gitbook/assets/Screenshot 2023-04-23 at 18.19.15.png" alt=""><figcaption></figcaption></figure>
7. You may now choose one of the given **Hook types** which this alert source should process. (Leaving the selection on 'Select' will result the alert source to process all incoming **Hook types**)
8.

    <figure><img src="../.gitbook/assets/Screenshot 2023-04-23 at 14.57.15.png" alt=""><figcaption></figcaption></figure>
9. Some **Hook types** do additionally have a selection for an **Event type**.
10. Click on **Save** to proceed to the next step.
11.

    <figure><img src="../.gitbook/assets/Screenshot 2023-04-23 at 14.57.56.png" alt=""><figcaption></figcaption></figure>
12. On the next page a **GitLab Integration URL** is generated. You will need the URL for the webhook configuration
13.

    <figure><img src="../.gitbook/assets/Screenshot 2023-04-23 at 18.13.43.png" alt=""><figcaption></figcaption></figure>

## In GitLab

1. From your Project Page, navigate to **"Settings"** -> **"Webhooks"**

![](../.gitbook/assets/gitlab\_settingswebhook.png)

2. Select the events that should be send to ilert, in this case any **Issues events** or **Confidential issues events** activity will be send to ilert.

![](../.gitbook/assets/gitlab\_webhookselections.png)

3. Select "**Add Webhooks**"
4. and if it is added successfully it will be shown at the bottom of the page.

![](../.gitbook/assets/gitlab\_savewebhook.png)

5. Your GitLab integration is set up.
