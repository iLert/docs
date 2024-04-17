---
description: The ilert Datadog Integration helps you to easily connect ilert with Datadog.
---

# Datadog Integration

Datadog is a popular monitoring and analytics platform designed for cloud-scale applications and infrastructure. It allows organizations to collect, visualize, and analyze data from various sources to gain insights into their IT environments and improve performance, security, and availability.

ilert's Datadog integration empowers you to swiftly respond and resolve incidents. By introducing bi-directional alerting across various channels, such as voice calls, SMS, and push notifications, this integration ensures that the appropriate person is notified based on on-call schedules and escalation policies.

With the ilert Datadog integration, you can create alerts in ilert based on Datadog events.

## In ilert: Create a Datadog alert source <a href="#alert-source" id="alert-source"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Datadog** in the search field, click on the Datadog tile, and click **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click on **Finish setup** for now.
7.  On the final page, an API key and/or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Datadog: Add ilert Webhook as an alerting channel <a href="#add-webhook" id="add-webhook"></a>

1. Go to the Datadog integrations page and **install Webhooks integration**: [https://app.datadoghq.com/account/settings#integrations](https://app.datadoghq.com/account/settings#integrations)
2. Click a Webhooks integration, scroll to the bottom, and add a new webhook:

![](../.gitbook/assets/dd3.png)

3. Enter a name, the **Datadog webhook URL** from the ilert alert source, and **template payload**:

```
{
 "body": "$EVENT_MSG",
 "last_updated": "$LAST_UPDATED",
 "event_type": "$EVENT_TYPE",
 "alert_transition": "$ALERT_TRANSITION",
 "alert_id": "$ALERT_ID",
 "link": "$LINK",
 "title": "$EVENT_TITLE",
 "date": "$DATE",
 "org": {
     "id": "$ORG_ID",
     "name": "$ORG_NAME"
 },
 "id": "$ID"
}
```

![](../.gitbook/assets/dd4.png)

4. Click **save** button
5. The integration is now set up!

### Use webhooks in monitors/alerts

You can now trigger the webhook and send alerts to ilert. To do so, include the name of the webhook with an _@webhook-_ in the text of the monitor’s alert. For example, if we use the example above, use _@webhook-main\_stream_.



### Optional: Receive alerts based on specific event types

To create alerts only for specific Datadog event types, open the advanced settings in your Datadog alert source and select the desired types from the **Event types** selection.

{% hint style="info" %}
Note that only the selected Datadog event types will create or resolve an alert in ilert; any other event types will be ignored. When no selections are made, all event types will create an alert.
{% endhint %}

<figure><img src="../.gitbook/assets/datadog-advanced-1.png" alt=""><figcaption></figcaption></figure>

## FAQ <a href="#faq" id="faq"></a>

**Are alerts in ilert automatically resolved?**

Yes, as soon as an Incident is closed in Datadog, the corresponding Alert is automatically resolved in ilert. Note: Downtime monitors will only resolve if the alert source is configured with the [corresponding additional setting](datadog.md#optional-receive-alerts-based-on-specific-event-types).

**Can I link Datadog to several alert sources in ilert?**

Yes, create a webhook in Datadog for each alert source.\


## Further References <a href="#faq" id="faq"></a>

Here is the instruction on how to import metrics from Datadog and display them on your ilert status page: \
\
[Import metrics from Datadog](https://docs.ilert.com/incident-comms-and-status-pages/metrics/import-metrics-from-datadog)
