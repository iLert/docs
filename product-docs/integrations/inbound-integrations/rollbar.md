---
description: Resolve application errors quicker—with ilert and Rollbar
---

# Rollbar Integration

[Rollbar](https://rollbar.com/) is a tool for debugging errors, enabling developers to quickly identify, understand, and resolve application issues. When integrated with ilert, Rollbar can automatically trigger alerts in ilert whenever it detects new errors or critical events.

## In ilert: Create a Rollbar alert source&#x20;

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Rollbar** in the search field, click the Rollbar tile, and then **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7. On the final page, an API key and/or webhook URL will be generated. You will need it later.

<figure><img src="../../.gitbook/assets/il-1 (6).png" alt=""><figcaption></figcaption></figure>

## In Rollbar: Create a Webhook

1. On the sidebar, navigate to **Projects**.

<figure><img src="../../.gitbook/assets/1 (21).png" alt=""><figcaption></figcaption></figure>

2. Select a desired project you want to receive notifications from.

<figure><img src="../../.gitbook/assets/2 (19).png" alt=""><figcaption></figcaption></figure>

3. Now navigate to **Notifications** and select **Webhook** from the available channels.

<figure><img src="../../.gitbook/assets/3 (16).png" alt=""><figcaption></figcaption></figure>

4. Enter the previously in ilert created integration url into the **URL** field.
5. Click on **Enable Webhook Integration** to finish the setup.

<figure><img src="../../.gitbook/assets/4 (14).png" alt=""><figcaption></figcaption></figure>

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as Rollbar is sending a notification with the `event_name` field set to `resolved_item`, corresponding alert in ilert will be resolved.
