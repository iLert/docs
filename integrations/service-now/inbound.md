---
description: >-
  With the iLert ServiceNow integration, you can create alerts in iLert based on
  ServiceNow alerts.
---

# ServiceNow Inbound Integration

[ServiceNow](http://www.servicenow.com) is a platform-as-a-service (PaaS) provider of enterprise Service Management (SM) software.

## In iLert <a href="in-ilert" id="in-ilert"></a>

### Create a ServiceNow alert source <a href="create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click **Create new alert source**
2. Enter a name and select your desired escalation policy. Select "ServiceNow" as the **Integration Type** and click on **Save**.

![](../../.gitbook/assets/Screenshot\_09\_02\_21\__07\_51.png)

1. On the next page, a **ServiceNow URL** is generated. You will need this URL below when setting up the hook in ServiceNow.

![](../../.gitbook/assets/Screenshot\_09\_02\_21\__07\_52.png)

## In ServiceNow <a href="in-servicenow" id="in-servicenow"></a>

### Create business rule <a href="create-business-rule" id="create-business-rule"></a>

1. Go to ServiceNow, search for **Incidents**, **\*\*then open the header menu and choose **Configure -> Business Rules\*\*

![](../../.gitbook/assets/Screenshot\_08\_02\_21\__22\_40.png)

1. In the **Business Rules** view click on **New** to create a new business rule

![](../../.gitbook/assets/Screenshot\_08\_02\_21\__22\_42.png)

1. Name the business rule e.g. **iLert Alerts**, choose **Advanced** option, in the **When to run** section choose **async** then choose **Insert** and **Update** options

![](../../.gitbook/assets/Screenshot\_08\_02\_21\__22\_43.png)

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

![](../../.gitbook/assets/Screenshot\_08\_02\_21\__22\_46.png)

## ServiceNow Incident Lifecycle <a href="lifecycle" id="lifecycle"></a>

| When I create an ServiceNow ticket with status... | ...then an iLert Alert...                                             |
| ------------------------------------------------- | --------------------------------------------------------------------- |
| **New**                                           | is created                                                            |
| **In Progress** or **Complete** or **Closed**     | <p>will not be created and a</p><p>400 (bad request) error occurs</p> |

| When I update an ServiceNow ticket with status... | ...and the iLert alert... | ...then the/an iLert Alert...                                         |
| ------------------------------------------------- | ------------------------- | --------------------------------------------------------------------- |
| **New**                                           | does not exist            | is created                                                            |
| **In Progress** or **Complete** or **Closed**     | does not exist            | <p>will not be created and a</p><p>400 (bad request) error occurs</p> |
| **New**                                           | exists                    | doesn't change                                                        |
| **Complete** or **Closed**                        | exists                    | change status to **Resolved** if not already resolved                 |
| **In Progress**                                   | exists                    | change status to **Accepted** if not already accepted                 |

## FAQ <a href="faq" id="faq"></a>

**Will alerts in iLert be resolved automatically?**

Yes

**Can I connect ServiceNow with multiple alert sources from iLert?**

Yes, simply create more business rules in ServiceNow.
