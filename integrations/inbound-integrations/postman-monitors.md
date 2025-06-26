---
description: >-
  Connect ilert and Postman's Monitor to receive alerts via SMS, push, and voice
  notifications
---

# Postman Monitors Integration

Postman is a platform for API development, allowing developers to design, test, document, and monitor APIs. It offers a user-friendly interface and a comprehensive suite of tools to simplify working with APIs, making creating, sharing, and troubleshooting API requests easier. Postman's monitor feature enables developers to schedule and automate API tests. By integrating ilert with Postman, users can automatically send alerts from Postman to their incident management platform, ensuring the prompt delivery of alerts. This guide will walk you through setting up a connection between ilert and Postman.

## In ilert: Create a Postman Monitors alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Postman Monitors** in the search field, click the Postman tile, and then **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7. On the final page, an API key and/or webhook URL will be generated. You will need it later.

<figure><img src="../../.gitbook/assets/il-1 (1) (1) (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

## In Postman: Create a Webhook

1. On the Home page, click **Integrations**.

<figure><img src="../../.gitbook/assets/1 (1) (1) (1) (1) (1) (1) (1) (1).png" alt="" width="375"><figcaption></figcaption></figure>

2. Now click on **Browse All Integrations**.

<figure><img src="../../.gitbook/assets/2 (1) (1) (1) (1) (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

3. In the search field, enter webhooks and click the **Webhooks** tile.

<figure><img src="../../.gitbook/assets/3 (1) (1) (1) (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

4. Now in the **Post monitoring results** section, click on **Add integration**.

<figure><img src="../../.gitbook/assets/4 (1) (1) (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

5. Enter a **Nickname**, choose a desired **workspace** and **Monitor**.
6. Now enter the alert source url created in ilert into the **Webhook URL** field and select **Notify for 3 failures and then first success**.
7. Click on **Add Integration** to finish the setup.

<figure><img src="../../.gitbook/assets/5-2.png" alt="" width="563"><figcaption></figcaption></figure>

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as the state of a Monitor in Postman is Healthy again, the alert in ilert will be fixed.
