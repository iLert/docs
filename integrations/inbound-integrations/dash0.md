# Dash0 Integration

## In ilert: Create a Dash0 alert source&#x20;

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Dash0** in the search field, click the Dash0 tile, and then **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7. On the final page, an API key and/or webhook URL will be generated. You will need it later.

<figure><img src="../../.gitbook/assets/il-1 (5).png" alt="" width="563"><figcaption></figcaption></figure>

## In Dash0: Create a  Notification channel

1. In the sidebar navigate to the company Settings.

<figure><img src="../../.gitbook/assets/1-2 (3).png" alt=""><figcaption></figcaption></figure>

2. Navigate to **Notification Channels** -**>** **New notification channel**.

<figure><img src="../../.gitbook/assets/2-2 (2).png" alt=""><figcaption></figcaption></figure>

3. Now select **Webhook**.

<figure><img src="../../.gitbook/assets/3-2 (3).png" alt=""><figcaption></figcaption></figure>

4. Now enter a **Name** and the previously in ilert created alert source url into the **URL** field.
5. Optional: click on **Send test notification**, to test.
6. Save the notification channel.

<figure><img src="../../.gitbook/assets/4-2 (2).png" alt=""><figcaption></figcaption></figure>

7. Navigate to **Alerting** -> **Notifications**.
8. Create a **new notification rule** or **Edit** an existing one.

<figure><img src="../../.gitbook/assets/5 (13).png" alt=""><figcaption></figcaption></figure>

9. In the **Notification channels** tab, click on **Add notification channel** and select the previously created notification channel.
10. Click on **Save**.

<figure><img src="../../.gitbook/assets/6 (14).png" alt=""><figcaption></figcaption></figure>

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as Dash0 sends a notification with type "alert.resolved", corresponding alerts in ilert will be resolved automatically.
