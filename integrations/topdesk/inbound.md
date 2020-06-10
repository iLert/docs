---
title: TOPdesk Inbound Integration
seoTitle: 'iLert: TOPdesk Inbound Integration for Alerting | Incident Response | Uptime'
description: >-
  The iLert TOPdesk Inbound Integration helps you to easily connect iLert with
  TOPdesk.
date: '2020-04-29T07:00:00.000Z'
weight: 1
---

# TOPdesk Inbound Integration

With the iLert TOPdesk integration, you can create incidents in iLert based on TOPdesk event such as tickets or calls.

## In iLert <a id="in-ilert"></a>

### Create a TOPdesk alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "TOPdesk" as the **Integration Type** and click on **Save**.
3. On the next page, a Webhook URL is generated. You will need this URL below when setting up the hook in TOPdesk.

## In TOPdesk <a id="in-topdesk"></a>

> In this guide we will use **First Line Ticket** service for the integration. You can use any other service to sync with iLert.

### Create action sequences <a id="create-action-sequences"></a>

1. Go to TOPdesk and then to **Modules**
2. Click on **Action Management** and then on **Action sequence** to add an action sequence
3. On the modal window, choose a service you are interested in e.g. **Ticket Management - First Line Ticket** and click on **Create new action sequence**
4. In the **Name** section, enter a name eg. `iLert Create Incident Action`
5. In the **Available** section, ensure that the **Active**, **Apply in the Self-Service Portal** and **Apply in the Operator's Section** checkboxes are checked
6. In the **Step 1** section **Name** field, enter a name e.g. `ilert_create_incident`
7. In the **Step 1** section **HTTP Method** field, choose **POST**
8. In the **Step 1** section **URL** field, paste the **Webhook URL** that you generated in iLert
9. In the **Step 1** section **Headers** field, add **Content-Type: application/json** and **Accept: application/json**
10. In the **Step 1** section **Body** field, copy and paste the following JSON payload

    ```javascript
    {
    "eventType": "ALERT",
    "incidentKey": "${naam}",
    "summary": "${korteomschrijving}"
    }
    ```

11. _Optional_: Add more entries to the request body to show custom information in an iLert incident. You can find more TOPdesk variables in the **DataDict**

    **For example:** to add ticket caller to iLert incident details just add `persoonid` variable on the top-level of json body

    ```javascript
    {
    "eventType": "ALERT",
    "incidentKey": "${naam}",
    "summary": "${korteomschrijving}",
    "persoonid": "${persoonid}"
    }
    ```

12. Click on **Save**
13. Go to **Modules** again
14. Click on **Action Management** and then on **Action sequence** to add an action sequence
15. On the modal window, choose a service you are interested in e.g. **Ticket Management - First Line Ticket** and click on **Create new action sequence**
16. In the **Name** section, enter a name eg. `iLert Create Incident Action`
17. In the **Available** section, ensure that the **Active**, **Apply in the Self-Service Portal** and **Apply in the Operator's Section** checkboxes are checked
18. In the **Step 1** section **Name** field, enter a name eg. `ilert_resolve_incident`
19. In the **Step 1** section **HTTP Method** field, choose **POST**
20. In the **Step 1** section **URL** field, paste the **Webhook URL** that you generated in iLert
21. In the **Step 1** section **Headers** field, add **Content-Type: application/json** and **Accept: application/json**
22. In the **Step 1** section **Body** field, copy and paste the following JSON payload

    ```javascript
    {
    "eventType": "RESOLVE",
    "incidentKey": "${naam}",
    "summary": "${korteomschrijving}"
    }
    ```

23. Click on **Save**

### Create events <a id="create-events"></a>

1. Go to **Modules**
2. Click on **Action Management** and then on **Event** to add a new event
3. On the modal window, choose a service you are interested in e.g. **Ticket Management - First Line Ticket** and click on **Create new event**
4. In the **Details** section **Name** field, enter a name eg. `iLert - Create Incident Event`
5. In the **Details** section **Active** field, ensure that checkbox is checked
6. In the **Details** section **Choose type** field, choose **New card**
7. In the **Linked actions** section, choose the action sequence `iLert - Create Incident Action` that you created in the last step
8. _Optional_: You can choose another card type \(e.g. **Edit card**\) and add conditions or specifications for your use case \(e.g. Status changed to "Open"\). In this case an iLert incident will be created only if event conditions and specifications match.
9. Click on **Save**
10. Go to **Modules** again
11. Click on **Action Management** and then on **Event** to add a new event
12. On the modal window, choose a service you are interested in e.g. **Ticket Management - First Line Ticket** and click on **Create new event**
13. In the **Details** section **Name** field, enter a name eg. `iLert - Resolve Incident Event`
14. In the **Details** section **Active** field, ensure that checkbox is checked
15. In the **Details** section **Choose type** field, choose **Edit card**
16. In the **Linked actions** section, choose the action sequence `iLert - Resolve incident` that you created in the last step
17. _Optional_: You can add conditions or specifications for your use case \(e.g. ticket was closed\). In this case an iLert incident will be resolved only if event conditions and specifications match.
18. Click on **Save**

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

Yes

**Can I connect TOPdesk with multiple alert sources from iLert?**

Yes, simply create more action sequences in TOPdesk.

**Can I customize the incident messages?**

Yes, any custom field will be shown in the incident details.

