# Healthchecks.io Integration

[Healthchecks.io](https://healthchecks.io/) is an online service designed to monitor the execution of cron jobs and other scheduled tasks. By generating unique ping URLs for each task, users can configure their jobs to send HTTP requests upon completion. If a task fails to ping within the expected timeframe, Healthchecks.io sends alerts to ilert.&#x20;

## In ilert: Create a Healthchecks.io alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Healthchecks.io** in the search field, click the Healthchecks.io tile, and then **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7. On the final page, an API key and/or webhook URL will be generated. You will need it later.

<figure><img src="../../.gitbook/assets/il-1 (3).png" alt="" width="563"><figcaption></figcaption></figure>

## In Healthchecks.io: Create a Webhook

1. On the navigation bar, click on **INTEGRATIONS**.

<figure><img src="../../.gitbook/assets/1 (17).png" alt=""><figcaption></figcaption></figure>

2. Click on the **Add Integration** button next to **Webhook**.

<figure><img src="../../.gitbook/assets/2 (15).png" alt=""><figcaption></figcaption></figure>

3. Enter a Name.
4. Enter the previously in ilert generated alert source url into the **URL** fields.
5. Enter `$JSON` to both 'up' and 'down' **Request Body** fields.
6. Now enter following into both **Request Headers** fields:

```
Check-Status: $STATUS
Content-Type: application/json
```

7. Click on the **Save Integration** button to finish the setup.

<figure><img src="../../.gitbook/assets/3 (14).png" alt=""><figcaption></figcaption></figure>

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as the Check-Status of a check in Healthchecks.io is 'up' again, corresponding alert in ilert will be resolved.
