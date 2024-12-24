---
description: Create tickets in Autotask PSA based on alerts from ilert.
---

# Autotask Outbound Integration

## In Autotask: Create an API user <a href="#create-api-user" id="create-api-user"></a>

1\. Sign in to Autotask and then go to **Admin -> Resources (Users)**

![](<../.gitbook/assets/autotask1 (1) (2).png>)

2\. Click the **New** button and then navigate to **New API User**

![](<../.gitbook/assets/autotask2 (1).png>)

3\. In the **First Name** section, enter a first name eg. ilert

4\. In the **Last Name** section, enter a last name eg. API

5\. In the **Email** section, enter an email

6\. Click the **Generate key** button to generate a username and then the **Generate Secret** button to generate a password. You will need **Username** and **Secret** below when setting up the connector.

7\. In the **Integration Vendor** section, choose ilert or your custom internal integration

![](<../.gitbook/assets/autotask3 (2).png>)

## In ilert: Create an Autotask Connector and Link to alert source

1\. Click on the gear icon and then on **Connectors** button

![](<../.gitbook/assets/iLert (16).png>)

2\. Click on **Add Connector**

![](<../.gitbook/assets/iLert (17).png>)

3\. Select **Autotask** as **type** and fill in all fields. Enter a name and the username/password pair that you created in the last step.

![](<../.gitbook/assets/iLert (18).png>)

4\. Go to the alert sources tab and open the alert source whose alerts you want to publish in Autotask. Click on **Alert actions** and then on **Create alert action**.

![](<../.gitbook/assets/new_incident_action (3).png>)

5\. Select **Autotask** as the **type**, select the connector created in step 3, fill in all fields. In the **Label** field, specify the alert action name.

![](<../.gitbook/assets/iLert (58).png>)

6\. Finished! You can now test the alert action by clicking on the button **Test this connection**. Then a test ticket will be created in Autotask.

![](<../.gitbook/assets/iLert (59).png>)

## FAQ <a href="#faq" id="faq"></a>

**Are updates to an alert published in Autotask?**

Yes.

**Can Autotask alert sources use Autotask connections?**

No, please create a different alert source or create a bi-directional Autotask alert source.

**My API user gets blocked**

Please ensure that you have correctly chosen "iLert " as Integration Vendor in Autotask when setting up your API user.

## **Related articles**

{% content-ref url="../inbound-integrations-1/autotask.md" %}
[autotask.md](../inbound-integrations-1/autotask.md)
{% endcontent-ref %}
