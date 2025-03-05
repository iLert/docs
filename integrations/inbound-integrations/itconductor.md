# IT-Conductor Integration

## In ilert: Create an IT-Conductor alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **IT-Conductor** in the search field, click the IT-Conductor tile, and then **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7. On the final page, an API key and/or webhook URL will be generated. You will need it later.

<figure><img src="../../.gitbook/assets/il (1).png" alt="" width="563"><figcaption></figcaption></figure>

## In IT-Conductor: Create an Integration Provider

1. On the top bar, navigate to **Management** -> **Notification** -> **Integration Providers**.

<figure><img src="../../.gitbook/assets/1 (18).png" alt="" width="563"><figcaption></figcaption></figure>

2. Click on the ilert symbole.

<figure><img src="../../.gitbook/assets/2-2 (1).png" alt="" width="563"><figcaption></figcaption></figure>

3. Select the desired **Role** and **Gateway**.
4. Add the Integration key of the ilert alert source into the Integration Key field.

<figure><img src="../../.gitbook/assets/2 (16).png" alt="" width="563"><figcaption></figcaption></figure>
