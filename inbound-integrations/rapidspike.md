---
description: >-
  Receive critical RapidSpike alerts via SMS, voice calls, messenger and push
  notifications
---

# RapidSpike Integration

[RapidSpike](https://www.rapidspike.com/) is a digital experience monitoring tool that tracks website performance. Integrating it with ilert allows users to receive instant alerts for issues, enabling quicker response times, minimized downtime, and a better user experience.

## In ilert: Create a RapidSpike alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **RapidSpike** in the search field, click the RapidSpike tile, and then **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7. On the final page, an API key and/or webhook URL will be generated. You will need it later.

<figure><img src="../.gitbook/assets/il-1 (1) (1) (1).png" alt="" width="563"><figcaption></figcaption></figure>

## In RapidSpike: Create a Webhook

1. On the sidebar, navigate to **Integrations**.

<figure><img src="../.gitbook/assets/1 (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

2. Scroll to the **Webhooks** section and click on **Add**.

<figure><img src="../.gitbook/assets/2 (1) (1) (1) (1) (1) (2).png" alt=""><figcaption></figcaption></figure>

3. Change the **Request Type** to 'POST'.
4. Enter a **Label** and the previously in ilert created alert source url into the **WebHook URL** field.
5. Click on **Add** to finish the setup.

<figure><img src="../.gitbook/assets/3 (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as the state of a Monitor in RapidSpike is on 'passing' again, corresponding alert in ilert will be resolved.
