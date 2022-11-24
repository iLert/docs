---
description: Create alerts in ilert based on tickets from TOPdesk
---

# TOPdesk Inbound Integration

With the ilert TOPdesk integration, you can create alerts in ilert based on TOPdesk event such as tickets or calls.

## In ilert <a href="#in-ilert" id="in-ilert"></a>

### Create a TOPdesk alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "TOPdesk" as the **Integration Type** and click on **Save**.

![](../../.gitbook/assets/tpdki1.png)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the hook in TOPdesk.

![](../../.gitbook/assets/tpdki2.png)

## In TOPdesk <a href="#in-topdesk" id="in-topdesk"></a>

> In this guide we will use **First Line Ticket** service for the integration. You can use any other service to sync with ilert.

### Create action sequences <a href="#create-action-sequences" id="create-action-sequences"></a>

1. Go to TOPdesk and then to **Modules**

![](../../.gitbook/assets/tpdki3.png)

1. Click on **Action Management** and then on **Action sequence** to add an action sequence

![](../../.gitbook/assets/tpdki4.png)

1. On the modal window, choose a service you are interested in e.g. **Ticket Management - First Line Ticket** and click on **Create new action sequence**

![](<../../.gitbook/assets/tpdki5 (1).png>)

1. In the **Name** section, enter a name eg. `iLert Create Alert Action`
2. In the **Available** section, ensure that the **Active**, **Apply in the Self-Service Portal** and **Apply in the Operator's Section** checkboxes are checked
3. In the **Step 1** section **Name** field, enter a name e.g. `ilert_create_incident`
4. In the **Step 1** section **HTTP Method** field, choose **POST**
5. In the **Step 1** section **URL** field, paste the **Webhook URL** that you generated in ilert
6. In the **Step 1** section **Headers** field, add **Content-Type: application/json** and **Accept: application/json**
7. In the **Step 1** section **Body** field, copy and paste the following JSON payload

```javascript
{
"eventType": "ALERT",
"incidentKey": "${naam}",
"summary": "${korteomschrijving}"
}
```

![](../../.gitbook/assets/tpdki6.1.png)

1. _Optional_: Add more entries to the request body to show custom information in an ilert alert. You can find more TOPdesk variables in the **DataDict**

![](../../.gitbook/assets/tpdki7.png)

**For example:** to add ticket caller to ilert alert details just add `persoonid` variable on the top-level of json body

```javascript
{
"eventType": "ALERT",
"incidentKey": "${naam}",
"summary": "${korteomschrijving}",
"persoonid": "${persoonid}"
}
```

1. Click on **Save**
2. Go to **Modules** again
3. Click on **Action Management** and then on **Action sequence** to add an action sequence

![](<../../.gitbook/assets/tpdki4 (1) (1).png>)

1. On the modal window, choose a service you are interested in e.g. **Ticket Management - First Line Ticket** and click on **Create new action sequence**

![](<../../.gitbook/assets/tpdki5 (2).png>)

1. In the **Name** section, enter a name eg. `iLert Create Alert Action`
2. In the **Available** section, ensure that the **Active**, **Apply in the Self-Service Portal** and **Apply in the Operator's Section** checkboxes are checked
3. In the **Step 1** section **Name** field, enter a name eg. `ilert_resolve_incident`
4. In the **Step 1** section **HTTP Method** field, choose **POST**
5. In the **Step 1** section **URL** field, paste the **Webhook URL** that you generated in ilert
6. In the **Step 1** section **Headers** field, add **Content-Type: application/json** and **Accept: application/json**
7. In the **Step 1** section **Body** field, copy and paste the following JSON payload

```javascript
{
"eventType": "RESOLVE",
"incidentKey": "${naam}",
"summary": "${korteomschrijving}"
}
```

![](../../.gitbook/assets/tpdki6.2.png)

1. Click on **Save**

### Create events <a href="#create-events" id="create-events"></a>

1. Go to **Modules**
2. Click on **Action Management** and then on **Event** to add a new event

![](../../.gitbook/assets/tpdki8.png)

1. On the modal window, choose a service you are interested in e.g. **Ticket Management - First Line Ticket** and click on **Create new event**

![](<../../.gitbook/assets/tpdki9 (1) (1).png>)

1. In the **Details** section **Name** field, enter a name eg. `iLert - Create Alert Event`
2. In the **Details** section **Active** field, ensure that checkbox is checked
3. In the **Details** section **Choose type** field, choose **New card**
4. In the **Linked actions** section, choose the action sequence `iLert - Create Alert Action` that you created in the last step
5. _Optional_: You can choose another card type (e.g. **Edit card**) and add conditions or specifications for your use case (e.g. Status changed to "Open"). In this case an ilert alert will be created only if event conditions and specifications match.

![](../../.gitbook/assets/tpdki10.1.png)

1. Click on **Save**
2. Go to **Modules** again
3. Click on **Action Management** and then on **Event** to add a new event

![](<../../.gitbook/assets/tpdki8 (1) (1).png>)

1. On the modal window, choose a service you are interested in e.g. **Ticket Management - First Line Ticket** and click on **Create new event**

![](<../../.gitbook/assets/tpdki9 (1).png>)

1. In the **Details** section **Name** field, enter a name eg. `iLert - Resolve Alert Event`
2. In the **Details** section **Active** field, ensure that checkbox is checked
3. In the **Details** section **Choose type** field, choose **Edit card**
4. In the **Linked actions** section, choose the action sequence `iLert - Resolve alert` that you created in the last step
5. _Optional_: You can add conditions or specifications for your use case (e.g. ticket was closed). In this case an ilert alert will be resolved only if event conditions and specifications match.

![](../../.gitbook/assets/tpdki10.2.png)

1. Click on **Save**

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes

**Can I connect TOPdesk with multiple alert sources from ilert?**

Yes, simply create more action sequences in TOPdesk.

**Can I customize the alert messages?**

Yes, any custom field will be shown in the alert details.
