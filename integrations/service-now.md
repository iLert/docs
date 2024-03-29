---
title: ServiceNow Integration
seoTitle: 'iLert: ServiceNow Integration for Alerting | Incident Response | Uptime'
description: >-
  The ilert ServiceNow Integration helps you to easily connect ilert with
  ServiceNow.
date: '2018-12-29T05:02:05.000Z'
weight: 1
---

# ServiceNow Integration

## In ilert: Create ServiceNow Connector and link to alert source <a id="alarm-sources"></a>

1. Click the gear icon → **Connectors**

![](../.gitbook/assets/sn5.png)

2. Click **Add Connector**

![](../.gitbook/assets/sn6.png)

3. Select **ServiceNow** as **type** and fill out all fields.

![](../.gitbook/assets/sn7.png)

4. Switch to the **alert sources** tab and open the alert source whose alerts you want to publish in ServiceNow. Click on **Connections → Add new connection**

![](../.gitbook/assets/sn8.png)

5. Select **ServiceNow** as the **type**, select the connector created in step 3, fill in all fields.

![](../.gitbook/assets/sn9.png)

6. Finished! You can now test the connection by clicking the **Test this connection** button. A test issue is then published in ServiceNow.

![](../.gitbook/assets/sn10.png)

## In ServiceNow: Create ilert user <a id="create-user"></a>

1. Go to the **User Administration** area

![](../.gitbook/assets/sn1.png)

2. Live an internal ilert user and click **Submit**

![](../.gitbook/assets/sn2.png)

3. Call up the ilert user page and click the **Edit** button in the **Roles** tab.

![](../.gitbook/assets/sn3.png)

4. Select the **incident\_manager** role and click **Save** .

![](../.gitbook/assets/sn4.png)

## FAQ <a id="faq"></a>

**Are updates to an alert published in the ServiceNow Alert?**

Yes, the status of the ilert Incident is shown in the title of the JIRA ticket, eg `RESOLVED` Host compute.infra is `DOWN`.

**Can I choose which updates to an alert are published in ServiceNow?**

Currently not. If you wish, we look forward to your feedback via chat or email.

