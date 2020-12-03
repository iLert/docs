---
description: >-
  The iLert Autotask Inbound Integration helps you to easily connect iLert with
  Autotask.
---

# Autotask Inbound Integration

With the iLert Autotask inbound integration, you can create incidents in iLert based on tickets from Autotask.

## In Autotask: Create an API user <a id="create-api-user"></a>

1. Sign in to Autotask and then go to **Admin -&gt; Resources \(Users\)**

![](../../.gitbook/assets/autotask1.png)

1. Click the **New** button and then navigate to **New API User**

![](../../.gitbook/assets/autotask2.png)

1. In the **First Name** section, enter a first name eg. iLert
2. In the **Last Name** section, enter a last name eg. API
3. In the **Email** section, enter an email
4. Click the **Generate key** button to generate a username and then the **Generate Secret** button to generate a password. You will need **Username** and **Secret** below when setting up the alert source.
5. In the **Integration Vendor** section, choose iLert or your custom internal integration

![](../../.gitbook/assets/autotask3%20%283%29.png)

## In iLert: Create an Autotask alert source <a id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click on "Create new alert source"

![](../../.gitbook/assets/autotask4%20%281%29.png)

1. In the **Name** section, enter a name eg. iLert
2. In the **Integration Type** section, choose "Autotask"
3. In the **Autotask Settings -&gt; Username** section, paste the API user username generated above
4. In the **Autotask Settings -&gt; Secret** section, paste the API user secret generated above
5. select your desired escalation policy and click the **Save** button

![](../../.gitbook/assets/ilert%20%281%29.png)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the extension callout in Autotask.

![](../../.gitbook/assets/autotask6.png)

## In Autotask: Create Extension Callout <a id="create-extension-callout"></a>

1. Go to Autotask and then to **Admin -&gt; Extensions & Integrations**

![](../../.gitbook/assets/autotask7.png)

1. Click the **Other Extensions & Tools** panel and then click on the **Extension Callout \(Tickets\)** link

![](../../.gitbook/assets/autotask8.png)

1. Click on **New Extension Callout** 

![](../../.gitbook/assets/autotask9.png)

1. In the **Name** section, enter a name eg. iLert
2. In the **URL** section, paste the **Webhook URL** that you generated in iLert
3. Ensure that **Active** is selected and click the **Save & Close** button

![](../../.gitbook/assets/autotask10.png)

## In Autotask: Create Workflow Rule <a id="create-workflow-rule"></a>

1. Go to Autotask and then to **Admin -&gt; Workflow Rules**

![](../../.gitbook/assets/autotask11.png)

1. Click the **New** button

![](../../.gitbook/assets/autotask12.png)

1. In the **General -&gt; Workflow Rule Name** section, enter a name eg. iLert
2. Ensure that **Active** is selected
3. In the **Events -&gt; CREATED/EDITED** section, activate the **Created by** and the **Edited by** fields and choose **Anyone**

![](../../.gitbook/assets/autotask13.png)

1. Scroll down to the **Actions** panel and in the **Then Execute Extension Callout** section choose the **iLert Callout** that you created above
2. Click on the **Save & Close** button

![](../../.gitbook/assets/autotask14%20%281%29.png)

## Autotask Incident Lifecycle

<table>
  <thead>
    <tr>
      <th style="text-align:left">When I create an Autotask ticket with status...</th>
      <th style="text-align:left">...then an iLert Incident...</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>New</b>
      </td>
      <td style="text-align:left">is created</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>In Progress</b>
      </td>
      <td style="text-align:left">is created</td>
    </tr>
    <tr>
      <td style="text-align:left">Any other</td>
      <td style="text-align:left">is created</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Complete</b> or <b>Denied</b>
      </td>
      <td style="text-align:left">
        <p>will not be created and a</p>
        <p>400 (bad request) error occurs</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>Waiting Customer</b> or <b>Waiting Materials </b>or<b> </b>
        </p>
        <p><b>Scheduled </b>or<b> Escalate</b> or</p>
        <p><b>Waiting Vendor</b> or <b>Waiting Approval</b> or</p>
        <p><b>Waiting Dispatch</b> or <b>Approved</b>
        </p>
      </td>
      <td style="text-align:left">
        <p>will not be created and a</p>
        <p>400 (bad request) error occurs</p>
      </td>
    </tr>
  </tbody>
</table>



<table>
  <thead>
    <tr>
      <th style="text-align:left">When I update an Autotask ticket with status...</th>
      <th style="text-align:left">...and the<b> </b>iLert incident...</th>
      <th style="text-align:left">...then the/an iLert Incident...</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>New</b>
      </td>
      <td style="text-align:left">does not exist</td>
      <td style="text-align:left">is created</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Complete</b> or <b>Denied</b>
      </td>
      <td style="text-align:left">does not exist</td>
      <td style="text-align:left">
        <p>will not be created and a</p>
        <p>400 (bad request) error occurs</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>Waiting Customer</b> or <b>Waiting Materials </b>or<b> </b>
        </p>
        <p><b>Scheduled </b>or<b> Escalate</b> or</p>
        <p><b>Waiting Vendor</b> or <b>Waiting Approval</b> or</p>
        <p><b>Waiting Dispatch</b> or <b>Approved</b>
        </p>
      </td>
      <td style="text-align:left">does not exist</td>
      <td style="text-align:left">
        <p>will not be created and a</p>
        <p>400 (bad request) error occurs</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>In Progress</b>
      </td>
      <td style="text-align:left">does not exist</td>
      <td style="text-align:left">is created</td>
    </tr>
    <tr>
      <td style="text-align:left">Any other</td>
      <td style="text-align:left">does not exist</td>
      <td style="text-align:left">is created</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>New</b>
      </td>
      <td style="text-align:left">exists</td>
      <td style="text-align:left">doesn&apos;t change</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Complete</b> or <b>Denied</b>
      </td>
      <td style="text-align:left">exists</td>
      <td style="text-align:left">change status to <b>Resolved</b> if not already resolved</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p><b>Waiting Customer</b> or <b>In Progress</b> or</p>
        <p><b>Waiting Materials </b>or<b> Scheduled </b>or<b> </b>
        </p>
        <p><b>Escalate</b> or <b>Waiting Vendor</b> or</p>
        <p><b>Waiting Approval</b> or</p>
        <p><b>Waiting Dispatch</b> or <b>Approved</b>
        </p>
      </td>
      <td style="text-align:left">exists</td>
      <td style="text-align:left">change status to <b>Accepted</b> if not already accepted</td>
    </tr>
    <tr>
      <td style="text-align:left">Any other</td>
      <td style="text-align:left">exists</td>
      <td style="text-align:left">doesn&apos;t change</td>
    </tr>
  </tbody>
</table>

## FAQ <a id="faq"></a>

**Will incidents in iLert be resolved automatically?**

Yes, as soon as an Autotask Ticket is completed, the incident in iLert will be resolved automatically.

**Can I connect Autotask with multiple alert sources from iLert?**

Yes, simply create more Extension Callouts in Autotask.

**Can I customize the incident messages?**

No.

