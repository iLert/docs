---
description: >-
  With the Zammad Outbound Integration you can create Zammad Tickets right from
  iLert incidents.
---

# Zammad Outbound Integration

{% hint style="warning" %}
To set up this integration, you must have admin rights in iLert.
{% endhint %}

## In Zammad <a id="in-topdesk"></a>

### Create an API key <a id="create-api-user"></a>

1. Optional: create a dedicated iLert user in Zammad. This has the advantage that you can distinguish the Zammad tickets created by iLert.

2. Go to **Profile**, then to **Token Access** and click on **Create**

![](../../.gitbook/assets/screenshot_07_02_21__13_32.png)

3. In the **Name** section, enter a name eg. iLert

![](../../.gitbook/assets/screenshot_07_02_21__13_33.png)

4. In the **Ticket** section,  choose **Agent**

![](../../.gitbook/assets/screenshot_07_02_21__13_34.png)

5. Click on **Create**

9. The modal window will open, copy the generated access token

![](../../.gitbook/assets/screenshot_07_02_21__13_36.png)

## In iLert <a id="in-ilert"></a>

### Create a Zammad Connector and Link to the alert source <a id="create-alarm-source"></a>

1. Click on the gear icon and then on the **Connectors** button

![](../../.gitbook/assets/tpdko7.png)

2. Click on **Add Connector**

![](../../.gitbook/assets/tpdko8.png)

3. Select **Zammad** as **type** and fill in all fields. Enter a name, the URL of your Zammad server and the access token that you have created in the previous step.

![](../../.gitbook/assets/screenshot_07_02_21__13_39.png)

4. Go to the alert sources tab and open the alert source whose incidents you want to publish in Zammad. Click on **Connections** and then on **Add New Connection**.

![](../../.gitbook/assets/tpdko10.png)

5. Select **Zammad** as the **type**; ****futhermore ****select the connector created in step 3, fill in all fields.  
In the **Email** field enter the existing customer email of Zammad.

![](../../.gitbook/assets/screenshot_07_02_21__13_41.png)

6. Finished! You can now test the connection by clicking on the button **Test this connection**.  
A test ticket will be created in Zammad.

![](../../.gitbook/assets/screenshot_07_02_21__13_43.png)

## FAQ <a id="faq"></a>

**Are updates to an incident added to the Zammad Ticket?**

Yes, the state of the iLert Incident is reflected in the brief description of the Zammad ticket eg. _\[RESOLVED\] Host compute.infra is DOWN._

**Can I choose which updates are to be published to a Zammad Ticket?**

Currently not. If you wish to, we look forward to your feedback via chat or e-mail

