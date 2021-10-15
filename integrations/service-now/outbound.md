---
description: >-
  The iLert ServiceNow Outbound Integration helps you to easily connect iLert
  with ServiceNow.
---

# ServiceNow Outbound Integration

[ServiceNow](http://www.servicenow.com) is a platform-as-a-service (PaaS) provider of enterprise Service Management (SM) software.

## In iLert: Create ServiceNow Connector and link to alert source <a href="alarm-sources" id="alarm-sources"></a>

1. Click the gear icon → **Connectors**

![](<../../.gitbook/assets/go_to_connectors (1) (1).png>)

1. Click **Create Connector**

![](<../../.gitbook/assets/create_connector_button (6).png>)

1. Select **ServiceNow** as **type** and fill out all fields.

![](<../../.gitbook/assets/iLert (64).png>)

1. Switch to the **alert sources** tab and open the alert source whose alerts you want to publish in ServiceNow. Click on **Alert actions → Create alert action**

![](<../../.gitbook/assets/new_incident_action (10).png>)

1. Select **ServiceNow** as the **type**, select the connector created in step 3, fill in all fields.

![](<../../.gitbook/assets/iLert (65).png>)

1. Finished! You can now test the connection by clicking the **Test this connection** button. A test issue is then published in ServiceNow.

![](<../../.gitbook/assets/iLert (66).png>)

## In ServiceNow: Create iLert user <a href="create-user" id="create-user"></a>

1. Go to the **User Administration** area

![](../../.gitbook/assets/sn1.png)

1. Live an internal iLert user and click **Submit**

![](../../.gitbook/assets/sn2.png)

1. Call up the iLert user page and click the **Edit** button in the **Roles** tab.

![](../../.gitbook/assets/sn3.png)

1. Select the **incident_manager** role and click **Save** .

![](../../.gitbook/assets/sn4.png)

## FAQ <a href="faq" id="faq"></a>

**Are updates to an alert published in the ServiceNow Alert?**

Yes, the status of the iLert Alert is shown in the title of the JIRA ticket, eg `RESOLVED` Host compute.infra is `DOWN`.

**Can I choose which updates to an alert are published in ServiceNow?**

Currently not. If you wish, we look forward to your feedback via chat or email.
