---
description: >-
  The iLert Autotask Outbound Integration helps you to easily connect Autotask
  with iLert.
---

# Autotask Outbound Integration

With the iLert Autotask outbound integration, you can create tickets in Autotask based on incidents from iLert.

## In Autotask <a id="create-api-user"></a>

### Create an API user

1. Sign in to Autotask and then go to **Admin -&gt; Resources \(Users\)**

![](../../.gitbook/assets/autotask1.png)

1. Click the **New** button and then navigate to **New API User**

![](../../.gitbook/assets/autotask2.png)

1. In the **First Name** section, enter a first name eg. iLert
2. In the **Last Name** section, enter a last name eg. API
3. In the **Email** section, enter an email
4. Click the **Generate key** button to generate a username and then the **Generate Secret** button to generate a password. You will need **Username** and **Secret** below when setting up the connector.
5. In the **Integration Vendor** section, choose iLert or your custom internal integration

![](../../.gitbook/assets/autotask3%20%282%29.png)

## In iLert

### Create a Autotask Connector and Link to alert source

1. Click on the gear icon and then on **Connectors** button

![](../../.gitbook/assets/ilert%20%2819%29.png)

2. Click on **Add Connector**

![](../../.gitbook/assets/ilert%20%2817%29.png)

3. Select **Autotask** as **type** and fill in all fields. Enter a name and the username/password pair that you created in the last step.

![](../../.gitbook/assets/ilert%20%2821%29.png)

4. Go to the alert sources tab and open the alert source whose incidents you want to publish in Autotask. Click on **Connections** and then on **Create Connection**.

![](../../.gitbook/assets/ilert%20%2820%29.png)

5. Select **Autotask** as the **type**, select the connector created in step 3, fill in all fields. In the **Label** field, specify the connector name.

![](../../.gitbook/assets/ilert%20%2818%29.png)

6. Finished! You can now test the connection by clicking on the button **Test this connection**. Then a test ticket will be created in Autotask.

![](../../.gitbook/assets/ilert%20%2816%29.png)

## FAQ <a id="faq"></a>

**Are updates to an incident published in Autotask?**

Yes.

**Can Autotask alert sources use Autotask connections?**

No, please create a different alert source.

\*\*\*\*

