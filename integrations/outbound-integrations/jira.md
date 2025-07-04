---
description: Create JIRA issues from ilert alerts.
---

# Jira Outbound Integration

## In JIRA: Create an ilert user and create API token <a href="#jira-preparation" id="jira-preparation"></a>

1. Optional: Create a dedicated ilert user in JIRA. This has the advantage that you can distinguish the JIRA tickets created by ilert.
2. Go to **Atlassian account settings** **→** **Security** and click on **Create and Manage API Tokens**.

![](<../../.gitbook/assets/Screenshot 2020-08-05 at 13.15.25.png>)

3. Click on the button **Create API token**

![](../../.gitbook/assets/ji2.png)

4. Give a name and click **Create**. Write down your API key. You will need it later in ilert.

![](../../.gitbook/assets/ji3.png)

![](../../.gitbook/assets/ji4.png)

## In ilert: Create a JIRA Connector and link to alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1. Click the gear icon → **Connectors**

![](<../../.gitbook/assets/go_to_connectors (6).png>)

2. Click **Add Connector**

![](<../../.gitbook/assets/create_connector_button (5).png>)

3. Select **JIRA** as **type** and fill in all fields. Enter as URL the URL of your JIRA instance and as password the API key above.

![](<../../.gitbook/assets/iLert (63).png>)

4. **Go to** the alert sources tab and open the alert source whose alerts you want to publish in JIRA. Click **Alert actions → Create new alert action**.

![](<../../.gitbook/assets/new_incident_action (2).png>)

5. Select **JIRA** as the **type** and in the secondary dropdown select the connector created in step 3. ilert will now try to fetch the available Projects and Issue Types from your provided Jira instance.

![](<../../.gitbook/assets/iLert (60).png>)

Select the desired Project and Issue Type that should be used to create issues and give the alert action a name, before clicking on save.

## Custom Variables and request configuration <a href="#custom" id="custom"></a>

Optionally you may choose to customize the request that will be made to your JIRA instance, by choosing the custom fields option. (This will overwrite the HTTP request body content `fields` with your provided variables. Our template editor will help you to send a valid request), you may also click on "Show me the available issue type fields" in case you do not have the keys handy.

![](../../.gitbook/assets/ji10.png)

In case of an invalid template the border will become red.

![](../../.gitbook/assets/ji11.png)

In case of a valid template the border will turn green. As you may have noticed we also offer to use ilert related variables that will be swapped with the corresponding event related data when the request is made. These work, as described under the template field in simple mustache sytnax `{{ VARNAME }}`. Again our editor will tell you if you are using the variables incorrectly.

![](../../.gitbook/assets/ji12.png)

Just save the connector and your done. You can now test the connection by clicking on the button **Test this connection**. A test issue will be published in the respective JIRA project. In case of a bad request we will show the response of your JIRA instance, which makes it easier for you to understand what went wrong.

![](<../../.gitbook/assets/iLert (61).png>)

In case your connection has been setup correctly you will see a successful message.

![](../../.gitbook/assets/ji14.png)

## FAQ <a href="#faq" id="faq"></a>

**Are updates to an alert published in the JIRA Ticket?**

Yes, the state of the ilert Alert is reflected in the title of the JIRA ticket, eg \[RESOLVED] Host compute.infra is DOWN.

**Can I choose which updates to publish to an alert in JIRA?**

Currently not. If you wish, we look forward to your feedback via chat or e-mail.

**I need to add more custom code to the template and the editor turns yellow**

Dont worry, you will still be able to save the connector, even if the hint is yellow or red, just click on the save button as soon as your template is ready.



## Related articles

{% content-ref url="../inbound-integrations/jira.md" %}
[jira.md](../inbound-integrations/jira.md)
{% endcontent-ref %}
