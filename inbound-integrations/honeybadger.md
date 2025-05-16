# Honeybadger Integration

[Honeybadger](https://www.honeybadger.io/) is an application monitoring solution designed for developers to identify and resolve issues in real-time. It tracks errors, uptime, and performance, giving teams insight into problems before users report them. By connecting Honeybadger to ilert, users can streamline their incident management process, receiving alerts on critical errors via ilert’s flexible notification channels and escalation policies.

## In ilert: Create a Honeybadger alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Honeybadger** in the search field, click the Honeybadger tile, and then **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7. On the final page, an API key and/or webhook URL will be generated. You will need it later.

<figure><img src="../.gitbook/assets/il-1-2 (1).png" alt="" width="563"><figcaption></figcaption></figure>

## In Honeybadger: Create a Webhook

1. On the dashboard, click on **Settings**.

<figure><img src="../.gitbook/assets/1 (1) (1) (1) (1) (1) (1) (2).png" alt=""><figcaption></figcaption></figure>

2. Now click on **Alerts & integrations**.

<figure><img src="../.gitbook/assets/2 (1) (1) (1) (1) (1) (2) (1).png" alt=""><figcaption></figcaption></figure>

3. Scroll down and choose **ilert**.

<figure><img src="../.gitbook/assets/5 (11).png" alt=""><figcaption></figcaption></figure>

4. Enter the in ilert previous generated alert source url into the URL field.
5. Select the error-related events for which you want to receive notifications.
6. Click on Save to finish the setup.

<figure><img src="../.gitbook/assets/6 (12).png" alt=""><figcaption></figcaption></figure>

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as the state of a Monitor, Error or Heartbeat in Honeybadger is 'up', 'resolved' or 'check\_in\_reporting', corresponding  alert in ilert will be resolved.
