---
description: >-
  The iLert ServiceNow Outbound Integration helps you to easily connect iLert
  with ServiceNow.
---

# ServiceNow Outbound Integration

[ServiceNow](http://www.servicenow.com/) is a platform-as-a-service \(PaaS\) provider of enterprise Service Management \(SM\) software.

## In iLert: Create ServiceNow Connector and link to alert source <a id="alarm-sources"></a>

1. Click the gear icon → **Connectors**

![](../../.gitbook/assets/go_to_connectors%20%281%29.png)

2. Click **Create Connector**

![](../../.gitbook/assets/create_connector_button%20%286%29.png)

3. Select **ServiceNow** as **type** and fill out all fields.

![](../../.gitbook/assets/ilert%20%2870%29.png)

4. Switch to the **alert sources** tab and open the alert source whose incidents you want to publish in ServiceNow. Click on **Incident actions → Create incident action**

![](../../.gitbook/assets/new_incident_action%20%2810%29.png)

5. Select **ServiceNow** as the **type**, select the connector created in step 3, fill in all fields.

![](../../.gitbook/assets/ilert%20%2881%29.png)

6. Finished! You can now test the connection by clicking the **Test this connection** button. A test issue is then published in ServiceNow.

![](../../.gitbook/assets/ilert%20%2867%29.png)

## In ServiceNow: Create iLert user <a id="create-user"></a>

1. Go to the **User Administration** area

![](../../.gitbook/assets/sn1.png)

2. Live an internal iLert user and click **Submit**

![](../../.gitbook/assets/sn2.png)

3. Call up the iLert user page and click the **Edit** button in the **Roles** tab.

![](../../.gitbook/assets/sn3.png)

4. Select the **incident\_manager** role and click **Save** .

![](../../.gitbook/assets/sn4.png)

## FAQ <a id="faq"></a>

**Are updates to an incident published in the ServiceNow Incident?**

Yes, the status of the iLert Incident is shown in the title of the JIRA ticket, eg `RESOLVED` Host compute.infra is `DOWN`.

**Can I choose which updates to an incident are published in ServiceNow?**

Currently not. If you wish, we look forward to your feedback via chat or email.

