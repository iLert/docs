---
description: >-
  The iLert Sysdig Outbound Integration helps you to easily connect Sysdig with
  iLert.
---

# Sysdig Outbound Integration

## In Sysdig <a id="in-topdesk"></a>

### Copy API token <a id="create-api-user"></a>

2. Go to **Settings**, then to **User Profile.** Write down your API Token. You will need it later in iLert.

![](../../.gitbook/assets/profile_-_settings_-_sysdig.png)

## In iLert <a id="in-ilert"></a>

### Create a Sysdig Connector and Link to alert source <a id="create-alarm-source"></a>

1. Click on the gear icon and then on **Connectors** button

![](../../.gitbook/assets/go_to_connectors%20%285%29.png)

2. Click on **Add Connector**

![](../../.gitbook/assets/create_connector_button%20%283%29.png)

3. Select **Sysdig** as **type** and fill in all fields. Enter a name, the API Token that you copied in the last step.

![](../../.gitbook/assets/ilert%20%283%29.png)

4. Go to the alert sources tab and open the alert source whose alerts you want to publish in Sysdig. Click on **Alert actions** and then on **Create alert action**.

![](../../.gitbook/assets/new_incident_action%20%288%29.png)

5. Select **Sysdig** as the **type**, select the connector created in step 3, fill in all fields. In the **Label** field, specify the alert action name.

![](../../.gitbook/assets/ilert%20%2878%29.png)

6. Optional: You can define tags and event filters. More information aber it you can find here: [https://docs.sysdig.com/en/events.html](https://docs.sysdig.com/en/events.html)

7. Finished! You can now test the connection by clicking on the button **Test this connection**. Then a test event will be created in Sysdig.

![](../../.gitbook/assets/ilert%20%2871%29.png)

## FAQ <a id="faq"></a>

**Are updates for an alert adapted in the corresponding Sysdig Event?**

Yes, the state of the iLert Alert is reflected in the brief description of the Sysdig event, eg \[RESOLVED\] Host compute.infra is DOWN.

