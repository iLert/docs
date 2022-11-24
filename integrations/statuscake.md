---
title: StatusCake Integration
seoTitle: 'iLert: StatusCake Integration for Alerting | Incident Response | Uptime'
description: >-
  The ilert StatusCake integration helps you to easily connect ilert with
  StatusCake.
date: '2020-04-24T07:00:00.000Z'
weight: 1
---

# StatusCake Integration

With the ilert StatusCake integration, you can create alerts in ilert based on alerts from StatusCake.

## In ilert: Create a StatusCake alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click "Create new alert source"
2. Enter a name and select your desired escalation policy. Select "StatusCake" as the **Integration Type** and click **Save**.

![](../.gitbook/assets/stck1.png)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the hook in StatusCake.

![](../.gitbook/assets/stck2.png)

## In StatusCake <a id="in-statuscake"></a>

### Create a Contact Group

1. Go to StatusCake and then to **Alerting** and click on **New Contact Group** to add a new contact group \(`https://app.statuscake.com/ContactGroup.php`\)

![](../.gitbook/assets/stck3.png)

1. In the **Group Name** section, enter a name eg. ilert
2. In the **Repeat Alert** section, move the slider to the left so that it says **No Repeat Alerts**
3. In the **Webhook URL** section, paste the **Webhook URL** that you generated in ilert
4. In the **Webhook Method** section, choose **POST**
5. Optional: Send a test alert through the **Test** button

![](../.gitbook/assets/stck4.png)

1. Click **Save Now**

![](../.gitbook/assets/stck5.png)

## FAQ <a id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as the StatusCake alert is closed, the alert in ilert will be resolved automatically.

**Can I connect StatusCake with multiple alert sources from ilert?**

Yes, simply create more Contact Groups in StatusCake.

**Can I customize the alert messages?**

No.

