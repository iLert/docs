---
title: AppDynamics Integration
seoTitle: 'iLert: AppDynamics Integration for Alerting | Incident Response | Uptime'
description: >-
  The iLert AppDynmics integration guide helps you to easily connect iLert with
  AppDynamics.
date: '2020-02-28T05:02:05.000Z'
type: post
---

# AppDynamics Integration

AppDynamics provides application performance management \(APM\) and IT operations analytics across cloud computing environments as well as inside the data center.

With the iLert AppDynamics integration, you can create incidents in iLert based on custom thresholds from AppDynamics.

## In iLert: create an AppDynamics alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click "Create new alert source"
2. Enter a name and select your desired escalation policy. Select "AppDynamics" as the **Integration Type**.
3. Click **Save**. You're going to need the alert source's API key in AppDynamics.

## In AppDynamics <a id="in-appdynammics"></a>

### Create HTTP Request Template

1. Go to **Alert & Respond** --&gt; **HTTP Request Templates** and click on **New** to add a new template
2. Give the template a name \(e.g. "iLert Notification"\) and add the following **Custom Templating Variables**:
   * `ilertApiKey` - set it to the alert sources's API key from above
   * `ilertEventType` - set it to `ALERT`
3. In the **Request URL** section, set the the **Method** to `POST` and the **Raw URL** to `https://api.ilert.com/api/v1/events`
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

6. In the **Response Handling Criteria** section, add the following **Success Criteria**
7. Under **Settings**, check **One Request Per Event** and click on **Save**

### Test the HTTP Request Template

You can now test the template to make sure an incident is created in iLert.

1. Click the _Test_ button at the bottom of the page
2. Click _Add Event Type_ and select any event and then click _Run Test_.
3. Go to iLert and check that an incident has been created by AppDynamics.

### Create action

1. Go to **Actions** in the left navigation menu, select an application, server or database to create the action for, and 

   click **Create**

2. Select **HTTP Request** from the list and click **OK**.
3. Give the action a name, e.g. "iLert Alert" and select the iLert **HTTP Request Template** from above and click on **Save**.
4. Create another action that will be used to resolve incidents in iLert. Give the action a name \(e.g. “iLert Resolve”\) 

   and select the same HTTP template again. Change the `iLertEventType` from `ALERT` to `RESOLVE`, then click **Save**.

### Create policy

1. You can use the above actions in your policies. Go to **Policies** in the left navigation menu, select an application, server or database to create the policy for, and 

   click **Create**

2. On the **Triggers** tab, create a new policy with the settings that should create incidents in iLert.
3. Switch to the **Actions** tab and add the **iLert Alert** that you've created above. Then, click on **Save**. 
4. Now repeat the last 3 steps with your desired recovery conditions to have incidents in iLert close automatically 

   when your application, server or database in AppDynamics recovers.

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

Yes, as soon as the recovery conditions of application, server or database are met, the incident in iLert will be resolved automatically.

**Can I use AppDynamics with multiple alert sources from iLert?**

Yes, you can create arbitrary mappings between your applications in AppDynamics and alert sources in iLert. Simply create additional actions in AppDynamics using the same HTTP Request Template with a different `ilertApiKey`.

**Can I customize the incident messages?**

Yes, you can customize the events sent to iLert by changing the JSON payload in the **Payload** section of the **HTTP Request Template**.

