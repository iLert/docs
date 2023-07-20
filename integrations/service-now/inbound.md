---
description: >-
  With the ilert ServiceNow integration, you can create alerts in ilert based on
  ServiceNow tickets or sync alert updates back to ServiceNow
---

# ServiceNow Inbound Integration

[ServiceNow](http://www.servicenow.com/) is a platform-as-a-service (PaaS) provider of enterprise Service Management (SM) software.

## In ilert <a href="#in-ilert" id="in-ilert"></a>

### Create a ServiceNow alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "ServiceNow" as the **Integration Type** and click on **Save**.

![](../../.gitbook/assets/Screenshot\_09\_02\_21\_\_07\_51.png)

1. On the next page, a **ServiceNow URL** is generated. You will need this URL below when setting up the hook in ServiceNow.

![](../../.gitbook/assets/Screenshot\_09\_02\_21\_\_07\_52.png)

## In ServiceNow <a href="#in-servicenow" id="in-servicenow"></a>

### Create business rule <a href="#create-business-rule" id="create-business-rule"></a>

1. Go to ServiceNow, search for **Incidents**, **\*\*then open the header menu and choose** Configure -> Business Rules\*\*

![](../../.gitbook/assets/Screenshot\_08\_02\_21\_\_22\_40.png)

1. In the **Business Rules** view click on **New** to create a new business rule

![](../../.gitbook/assets/Screenshot\_08\_02\_21\_\_22\_42.png)

1. Name the business rule e.g. **ilert Alerts**, choose **Advanced** option, in the **When to run** section choose **async** then choose **Insert** and **Update** options

![](../../.gitbook/assets/Screenshot\_08\_02\_21\_\_22\_43.png)

1. Go to Advanced tab and paste the following code into the script section:

```
(function executeRule(current, previous /*null when async*/) {

    var iLertUrl = "<your alert source URL here>";


    function glideRecordToJson(gr) {
        var obj = {};
        for (var prop in gr) {
            if (gr[prop]){
                obj[prop] = gr.getValue(prop);
            }
        }
        return obj;
    }

    var obj = glideRecordToJson(current);
    obj.server_url = gs.getProperty("glide.servlet.uri");
    var body = JSON.stringify(obj);
    var request = new sn_ws.RESTMessageV2();
    request.setEndpoint(iLertUrl);
    request.setHttpMethod("POST");
    request.setRequestBody(body);
    request.setRequestHeader("Accept", "application/json");
    request.setRequestHeader("Content-Type", "application/json");

    var response = request.execute();
    gs.log(response.getBody());


})(current, previous);
```

1. Click on **Submit** or **Update** to save the business rule

![](../../.gitbook/assets/Screenshot\_08\_02\_21\_\_22\_46.png)

## ServiceNow Incident Lifecycle <a href="#lifecycle" id="lifecycle"></a>

| When I create an ServiceNow ticket with status... | ...then an ilert Alert...                                             |
| ------------------------------------------------- | --------------------------------------------------------------------- |
| **New**                                           | is created                                                            |
| **In Progress** or **Complete** or **Closed**     | <p>will not be created and a</p><p>400 (bad request) error occurs</p> |

| When I update an ServiceNow ticket with status... | ...and the ilert alert... | ...then the/an ilert Alert...                                         |
| ------------------------------------------------- | ------------------------- | --------------------------------------------------------------------- |
| **New**                                           | does not exist            | is created                                                            |
| **In Progress** or **Complete** or **Closed**     | does not exist            | <p>will not be created and a</p><p>400 (bad request) error occurs</p> |
| **New**                                           | exists                    | doesn't change                                                        |
| **Complete** or **Closed**                        | exists                    | change status to **Resolved** if not already resolved                 |
| **In Progress**                                   | exists                    | change status to **Accepted** if not already accepted                 |

## Advanced configuration

ilert's ServiceNow integration allows you to easily configure advanced settings such as dynamic escalation policy routing and priority mapping.

![](<../../.gitbook/assets/image (57) (1) (1) (1).png>)

To get access to the advanced features, you will have to provide access credentials to your ServiceNow instance first. The provided user will need the following permissions in ServiceNow:

* `sys_user`
* `sys_user_group`
* `cmdb_ci_service`
* `service_offering`
* `sys_choice`
* `sys_dictionary`

This will grant you access to:

### Dynamic priority mapping

When selecting priority mapping, ilert will contact your ServiceNow instance and fetch all available priorities of ServiceNow alerts. You will then be able to choose a mapping for each of these and determine how ilert will treat them when creating alerts in ilert.

![](<../../.gitbook/assets/image (55) (1) (2).png>)

### Dynamic escalation policy routing

When selecting escalation policy routing, ilert will contact your ServiceNow instance and fetch all available alert fields. You will then be able to choose an alert field that should be used for incoming alerts in ilert to determine the routing key.

![](<../../.gitbook/assets/image (51) (1).png>)

You may choose to give escalation policies in ilert a unique routing key.

![](<../../.gitbook/assets/image (54) (3).png>)

With an incoming event ilert will try to find the right escalation policy based on the routing key and assign the alert to the escalation policy. If no routing key is provided, ilert will use the assigned escalation policy of the alert source.

### Bidirectional alert synchronisation

When providing credentials you may choose to activate bidirectional mode on the ServiceNow alert sources. This will cause your alert source to be automatically linked with an outbound connector and alert action. This way status changes to ilert alerts will synchronize to ServiceNow tickets.

![](<../../.gitbook/assets/image (53) (1) (1) (1).png>)

When saving the ServiceNow alert source with the bidirectional setting enabled, it will automatically create an outbound connector for you and take you to the creation page of the necessary alert action, **please make sure to continue with the setup of the action to finish your bidirectional alert source setup.**



![](<../../.gitbook/assets/image (56) (1).png>)

### Good to know

\
In the bidirectional setup, ilert will try to map users automatically (if **Caller ID** in alert action is left empty) based on their email address. This accounts for actions taken in ilert and synced back to ServiceNow, as well as actions taken in ServiceNow and send to ilert.

{% hint style="warning" %}
Remember to leave the Caller ID field in the alert action empty for automated user mapping to work properly
{% endhint %}

When providing a **comment** to the alert in ilert while **resolving** it, ilert will make sure sync the comments content as **resolve information** to the alert in ServiceNow.

### Understanding ServiceNOW <-> ilert flows

Synchronously mapping the the ServiceNOW ticket/incident lifecycle to the immutable lifecycle of an ilert alert, is not a simple back and forth. The connector runs a lot of state comparisons to identify if a ticket/incident update is needed based on the latest change event of an alert.

| Incoming event                                                                                   | State check                                                                                                                                                                                                                | Outgoing change operation                                                                                                                                                        |
| ------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **New (1)** ticket event from ServiceNOW                                                         | If alert does not exist, it is created, otherwise the event is dropped (even if the corresponding alert for the ticket is in RESOLVED state) this is determined based on the **sys\_id** of the ticket                     | Nothing, except if the **priority** or **assignment** of the alert differs from the original ticket status e.g. through configurations of the alert source or escalation policy  |
| **In Progress (2)** or **Complete/Resolved (6)** or **Closed (7)** ticket update from ServiceNOW | <p>If the alert does not exist, the event is dropped, otherwise:<br><strong>status -> transition</strong><br><strong>priority -> raise</strong><br><strong>assignment -> re-routing</strong><br>Operations might occur</p> | Usually there should be no outbound event triggered through this change, however a re-route operation will likely trigger an asynchronous escalation or more as follow up events |
| Responder re-routes through ilert                                                                | A different escalation policy is assigned and escalation is restarted                                                                                                                                                      | If **assignmentGroup** or similar mappings are configured and they differ due to the changed **routingKey** of the assigned escalation policy the ticket will be updated         |
| Responder accepts through ilert                                                                  | Alert is accepted                                                                                                                                                                                                          | If the ticket is not yet accepted, the status will be updated to In Progress if                                                                                                  |
| Responder raises priority through ilert                                                          | Alert's priority is raised from **LOW** to **HIGH** and escalation of the assigned policy is triggered                                                                                                                     | Depending on the ticket's priority it is updated and                                                                                                                             |
| Automated escalation of alert in ilert                                                           | Reaching the next escalation level, might add new responders to the alert                                                                                                                                                  | This might assign the ticket to a different user                                                                                                                                 |
| Responder resolves through ilert                                                                 |                                                                                                                                                                                                                            | If the ticket is not yet in status **Complete/Resolved (6), Closed (7) or Canceled (8)** it will be updated                                                                      |

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes

**Can I connect ServiceNow with multiple alert sources from ilert?**

Yes, simply create more business rules in ServiceNow.
