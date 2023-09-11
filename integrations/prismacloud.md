---
description: Palo Alto Network Prisma Cloud Integration
---

# Prisma Cloud Integration

## In ilert: Create a Prisma Cloud alert source

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Prisma Cloud** in the search field, click on the Prisma Cloud tile and click on **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## &#x20;<a href="#create-topic" id="create-topic"></a>

## In Prisma Cloud

Open your console and navigate to Mange -> Alerts\
You may also follow the official guide ([which can be found here](https://docs.paloaltonetworks.com/prisma/prisma-cloud/prisma-cloud-admin-compute/alerts/webhook.html))

Create a **new webhook alert** and make sure to paste your alert source's url as **incoming webhook url.** We suggest the following template that should be used as **custom json** for your webhook:

```
{
    "type": #type,
    "time": #time,
    "container": #container,
    "image": #image,
    "host": #host,
    "fqdn": #fqdn,
    "function": #function,
    "region": #region,
    "runtime": #runtime,
    "appID": #appID,
    "rule": #rule,
    "message": #message,
    "forensics": #forensics,
    "accountID": #accountID,
    "cluster": #cluster,
    "labels": #labels,
    "collections": #collections
}
```

Feel free to test your configuration with **Send test alert**.

Setup the alert channels and triggers to your liking and click **Save**.
