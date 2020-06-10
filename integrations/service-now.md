---
title: ServiceNow Integration
seoTitle: 'iLert: ServiceNow Integration for Alerting | Incident Response | Uptime'
description: >-
  The iLert ServiceNow Integration helps you to easily connect iLert with
  ServiceNow.
date: '2018-12-29T05:02:05.000Z'
weight: 1
---

# ServiceNow Integration

## In iLert: Create ServiceNow Connector and link to alert source <a id="alarm-sources"></a>

1. Click the gear icon → **Connectors**
2. Click **Add Connector**
3. Select **ServiceNow** as **type** and fill out all fields.
4. Switch to the **alert sources** tab and open the alert source whose incidents you want to publish in ServiceNow. Click on **Connections → Add new connection**
5. Select **ServiceNow** as the **type**, select the connector created in step 3, fill in all fields.
6. Finished! You can now test the connection by clicking the **Test this connection** button. A test issue is then published in ServiceNow.

## In ServiceNow: Create iLert user <a id="create-user"></a>

1. Go to the **User Administration** area
2. Live an internal iLert user and click **Submit**
3. Call up the iLert user page and click the **Edit** button in the **Roles** tab.
4. Select the **incident\_manager** role and click **Save** .

## FAQ <a id="faq"></a>

**Are updates to an incident published in the ServiceNow Incident?**

Yes, the status of the iLert Incident is shown in the title of the JIRA ticket, eg `RESOLVED` Host compute.infra is `DOWN`.

**Can I choose which updates to an incident are published in ServiceNow?**

Currently not. If you wish, we look forward to your feedback via chat or email.

