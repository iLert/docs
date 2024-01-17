---
description: >-
  The ilert Microsoft Teams integration makes it easier to collaborate on
  incidents by creating a dedicated Microsoft Teams channel.
---

# Create a channel for an existing alert in Microsoft Teams

{% hint style="info" %}
**Connect your Microsoft Teams workspace with ilert first**

Before you proceed, please make sure that a global admin has connected your Microsoft Teams workspace with your ilert account (as described in our [integration for Microsoft Teams guide](chat/#install-the-ilert-bot-application))
{% endhint %}

Our Microsoft Teams connector allows you to create a channel to an existing alert in Microsoft Teams, making it even easier for your team to discuss incidents in an more isolated environment.

### Creating a Microsoft Teams channel

1. On the alert list, navigate to the desired alert for which you want to create a channel.

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-09 at 13.59.06.png" alt=""><figcaption></figcaption></figure>

2. Now select a desired **Channel group**(Team) and enter a channel name.

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-09 at 14.06.55.png" alt="" width="367"><figcaption></figcaption></figure>

{% hint style="info" %}
Channel names are generated in advance and consist of the name of the alert source and the alert ID. If you want to choose another name, please make sure that you use a channel name that does not exist.
{% endhint %}

3. Click on **Create MS-Teams** channel to execute the channel creation and alert posting.
4. You can now view the created channel by clicking on **View MS-Teams channel**.

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-09 at 14.15.45.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-09 at 14.21.03.png" alt=""><figcaption></figcaption></figure>

{% embed url="https://www.youtube.com/watch?v=xwY6jz8sV4M" %}
Check out our step-by-step tutorial on Youtube
{% endembed %}

### Detaching a Microsoft Teams channel from an alert

1. On the alert list, navigate to the desired alert for which you want to detach a channel.
2. Hover over the **View MS-Teams channel** area and click on the small "x"



<figure><img src="../../.gitbook/assets/Screenshot 2023-08-09 at 14.16.07.png" alt=""><figcaption></figcaption></figure>

3. After detaching an alert from a channel, a message will be send to the detached channel.

<figure><img src="../../.gitbook/assets/Screenshot 2023-08-09 at 14.21.22.png" alt=""><figcaption></figcaption></figure>

## FAQ

**Are the alerts in the created channel updated in real time?**

Yes, as long as the channel is not detached the alert will receives real time updates in threads.

**The ilert bot has no permission to create a channel.**

If your ilert bot for Microsoft Teams bot has no permission. Please reauthorize your bot.

