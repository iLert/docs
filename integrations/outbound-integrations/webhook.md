---
description: The ilert Webhook Integration helps you to easily connect ilert with Webhooks.
---

# Webhook Integration

## In iLert: Create a Webhook Alert Action <a href="#create-webhook" id="create-webhook"></a>

1. Navigate to the **Alert Sources** tab and open the alert source whose alerts you want to publish via a webhook. Click on **Alert Actions → Create New Alert Action**.

   ![](<../../.gitbook/assets/new_incident_action (7).png>)

2. Select **Webhook** as the action **Type** and fill out the required fields. 
   - In the **Filter Alert Events** field, select the alert events that should trigger a webhook call. 
   - Webhook events are sent as `HTTP POST` requests to the specified URL. The URL must be publicly accessible.
   - Click **Save** to finalize the setup.

   ![](<../../.gitbook/assets/iLert (56).png>)

## Webhook Payload <a href="#payload" id="payload"></a>

When an alert event occurs, iLert sends a webhook request with a JSON payload. Below is an example of a webhook payload:

```json
{
     "id": "2983781",
     "status": "ACCEPTED",
     "summary": "PROBLEM Host Alert: app.compute is DOWN",
     "details": "details",
     "reportTime": "2019-08-29T09:52:39.551Z",
     "eventType": "incident-acknowledged",
     "priority": "LOW",
     "alertKey": "zabbix-12345",
     "alertSource": {
         "id": 2101194,
         "name": "Nagios Network and Hosts"
     },
     "assignedTo": {
         "username": "abr",
         "email": "example@example.com",
         "firstName": "Andreas",
         "lastName": "Farmer"
     }
}
```

For more details on the **status** or **eventType** fields, refer to the _Template Variables Explained_ section.

## Custom Webhook Payload / Request Body <a href="#custom" id="custom"></a>

You can customize the webhook's HTTP POST request body by enabling the **Custom Fields** option.

![](../../.gitbook/assets/Notification_Center.png)

This allows you to define a custom payload. If the template is invalid, the border will turn yellow or red.

![](../../.gitbook/assets/wh5.png)

If the template is valid, the border will turn green. You can also use iLert-specific variables, formatted in **Mustache syntax** (`{{ VARNAME }}`), to dynamically replace data in the payload.

![](../../.gitbook/assets/wh6.png)

## Template Variables Explained

The following table describes the available template variables for webhooks:

| Variable Key        | Description                                                                                      |
|---------------------|--------------------------------------------------------------------------------------------------|
| `alertId`          | The unique ID of the alert.                                                                      |
| `alertKey`         | The identifier for the initial event that created the alert.                                     |
| `alertDetails`     | Full details of the alert.                                                                       |
| `alertSummary`     | A brief summary of the alert.                                                                    |
| `alertStatus`      | Status of the alert (`PENDING`, `ACCEPTED`, or `RESOLVED`).                                     |
| `alertPriority`    | The alert's priority (`HIGH` or `LOW`).                                                          |
| `alertUrl`        | A URL linking to the alert in iLert.                                                             |
| `alertSourceId`   | The unique ID of the alert's source.                                                             |
| `alertSourceName` | The name of the alert's source.                                                                  |
| `escalationPolicyId`   | The ID of the escalation policy related to the alert source.                                 |
| `escalationPolicyName` | The name of the escalation policy related to the alert source.                              |
| `reportTime`      | The alert report timestamp in ISO-8601 format.                                                   |
| `link`            | The first link found in the alert payload (e.g., a link to the originating monitoring tool).     |
| `eventType`       | The type of event (`alert-created`, `alert-assigned`, `alert-auto-escalated`, etc.).             |

## Testing Webhooks with Beeceptor and Alternatives

To test your webhook integration, you can use tools like:

- **[Beeceptor](https://beeceptor.com/)** - A powerful tool for capturing and inspecting webhook requests.
- **[Webhook.site](https://webhook.site/)** - Another alternative for testing and debugging webhooks.

Simply replace the webhook URL in your alert action settings with the test endpoint provided by these tools to see and analyze the requests.

## FAQ <a href="#faq" id="faq"></a>

### **Do you support authentication?**

Yes, iLert webhooks support **HTTP Basic Authentication**. Include the username and password directly in the URL.

**Example:**
```
https://username:password@example.com/webhooks/ilert
```
Special characters in the username or password must be [URL-encoded](https://www.w3schools.com/tags/ref_urlencode.asp).

### **Can I specify a custom HTTP port?**

Yes. By default, webhooks use:

- **Port 80** for HTTP
- **Port 443** for HTTPS

To use a different port, append it after the host address using `:`.

**Example:**
```
https://example.com:8443/webhooks/ilert
```

### **Can I whitelist iLert webhook IP addresses for my firewall?**

Whitelisting all webhook IP addresses is not feasible as they may change. However, iLert offers **static IP agents** with its **Premium plan**. You can find the list of static IP addresses [here](../../alerting/phone-numbers/#email-services).
