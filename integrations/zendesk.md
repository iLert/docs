---
title: Zendesk Integration
seoTitle: 'iLert: Zendesk Integration for Alerting | Incident Response | Uptime'
description: The iLert Zendesk Integration helps you to easily connect iLert with Zendesk.
date: '2018-12-29T05:02:05.000Z'
weight: 1
---

# Zendesk Integration

**Admin Rights Required**

You need to have admin rights to setup this integration.

## In iLert: create a Zendesk connector and link it with an alert source <a id="alarm-source"></a>

**Admin authorization required** To set up the integration, you must have admin rights in iLert.

1. Click the gear icon → **Connectors**
2. Click on **Add Connector**
3. Select **Zendesk Support** and fill in the details
4. Go to **Alert sources** and select the alert source you want to connect with Zendesk. Click on **Connections → Add new connections**.
5. Select **Zendesk Support** as Type and select the **Connector** that you've create in step 3. Pick a name and priority. Tickets created in Zendesk will have this priority. Click **Save**.
6. You're done! You can now test this connection by clicking on **Test this connection**. A test ticket will be created in Zendesk.

## In Zendesk: Create API Token <a id="api-token"></a>

1. Optional: create a dedicated iLert user in Zendesk. That way, you will be able to distinguish tickets created by iLert.
2. Go to admin settings, select the API channel, enable token access and create an API token. 
3. You will need this API token later in iLert. Make sure to copy and store it. You won't be able to see it again in Zendesk. Click **Save**.

## FAQ <a id="faq"></a>

**Are tickets updated in Zendesk if the incident is updated in iLert?**

Yes, status updates to iLert Incidents are reflected in the title of the Zendesk ticket, e.g. `RESOLVED` host compute.infra is `DOWN`.

**Can I choose which updates to publish to a ticket in Zendesk?**

Currently not. If that's something you'd like see in iLert, we look forward to your feedback via chat or e-mail.

