---
title: StatusCake Integration
seoTitle: 'iLert: StatusCake Integration for Alerting | Incident Response | Uptime'
date: '2020-04-24T07:00:00.000Z'
weight: 1
description: >-
  The ilert StatusCake integration helps you to easily connect ilert with
  StatusCake.
---

# StatusCake Integration

With the ilert StatusCake integration, you can create alerts in ilert based on alerts from StatusCake.

## In ilert: Create a StatusCake alert source <a href="#create-alert-source" id="create-alert-source"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **StatusCake** in the search field, click on the StatusCake tile and click on **Next**.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In StatusCake <a href="#in-statuscake" id="in-statuscake"></a>

### Create a Contact Group

1. Go to StatusCake and then to **Alerting** and click on **New Contact Group** to add a new contact group (`https://app.statuscake.com/ContactGroup.php`)

![](../.gitbook/assets/stck3.png)

2. In the **Group Name** section, enter a name eg. ilert
3. In the **Repeat Alert** section, move the slider to the left so that it says **No Repeat Alerts**
4. In the **Webhook URL** section, paste the **Webhook URL** that you generated in ilert
5. In the **Webhook Method** section, choose **POST**
6. Optional: Send a test alert through the **Test** button

![](../.gitbook/assets/stck4.png)

7. Click **Save Now**

![](../.gitbook/assets/stck5.png)

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as the StatusCake alert is closed, the alert in ilert will be resolved automatically.

**Can I connect StatusCake with multiple alert sources from ilert?**

Yes, simply create more Contact Groups in StatusCake.

**Can I customize the alert messages?**

No.
