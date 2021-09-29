---
title: Github Outbound Issue Integration
seoTitle: 'iLert: Github Integration for Alerting | Incident Response | Uptime'
description: Create issues in GitHub based on alerts from iLert.
date: '2020-04-21T07:00:00.000Z'
weight: 1
---

# GitHub Outbound Issue Integration

## In Github: Create iLert user and create API token <a id="github-preparation"></a>

1. Optional: Create a dedicated iLert user in Github. This has the advantage that you can distinguish the Github tickets created by iLert.

2. Go to **Profile Settings** --&gt; **Developer settings** --&gt; **Personal access tokens**, and click **Generate new token**.

![](../../.gitbook/assets/ghoi1.png)

3. Give it a name and select **Repo Scope** for the token

![](../../.gitbook/assets/ghoi2.png)

4. Click on **Create**. Keep your API key for later, as it is needed in iLert.

![](../../.gitbook/assets/ghoi3.png)

![](../../.gitbook/assets/ghoi4.png)

## In iLert: Create a Github Connector and link to an alert source <a id="create-alarm-source"></a>

1. Click on the gear icon → **Connectors**

![](../../.gitbook/assets/go_to_connectors%20%287%29.png)

2. Click on **Add Connector**

![](../../.gitbook/assets/create_connector_button%20%281%29.png)

3. Select **Github** as **type** and fill in all fields. Enter a name and the API key from above.

![](../../.gitbook/assets/ghoi7.png)

4. **Go to** the alert sources tab and open the alert source whose alerts you want to publish in Github. Click on **Incident actions → Create alert action**.

![](../../.gitbook/assets/new_incident_action%20%285%29.png)

5. Select **Github** as the **type** then select the connector created in step 3 and fill in all fields. In the **Owner** and the **Repository** fields specify the owner and repository of the Github project where the iLert alerts should be published as Github Issue.

![](../../.gitbook/assets/ilert%20%2873%29.png)

6. Finished! You can now test the alert action by clicking on the button **Test this connection**. Then a test issue will be published in the respective Github project.

![](../../.gitbook/assets/ilert%20%2864%29.png)

## FAQ <a id="faq"></a>

**Are updates to an alert published in the Github Ticket?**

Yes, the state of the iLert Incident is reflected in the title of the Github ticket, eg. \[RESOLVED\] Host compute.infra is DOWN.

**Can I choose which updates should be published to an alert in Github?**

Currently not. If you wish we are looking forward to reading your feedback via chat or e-mail.

