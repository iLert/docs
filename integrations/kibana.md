---
description: The ilert Kibana Integration helps you to easily connect ilert with Kibana.
---

# Kibana

## In ilert: Create an Kibana alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Kibana** in the search field, click on the Kibana tile and click on **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>



## In Kibana: Create a connector

1. On the sidebar click on **Connectors** under the **Alerts and Insights** category.

<figure><img src="../.gitbook/assets/1 (3).png" alt="" width="136"><figcaption></figcaption></figure>

2. Now click on **Create connector**.

<figure><img src="../.gitbook/assets/2 (1).png" alt="" width="563"><figcaption></figcaption></figure>

3. Select **Webhook**.

<figure><img src="../.gitbook/assets/3.png" alt="" width="563"><figcaption></figcaption></figure>

4. Enter a **Connector name**.
5. Under **Connector settings** enter the previous generated ilert Elasticsearch Kibana alert source URL into the **URL** field and change the **Method** to POST.
6. Choose None under **Authentication** and enable **Add HTTP header**.
7. Enter following header -> `key: Content-Type value: application/json`
8. Save the connector.

<figure><img src="../.gitbook/assets/4.png" alt="" width="563"><figcaption></figcaption></figure>

9. Now navigate to **Rules** under the **Alerts and Insights** category.

<figure><img src="../.gitbook/assets/5 (1).png" alt="" width="137"><figcaption></figcaption></figure>

10. Click on **Create rule**.

<figure><img src="../.gitbook/assets/6.png" alt="" width="563"><figcaption></figcaption></figure>

10. Enter a **name** and select Webhook as **connector type**.

<figure><img src="../.gitbook/assets/7.png" alt="" width="375"><figcaption></figcaption></figure>

11. Choose the previous created ilert connector as **Webhook connector**.
12. Enter following payload into the **Body** field:

```mustache
{
  "alert" : {{{ alert }}},
  "context" : {{{ context }}},
  "rule" : {{{ rule }}}
}
```

<figure><img src="../.gitbook/assets/8.png" alt=""><figcaption></figcaption></figure>

13. Save the rule.

## FAQ

**Will alerts in ilert be resolved automatically?**

No, unfortunately Kibana is not compatible with ilert's resolve event.