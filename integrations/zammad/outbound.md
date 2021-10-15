---
description: >-
  With the Zammad Outbound Integration you can create Zammad Tickets right from
  iLert alerts.
---

# Zammad Outbound Integration

{% hint style="warning" %}
To set up this integration, you must have admin rights in iLert.
{% endhint %}

## In Zammad <a href="in-topdesk" id="in-topdesk"></a>

### Create an API key <a href="create-api-user" id="create-api-user"></a>

1. Optional: create a dedicated iLert user in Zammad. This has the advantage that you can distinguish the Zammad tickets created by iLert.
2. Go to **Profile**, then to **Token Access** and click on **Create**

![](../../.gitbook/assets/Screenshot\_07\_02\_21\__13\_32.png)

1. In the **Name** section, enter a name eg. iLert

![](../../.gitbook/assets/Screenshot\_07\_02\_21\__13\_33.png)

1. In the **Ticket** section,  choose **Agent**

![](../../.gitbook/assets/Screenshot\_07\_02\_21\__13\_34.png)

1. Click on **Create**

{% hint style="warning" %}
An agent token has a group scope

An agent token has a group scope so if you want to use a group that the current user is not a member of, you need to create a token with the admin scope for all groups.
{% endhint %}

1. The modal window will open, copy the generated access token

![](../../.gitbook/assets/Screenshot\_07\_02\_21\__13\_36.png)

## In iLert <a href="in-ilert" id="in-ilert"></a>

### Create a Zammad Connector and Link to the alert source <a href="create-alarm-source" id="create-alarm-source"></a>

1. Click on the gear icon and then on the **Connectors** button

![](<../../.gitbook/assets/go_to_connectors (4).png>)

1. Click on **Add Connector**

![](<../../.gitbook/assets/create_connector_button (2).png>)

1. Select **Zammad** as **type** and fill in all fields. Enter a name, the URL of your Zammad server and the access token that you have created in the previous step.

![](../../.gitbook/assets/Screenshot\_07\_02\_21\__13\_39.png)

1. Go to the alert sources tab and open the alert source whose alerts you want to publish in Zammad. Click on **Alert actions** and then on **Create alert action**.

![](<../../.gitbook/assets/new_incident_action (12) (9).png>)

1.  Select **Zammad** as the **type**; **futhermore **select the connector created in step 3, fill in all fields.  

    In the **Email** field enter the existing customer email of Zammad.

![](<../../.gitbook/assets/iLert (74).png>)

1.  Finished! You can now test the connection by clicking on the button **Test this connection**.  

    A test ticket will be created in Zammad.

![](<../../.gitbook/assets/iLert (75).png>)

## FAQ <a href="faq" id="faq"></a>

**Are updates to an alert added to the Zammad Ticket?**

Yes, the state of the iLert Alert is reflected in the brief description of the Zammad ticket eg. _\[RESOLVED] Host compute.infra is DOWN._

**Can I choose which updates are to be published to a Zammad Ticket?**

Currently not. If you wish to, we look forward to your feedback via chat or e-mail

**Can I use custom group for the Zammad tickets?**

Yes, you need to create an agent token and include the user in the group or create an admin token with the group scope.

**Can I use multiple Zammad groups?**

Yes, just create an alert action for each Zammad group.
