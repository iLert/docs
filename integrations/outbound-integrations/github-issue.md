---
description: Create issues in GitHub based on alerts from ilert.
---

# GitHub Outbound Issue Integration

## In Github: Create an ilert user and create an API token <a href="#github-preparation" id="github-preparation"></a>

1. Optional: Create a dedicated ilert user in Github. This has the advantage that you can distinguish the Github tickets created by ilert.
2. Go to **Profile Settings** --> **Developer settings** --> **Personal access tokens**, and click **Generate new token**.

![](../../.gitbook/assets/ghoi1.png)

3. Give it a name and select **Repo Scope** for the token

![](../../.gitbook/assets/ghoi2.png)

4. Click on **Create**. Keep your API key for later, as it is needed in ilert.

![](../../.gitbook/assets/ghoi3.png)

![](../../.gitbook/assets/ghoi4.png)

## In ilert: Create a Github Connector and link to an alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1. Click on the gear icon → **Connectors**

![](<../../.gitbook/assets/go_to_connectors (7) (6).png>)

2. Click on **Add Connector**

![](<../../.gitbook/assets/create_connector_button (1) (13).png>)

2. Select **Github** as **type** and fill in all fields. Enter a name and the API key from above.

![](../../.gitbook/assets/ghoi7.png)

3. **Go to** the alert sources tab and open the alert source whose alerts you want to publish in Github. Click on **Incident actions → Create alert action**.

![](<../../.gitbook/assets/new_incident_action (5).png>)

4. Select **Github** as the **type** then select the connector created in step 3 and fill in all fields. In the **Owner** and the **Repository** fields specify the owner and repository of the Github project where the ilert alerts should be published as Github Issue.

![](<../../.gitbook/assets/iLert (76).png>)

5. Finished! You can now test the alert action by clicking on the button **Test this connection**. Then a test issue will be published in the respective Github project.

![](<../../.gitbook/assets/iLert (77).png>)

## FAQ <a href="#faq" id="faq"></a>

**Are updates to an alert published in the Github Ticket?**

Yes, the state of the ilert Incident is reflected in the title of the Github ticket, eg. \[RESOLVED] Host compute.infra is DOWN.

**Can I choose which updates should be published to an alert in Github?**

Currently not. If you wish we are looking forward to reading your feedback via chat or e-mail.



## Related articles

{% content-ref url="../inbound-integrations/github/inbound-issue.md" %}
[inbound-issue.md](../inbound-integrations/github/inbound-issue.md)
{% endcontent-ref %}
