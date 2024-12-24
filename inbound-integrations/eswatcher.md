---
description: >-
  With the ilert Elastic Watcher (formerly X-Pack Alerting) integration, you can
  create alerts in ilert based on Watcher alerts.
---

# Elastic Watcher Integration

[Elastic Watcher](https://www.elastic.co/guide/en/kibana/8.12/watcher-ui.html) is a set of administrative features that enable you to watch for changes or anomalies in your data and perform the necessary actions in response.

## In ilert: Create an Elastic Watcher alert source <a href="#in-ilert" id="in-ilert"></a>

1.  Go to **Alert sources** -> **Alert sources** and click **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Elastic Watcher** in the search field, click the Elastic Watcher tile, and click **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select your [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page shows additional settings, such as customer alert templates or notification priority. Click on **Finish setup** for now.
7.  On the final page, an API key and/or webhook URL will be generated, which you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Elastic Watcher <a href="#in-splunk" id="in-splunk"></a>

### Create a watcher <a href="#create-action-sequences" id="create-action-sequences"></a>

1. Go to Stack Management and then to **Alerts and Insights -> Watcher**, then click the **Create** button and the **Create advanced watch** button.

<figure><img src="../.gitbook/assets/1 (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

2. On the next page, name the watcher e.g. ilert, define conditions and actions the **Webhook URL** that you generated in ilert as follows:

<figure><img src="../.gitbook/assets/2 (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

```
{
    ...
    [CONFIGURATIONS OF YOUR ELASTIC WATCHER ALERT]
    ...
    "actions" : {
        "ilert" : {
            "webhook" : {
                "scheme" : "https",
                "method" : "POST",
                "host" : "api.ilert.com",
                "port" : 443,
                "path" : "/api/v1/events/eswatcher/[YOUR API KEY]",
                "headers" : {
                    "Content-Type" : "application/json"
                },
                "params": {},
                "body" : "{{#toJson}}ctx{{/toJson}}"
            }
        }
    }
}
```

3. Finished! Your Elastic Watcher will now create alerts in ilert.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

No, unfortunately, Elastic Watcher's notification is not compatible with ilert's resolve event.

**Can I connect Elastic Watcher with multiple alert sources from ilert?**

Yes, simply add more watchers in Elastic Watcher.
