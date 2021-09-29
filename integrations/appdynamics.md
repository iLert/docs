---
title: AppDynamics Integration
seoTitle: 'iLert: AppDynamics Integration for Alerting | Incident Response | Uptime'
description: Create alerts in iLert based on custom thresholds from AppDynamics
date: '2020-02-28T05:02:05.000Z'
type: post
---

# AppDynamics Integration

AppDynamics provides application performance management \(APM\) and IT operations analytics across cloud computing environments as well as inside the data center.

With iLert's AppDynamics integration, you can automatically create alerts in iLert based on custom thresholds from AppDynamics. That way, you will never miss a critical alert and always alert the right person using iLert's on-call schedules, automatic escalation, and multiple alerting channels. When a threshold in AppDynamics is exceeded, iLert will alert the on-call person through their preferred channel, including SMS, phone calls, push notifications and Slack. iLert will automatically escalate to the next person, if the alert is not acknowledged. iLert also lets you define alerting rules based on support hours and delay alerts until your support hours start.

## In iLert: create an AppDynamics alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click "Create new alert source"

2. Enter a name and select your desired escalation policy. Select "AppDynamics" as the **Integration Type**.  

![](../.gitbook/assets/ad17.png)

3. Click **Save**. You're going to need the alert source's API key in AppDynamics.  

![](../.gitbook/assets/ad18.png)

## In AppDynamics <a id="in-appdynammics"></a>

### Create HTTP Request Template

1. Go to **Alert & Respond** --&gt; **HTTP Request Templates** and click on **New** to add a new template  

![](../.gitbook/assets/ad1.png)

2. Give the template a name \(e.g. "iLert Notification"\) and add the following **Custom Templating Variables**:

* `ilertApiKey` - set it to the alert sources's API key from above
* `ilertEventType` - set it to `ALERT`

3. In the **Request URL** section, set the the **Method** to `POST` and the **Raw URL** to `https://api.ilert.com/api/v1/events`   

![](../.gitbook/assets/ad2.png)

4. In the **Custom Request Headers** section, add the following header `Accept`: `application/json`

5. In the _Payload_ section, set the MIME type to `application/json` and copy and paste the following JSON payload:

```text
{
"apiKey": "${ilertApiKey}",
"eventType": "${ilertEventType}",
"incidentKey": "${latestEvent.node.name} - ${latestEvent.application.name}",
"summary": "${latestEvent.displayName} on ${latestEvent.node.name}"
}
}
```

![](../.gitbook/assets/ad3.png)

6. In the **Response Handling Criteria** section, add the following **Success Criteria**

![](../.gitbook/assets/ad4.png)

7. Under **Settings**, check **One Request Per Event** and click on **Save**

![](../.gitbook/assets/ad5.png)

\*\*\*\*

### Test the HTTP Request Template

You can now test the template to make sure an alert is created in iLert.

1. Click the _Test_ button at the bottom of the page

2. Click _Add Event Type_ and select any event and then click _Run Test_.

![](../.gitbook/assets/ad6.png)

3. Go to iLert and check that an alert has been created by AppDynamics.

### Create action

1. Go to **Actions** in the left navigation menu, select an application, server or database to create the action for, and click **Create**

![](../.gitbook/assets/ad7.png)

2. Select **HTTP Request** from the list and click **OK**.

![](../.gitbook/assets/ad8.png)

3. Give the action a name, e.g. "iLert Alert" and select the iLert **HTTP Request Template** from above and click on **Save**.

![](../.gitbook/assets/ad9.png)

4. Create another action that will be used to resolve alerts in iLert. Give the action a name \(e.g. “iLert Resolve”\) and select the same HTTP template again. Change the `iLertEventType` from `ALERT` to `RESOLVE`, then click **Save**.

![](../.gitbook/assets/ad10.png)

### Create policy

1. You can use the above actions in your policies. Go to **Policies** in the left navigation menu, select an application, server or database to create the policy for, and click **Create**

![](../.gitbook/assets/ad11.png)

2. On the **Triggers** tab, create a new policy with the settings that should create alerts in iLert.

![](../.gitbook/assets/ad12.png)

3. Switch to the **Actions** tab and add the **iLert Alert** that you've created above. Then, click on **Save**. 

![](../.gitbook/assets/ad13.png)

![](../.gitbook/assets/ad14.png)

4. Now repeat the last 3 steps with your desired recovery conditions to have alerts in iLert close automatically when your application, server or database in AppDynamics recovers.

![](../.gitbook/assets/ad15.png)

![](../.gitbook/assets/ad16.png)

## FAQ <a id="faq"></a>

**Will alerts in iLert be resolved automatically?**

Yes, as soon as the recovery conditions of application, server or database are met, the alert in iLert will be resolved automatically.

**Can I use AppDynamics with multiple alert sources from iLert?**

Yes, you can create arbitrary mappings between your applications in AppDynamics and alert sources in iLert. Simply create additional actions in AppDynamics using the same HTTP Request Template with a different `ilertApiKey`.

**Can I customize the alert messages?**

Yes, you can customize the events sent to iLert by changing the JSON payload in the **Payload** section of the **HTTP Request Template**.

