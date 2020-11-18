---
description: Create events in Datadog from iLert incidents.
---

# Datadog Outbound Integration

## In Datadog <a id="in-topdesk"></a>

### Create an API key <a id="create-api-user"></a>

1. Go to **Integrations**, then click on **APIs**

![](../../.gitbook/assets/datadog_1.png)

2. In the **New API key** section, enter a name eg. iLert and click on **Create API Key** button

![](../../.gitbook/assets/datadog_2.png)

3. Write down your API key. You will need it later in iLert.

## In iLert <a id="in-ilert"></a>

### Create a Datadog Connector and Link to alert source <a id="create-alarm-source"></a>

1. Click on the gear icon and then on **Connectors** button

![](../../.gitbook/assets/tpdko7.png)

2. Click on **Add Connector**

![](../../.gitbook/assets/tpdko8.png)

3. Select **Datadog** as **type** and fill in all fields. Enter a name and the API key that you created [in the last step]().

![](../../.gitbook/assets/datadog_il1.png)

4. Go to the alert sources tab and open the alert source whose incidents you want to publish in Datadog. Click on **Connections** and then on **Add New Connection**.

![](../../.gitbook/assets/tpdko10.png)

5. Select **Datadog** as the **type**, select the connector created in step 3, fill in all fields. In the **Label** field, specify the connector name.

![](../../.gitbook/assets/datadog_il4.png)

6. Finished! You can now test the connection by clicking on the button **Test this connection**. Then a test ticket will be published in Datadog.

![](../../.gitbook/assets/datadog_il5.png)

## FAQ <a id="faq"></a>

**Are updates to an incident published in the Datadog?**

Yes, the state of the iLert Incident is reflected in the Datadog events.

**Can I choose which updates to publish to an incident in Datadog?**

Currently not. If you wish, we look forward to your feedback via chat or e-mail.

