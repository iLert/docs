---
title: Dynatrace Integration
seoTitle: 'iLert: Dynatrace Integration for Alerting | Incident Response | Uptime'
description: >-
  The ilert Dynatrace integration helps you to easily connect ilert with
  Dynatrace.
date: '2020-02-28T05:02:05.000Z'
type: post
---

# Dynatrace Integration

With the ilert Dynatrace integration, you can add alerts in ilert based on problems from Dynatrace.

## In ilert: Create a Dynatrace alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click "Create new alert source"
2. Enter a name and select your desired escalation policy. Select "Dynatrace" as the **Integration Type** and click **Save**.

![](../.gitbook/assets/dyn5.png)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up Dynatrace.

![](../.gitbook/assets/dyn6.png)

## In Dynatrace <a id="in-dynatrace"></a>

### Create HTTP Request Template

1. Go to **Settings** --&gt; **Integration** --&gt;  **Problem Notifications** and click on **Set up notifications** to add a new template

![](../.gitbook/assets/dyn1.png)

1. Select **Custom integration** 

![](../.gitbook/assets/dyn2.png)

1. In the **Name** section, enter a name \(e.g. "ilert Notification"\)
2. In the **Webhook URL** section, set the **Webhook URL** to the one generated in ilert
3. In the **Additional HTTP Headers** section, add the following headers `Accept`: `application/json` and `Content-Type`: `application/json`
4. In the _Custom payload_ section, set the MIME type to `application/json` and copy and paste the following JSON payload:

```text
{
 "State": "{State}",
 "ProblemID": "{ProblemID}",
 "ProblemTitle": "{ProblemTitle}",
 "ProblemURL": "{ProblemURL}",
 "ProblemDetailsText": "{ProblemDetailsText}"
}
```

![](../.gitbook/assets/dyn3.png)

1. Click the **Send test notification** button and you should receive a **Custom integration test successful** dialog message

![](../.gitbook/assets/dyn4.png)

1. Click **Save**

## FAQ <a id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as the recovery conditions of application, server or database are met, the alert in ilert will be resolved automatically.

**Can I setup Dynatrace with multiple alert sources from ilert?**

Yes, you can create arbitrary mappings between your applications in Dynatrace and alert sources in ilert. Simply create additional actions in Dynatrace using the same HTTP Request Template with a different `ilertApiKey`.

**Can I customize the alert messages?**

Yes, you can customize the events sent to ilert by changing the JSON payload in the **Payload** section of the **HTTP Request Template**.

