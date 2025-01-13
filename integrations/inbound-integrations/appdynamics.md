---
title: AppDynamics Integration
seoTitle: 'iLert: AppDynamics Integration for Alerting | Incident Response | Uptime'
date: '2020-02-28T05:02:05.000Z'
type: post
description: Create alerts in ilert based on custom thresholds from AppDynamics
---

# AppDynamics Integration

AppDynamics provides application performance management (APM) and IT operations analytics across cloud computing environments as well as inside the data center.

With ilert's AppDynamics integration, you can automatically create alerts in ilert based on custom thresholds from AppDynamics. That way, you will never miss a critical alert and always alert the right person using ilert's on-call schedules, automatic escalation, and multiple alerting channels. When a threshold in AppDynamics is exceeded, ilert will alert the on-call person through their preferred channel, including SMS, phone calls, push notifications and Slack. ilert will automatically escalate to the next person, if the alert is not acknowledged. ilert also lets you define alerting rules based on support hours and delay alerts until your support hours start.

## In ilert: Create an AppDynamics alert source <a href="#create-alert-source" id="create-alert-source"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FjX0cS4q7woTXKajZmc1W%2FScreenshot%202023-08-28%20at%2010.21.10.png?alt=media&#x26;token=8ef3666b-84eb-4b51-abee-f07303313941" alt=""><figcaption></figcaption></figure>
2.  Search for **AppDynamics** in the search field, click on the AppDynamics tile and click on **Next**.

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FlXzQlJpaTFSR49AZk0xA%2FScreenshot%202023-08-28%20at%2010.24.23.png?alt=media&#x26;token=cffeacb4-57b9-47d4-827d-b0f6b1afd914" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FNnuZqONaIhbOf6fn4OkZ%2FScreenshot%202023-08-28%20at%2011.37.47.png?alt=media&#x26;token=8a74f7b5-5bd2-4eea-97fa-1c1dbb041333" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](https://docs.ilert.com/alerting/alert-sources#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FueugN4JgHn1c90ggFA6u%2FScreenshot%202023-08-28%20at%2011.38.24.png?alt=media&#x26;token=b8009daf-3ca8-4264-a6fa-e42ef7333205" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.​

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2Fi3TIOBvNYBQfDtNpmm0A%2FScreenshot%202023-08-28%20at%2011.47.34.png?alt=media&#x26;token=6cae965a-e448-4443-8c20-37cf501c43b2" alt=""><figcaption></figcaption></figure>

## In AppDynamics: Create HTTP Request Template <a href="#in-appdynammics" id="in-appdynammics"></a>

1. Go to **Alert & Respond** --> **HTTP Request Templates** and click on **New** to add a new template

![](../../.gitbook/assets/ad1.png)

2. Give the template a name (e.g. "ilert Notification") and add the following **Custom Templating Variables**:
3. `ilertApiKey` - set it to the alert sources's API key from above
4. `ilertEventType` - set it to `ALERT`
5. In the **Request URL** section, set the the **Method** to `POST` and the **Raw URL** to `https://api.ilert.com/api/v1/events`

![](../../.gitbook/assets/ad2.png)

6. In the **Custom Request Headers** section, add the following header `Accept`: `application/json`
7. In the _Payload_ section, set the MIME type to `application/json` and copy and paste the following JSON payload:

```
{
"apiKey": "${ilertApiKey}",
"eventType": "${ilertEventType}",
"incidentKey": "${latestEvent.node.name} - ${latestEvent.application.name}",
"summary": "${latestEvent.displayName} on ${latestEvent.node.name}"
}
}
```

![](../../.gitbook/assets/ad3.png)

8. In the **Response Handling Criteria** section, add the following **Success Criteria**

![](../../.gitbook/assets/ad4.png)

9. Under **Settings**, check **One Request Per Event** and click on **Save**

![](../../.gitbook/assets/ad5.png)

\*\*\*\*

### Test the HTTP Request Template

You can now test the template to make sure an alert is created in ilert.

1. Click the _Test_ button at the bottom of the page
2. Click _Add Event Type_ and select any event and then click _Run Test_.

![](../../.gitbook/assets/ad6.png)

3. Go to ilert and check that an alert has been created by AppDynamics.

### Create action

1. Go to **Actions** in the left navigation menu, select an application, server or database to create the action for, and click **Create**

![](../../.gitbook/assets/ad7.png)

2. Select **HTTP Request** from the list and click **OK**.

![](../../.gitbook/assets/ad8.png)

3. Give the action a name, e.g. "ilert Alert" and select the ilert **HTTP Request Template** from above and click on **Save**.

![](../../.gitbook/assets/ad9.png)

4. Create another action that will be used to resolve alerts in ilert. Give the action a name (e.g. “ilert Resolve”) and select the same HTTP template again. Change the `iLertEventType` from `ALERT` to `RESOLVE`, then click **Save**.

![](../../.gitbook/assets/ad10.png)

### Create policy

1. You can use the above actions in your policies. Go to **Policies** in the left navigation menu, select an application, server or database to create the policy for, and click **Create**

![](../../.gitbook/assets/ad11.png)

2. On the **Triggers** tab, create a new policy with the settings that should create alerts in ilert.

![](../../.gitbook/assets/ad12.png)

3. Switch to the **Actions** tab and add the **ilert Alert** that you've created above. Then, click on **Save**.

![](../../.gitbook/assets/ad13.png)

![](../../.gitbook/assets/ad14.png)

4. Now repeat the last 3 steps with your desired recovery conditions to have alerts in ilert close automatically when your application, server or database in AppDynamics recovers.

![](../../.gitbook/assets/ad15.png)

![](../../.gitbook/assets/ad16.png)

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as the recovery conditions of application, server or database are met, the alert in ilert will be resolved automatically.

**Can I use AppDynamics with multiple alert sources from ilert?**

Yes, you can create arbitrary mappings between your applications in AppDynamics and alert sources in ilert. Simply create additional actions in AppDynamics using the same HTTP Request Template with a different `ilertApiKey`.

**Can I customize the alert messages?**

Yes, you can customize the events sent to ilert by changing the JSON payload in the **Payload** section of the **HTTP Request Template**.
