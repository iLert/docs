---
description: Send ClusterControl Alarms to ilert
---

# ClusterControl Integration

[**ClusterControl**](https://docs.severalnines.com/docs/clustercontrol/) by [**Severalnines**](https://severalnines.com/) is a comprehensive database operations orchestration platform designed to manage the entire lifecycle of open-source and proprietary databases in various environments, including on-premises, cloud, and hybrid setups. With this integration, you can send alerts from ClusterControl to ilert and notify engineers about critical issues via phone calls, SMS, push, and other types of notifications.&#x20;

## In ilert: Create a ClusterControl alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **ClusterControl** in the search field, click the ClusterControl tile, and then **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click **Finish setup** for now.
7. On the final page, an API key and/or webhook URL will be generated. You will need it later.

<figure><img src="../.gitbook/assets/il-1 (1).png" alt=""><figcaption></figcaption></figure>

## In ClusterControl: Create a Webhook

1. On the sidebar, click on **Integrations**.

<figure><img src="../.gitbook/assets/1 (11).png" alt="" width="563"><figcaption></figcaption></figure>

2. Now click **Add your first service**.

<figure><img src="../.gitbook/assets/2 (10).png" alt="" width="563"><figcaption></figcaption></figure>

3. Enter an **Integration Name** and the ilert alert source URL into the **Url** field.

<figure><img src="../.gitbook/assets/3 (9).png" alt="" width="375"><figcaption></figcaption></figure>

4. Optionally: Click on **Test** to test the webhook.

<figure><img src="../.gitbook/assets/4 (9).png" alt="" width="563"><figcaption></figcaption></figure>

5. In the last step, choose the desired **Clusters** and **Event Triggers** from which you want to receive a notification.

<figure><img src="../.gitbook/assets/5 (8).png" alt="" width="563"><figcaption></figcaption></figure>

## FAQ <a href="#faq" id="faq"></a>

**Are alerts in ilert automatically resolved?**

Yes, as soon as an event's status is set to ENDED in ClusterControl, the corresponding alert in ilert will be resolved.
