# Apica Integration

## In ilert: Create a Apica alert source&#x20;

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Apica** in the search field, click the Apica tile, and then **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7. On the final page, an API key and/or webhook URL will be generated. You will need it later.

<figure><img src="../../.gitbook/assets/il-1 (4).png" alt="" width="563"><figcaption></figcaption></figure>

## In Apica: Create an Alert Destination

1. On the top menu bar, navigate to **Integrations -> Alert Destinations -> New Alert Destination**.

<figure><img src="../../.gitbook/assets/1 (20).png" alt=""><figcaption></figcaption></figure>

2. Now type "webhook" into the search field and select **Webhook**.

<figure><img src="../../.gitbook/assets/2 (18).png" alt=""><figcaption></figcaption></figure>

3. Enter a **Name** and the in ilert previously created alert source url into the **Url** field.

<figure><img src="../../.gitbook/assets/3 (15).png" alt=""><figcaption></figcaption></figure>

4. Now on the top menu bar, click on **Alerts**.

<figure><img src="../../.gitbook/assets/4 (13).png" alt=""><figcaption></figcaption></figure>

5. Select any Alert for which you want to receive a notification.
6. Click on the **'+'** in the Destinations tab.

<figure><img src="../../.gitbook/assets/5 (12).png" alt=""><figcaption></figcaption></figure>

7. Now select the previously created **Alert Destination** and click on **Save**.

<figure><img src="../../.gitbook/assets/6 (13).png" alt=""><figcaption></figcaption></figure>

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as the Alert transitions to the status "OK" , corresponding alerts in ilert will be resolved automatically.
