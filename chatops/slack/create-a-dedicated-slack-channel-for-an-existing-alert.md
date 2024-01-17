# Create a dedicated Slack channel for an existing alert

{% hint style="info" %}
**Connect your Slack workspace with ilert first**

Before you proceed, please make sure that a global admin has connected your Slack workspace with your ilert account (as described in our [integration for Slack guide](./))
{% endhint %}

Our Slack connector allows you to create a dedicated Slack channel for an existing alert to allow real-time collaboration. Gather your team members in a shared chat room to discuss the issue, share findings and coordinate the response.

### Creating a dedicated Slack channel

1. On the alert list, navigate to the desired alert for which you want to create a channel.
2.  In the **Links** section of the alert, click on the **Create Slack channel** link, set the channel name and save. If you'd like to create a private channel, tick the **Make the channel private checkbox**.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-10-05 at 16.28.46.png" alt=""><figcaption></figcaption></figure>
3. Once created, the channel will be linked in the alert. You can now open the created channel by clicking on **View Slack channel** link. All current and future responders will be automatically invited to the channel.&#x20;

### Detaching a Slack channel from an alert

1. On the alert list, navigate to the desired alert for which you want to detach a channel.
2. Hover over the **View Slack channel** area and click on the  "x" Button
3. Once detached, a message will be sent to the detached channel.

{% embed url="https://www.youtube.com/watch?v=EOpxqECNyEM" %}
Check out our step-by-step tutorial on Youtube
{% endembed %}

## FAQ

**Are the alerts in the created channel updated in real time?**

Yes, as long as the channel is not detached the alert will receives real time updates in the alert thread.

**The ilert bot has no permission to create a channel. What can I do?**

If your ilert bot for Microsoft Teams bot has no permission. Please reauthorize your bot. You need to have admin permissions both in ilert and Slack.
