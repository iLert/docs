---
description: Create alerts in iLert from tickets in Autotask PSA.
---

# Autotask Inbound Integration

With the iLert Autotask inbound integration, you can create alerts in iLert based on tickets from Autotask.

## In Autotask: Create an API user <a href="#create-api-user" id="create-api-user"></a>

1. Sign in to Autotask and then go to **Admin -> Resources (Users)**

![](<../../.gitbook/assets/autotask1 (1).png>)

1. Click the **New** button and then navigate to **New API User**

![](<../../.gitbook/assets/autotask2 (1).png>)

1. In the **First Name** section, enter a first name eg. iLert
2. In the **Last Name** section, enter a last name eg. API
3. In the **Email** section, enter an email
4. Click the **Generate key** button to generate a username and then the **Generate Secret** button to generate a password. You will need **Username** and **Secret** below when setting up the alert source.
5. In the **Integration Vendor** section, choose iLert or your custom internal integration

![](<../../.gitbook/assets/autotask3 (3).png>)

## In iLert: Create an Autotask alert source <a href="#create-alert-source" id="create-alert-source"></a>

1. Go to the "Alert sources" tab and click on "Create new alert source"

![](<../../.gitbook/assets/autotask4 (1).png>)

1. In the **Name** section, enter a name eg. iLert
2. In the **Integration Type** section, choose "Autotask"
3. In the **Autotask Settings -> Username** section, paste the API user username generated above
4. In the **Autotask Settings -> Secret** section, paste the API user secret generated above
5. select your desired escalation policy and click the **Save** button

![](<../../.gitbook/assets/iLert (2).png>)

1. On the next page, a Webhook URL is generated. You will need this URL below when setting up the extension callout in Autotask.

![](<../../.gitbook/assets/autotask6 (1).png>)

## In Autotask: Create Extension Callout <a href="#create-extension-callout" id="create-extension-callout"></a>

1. Go to Autotask and then to **Admin -> Extensions & Integrations**

![](<../../.gitbook/assets/autotask7 (2).png>)

1. Click the **Other Extensions & Tools** panel and then click on the **Extension Callout (Tickets)** link

![](<../../.gitbook/assets/autotask8 (2).png>)

1. Click on **New Extension Callout**&#x20;

![](<../../.gitbook/assets/autotask9 (1).png>)

1. In the **Name** section, enter a name eg. iLert
2. In the **URL** section, paste the **Webhook URL** that you generated in iLert
3. Ensure that **Active** is selected and click the **Save & Close** button

![](<../../.gitbook/assets/autotask10 (2).png>)

## In Autotask: Create Workflow Rule <a href="#create-workflow-rule" id="create-workflow-rule"></a>

1. Go to Autotask and then to **Admin -> Workflow Rules**

![](<../../.gitbook/assets/autotask11 (2).png>)

1. Click the **New** button

![](<../../.gitbook/assets/autotask12 (1).png>)

1. In the **General -> Workflow Rule Name** section, enter a name eg. iLert
2. Ensure that **Active** is selected
3. In the **Events -> CREATED/EDITED** section, activate the **Created by** and the **Edited by** fields and choose **Anyone**

![](<../../.gitbook/assets/autotask13 (1).png>)

1. Scroll down to the **Actions** panel and in the **Then Execute Extension Callout** section choose the **iLert Callout** that you created above
2. Click on the **Save & Close** button

![](<../../.gitbook/assets/autotask14 (1).png>)

## Autotask Alert Lifecycle

| **When Autotask creates a ticket with status ...**                                                                                                                                                                                                                                                                                                             | **... then an iLert alert ...**                                       |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| <p><code>New</code> or<br><code>In Progress</code></p>                                                                                                                                                                                                                                                                                                         | is created                                                            |
| <p><code>Complete</code> or </p><p><code>Denied</code> or</p><p><code>Waiting Customer</code> or </p><p><code>Waiting Materials</code> or</p><p><code>Scheduled</code> or </p><p><code>Escalate</code> or</p><p><code>Waiting Vendor</code> or </p><p><code>Waiting Approva</code>l or</p><p><code>Waiting Dispatch</code> or </p><p><code>Approved</code></p> | <p>will not be created and a</p><p>400 (bad request) error occurs</p> |
| any other status                                                                                                                                                                                                                                                                                                                                               | is created                                                            |

| **When Autotask updates a ticket with status ...**                                                                                                                                                                                                                                                                                                             | .**.. and the iLert alert ...** | **... then the/an iLert alert ...**                                   |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------- | --------------------------------------------------------------------- |
| <p><code>New</code> or<br><code>In Progress</code></p>                                                                                                                                                                                                                                                                                                         | does not exist                  | is created                                                            |
| <p><code>Complete</code> or </p><p><code>Denied</code> or</p><p><code>Waiting Customer</code> or </p><p><code>Waiting Materials</code> or</p><p><code>Scheduled</code> or </p><p><code>Escalate</code> or</p><p><code>Waiting Vendor</code> or </p><p><code>Waiting Approva</code>l or</p><p><code>Waiting Dispatch</code> or </p><p><code>Approved</code></p> | does not exist                  | <p>will not be created and a</p><p>400 (bad request) error occurs</p> |
| any other                                                                                                                                                                                                                                                                                                                                                      | does not exist                  | is created                                                            |
| `New`                                                                                                                                                                                                                                                                                                                                                          | exists                          | doesn't change                                                        |
| <p><code>Complete</code> or </p><p><code>Denied</code></p>                                                                                                                                                                                                                                                                                                     | exists                          | change status to **Resolved** if not already resolved                 |
| <p><code>Waiting Customer</code> or </p><p><code>In Progress</code> or</p><p><code>Waiting Materials</code> or </p><p><code>Scheduled</code> or</p><p><code>Escalate</code> or </p><p><code>Waiting Vendor</code> or</p><p><code>Waiting Approval</code> or</p><p><code>Waiting Dispatch</code> or </p><p><code>Approved</code></p>                            | exists                          | change status to **Accepted** if not already accepted                 |
| any other status                                                                                                                                                                                                                                                                                                                                               | exists                          | doesn't change                                                        |

## Mapping Autotask ticket priority to iLert alert priority

| Autotask ticket priority                      | iLert alert priority  |
| --------------------------------------------- | --------------------- |
| 1 - Low                                       | Low                   |
| <p>2 - High<br>3 - Medium<br>4 - Critical</p> | High                  |

## Bidirectional alert synchronisation

When providing credentials you may choose to activate bidirectional mode on the Autotask ticket source. This will cause your alert source to be automatically linked with an outbound connector and alert action. This way status changes to iLert alerts will synchronize to Autotask ticket.

<figure><img src="../../.gitbook/assets/ExampleAutotask.png" alt=""><figcaption></figcaption></figure>

When saving the Autotask alert source with bidirectional setting enabled, it will automatically create an outbound connector for you and take you to the creation page of the necessary alert action, please make sure to continue with the setup of the action to finish your bidirectional alert source setup.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in iLert be resolved automatically?**

Yes, as soon as an Autotask Ticket is completed, the alert in iLert will be resolved automatically.

**Can I connect Autotask with multiple alert sources from iLert?**

Yes, simply create more Extension Callouts in Autotask.

**Can I customize the alert messages?**

No.
