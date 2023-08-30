---
description: Create alerts in ilert from tickets in Autotask PSA.
---

# Autotask Inbound Integration

With the ilert Autotask inbound integration, you can create alerts in ilert based on tickets from Autotask.

## In Autotask: Create an API user <a href="#create-api-user" id="create-api-user"></a>

1. Sign in to Autotask and then go to **Admin -> Resources (Users)**

![](<../../.gitbook/assets/autotask1 (1) (2).png>)

1. Click the **New** button and then navigate to **New API User**

![](<../../.gitbook/assets/autotask2 (1).png>)

1. In the **First Name** section, enter a first name eg. ilert
2. In the **Last Name** section, enter a last name eg. API
3. In the **Email** section, enter an email
4. Click the **Generate key** button to generate a username and then the **Generate Secret** button to generate a password. You will need **Username** and **Secret** below when setting up the alert source.
5. In the **Integration Vendor** section, choose ilert or your custom internal integration

![](<../../.gitbook/assets/autotask3 (3).png>)

## In ilert: Create an Autotask alert source <a href="#create-alert-source" id="create-alert-source"></a>

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FjX0cS4q7woTXKajZmc1W%2FScreenshot%202023-08-28%20at%2010.21.10.png?alt=media&#x26;token=8ef3666b-84eb-4b51-abee-f07303313941" alt=""><figcaption></figcaption></figure>
2.  Search for **Autotask** in the search field, click on the Autotask tile and click on **Next**.

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FlXzQlJpaTFSR49AZk0xA%2FScreenshot%202023-08-28%20at%2010.24.23.png?alt=media&#x26;token=cffeacb4-57b9-47d4-827d-b0f6b1afd914" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FNnuZqONaIhbOf6fn4OkZ%2FScreenshot%202023-08-28%20at%2011.37.47.png?alt=media&#x26;token=8a74f7b5-5bd2-4eea-97fa-1c1dbb041333" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](https://docs.ilert.com/alerting/alert-sources#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FueugN4JgHn1c90ggFA6u%2FScreenshot%202023-08-28%20at%2011.38.24.png?alt=media&#x26;token=b8009daf-3ca8-4264-a6fa-e42ef7333205" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.​

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2Fi3TIOBvNYBQfDtNpmm0A%2FScreenshot%202023-08-28%20at%2011.47.34.png?alt=media&#x26;token=6cae965a-e448-4443-8c20-37cf501c43b2" alt=""><figcaption></figcaption></figure>

## In Autotask: Create Extension Callout <a href="#create-extension-callout" id="create-extension-callout"></a>

1. Go to Autotask and then to **Admin -> Extensions & Integrations**

![](<../../.gitbook/assets/autotask7 (2).png>)

2. Click the **Other Extensions & Tools** panel and then click on the **Extension Callout (Tickets)** link

![](<../../.gitbook/assets/autotask8 (2).png>)

3. Click on **New Extension Callout**

![](<../../.gitbook/assets/autotask9 (1).png>)

4. In the **Name** section, enter a name eg. ilert
5. In the **URL** section, paste the **Webhook URL** that you generated in ilert
6. Ensure that **Active** is selected and click the **Save & Close** button

![](<../../.gitbook/assets/autotask10 (2).png>)

## In Autotask: Create Workflow Rule <a href="#create-workflow-rule" id="create-workflow-rule"></a>

1. Go to Autotask and then to **Admin -> Workflow Rules**

![](<../../.gitbook/assets/autotask11 (2).png>)

2. Click the **New** button

![](<../../.gitbook/assets/autotask12 (1).png>)

3. In the **General -> Workflow Rule Name** section, enter a name eg. ilert
4. Ensure that **Active** is selected
5. In the **Events -> CREATED/EDITED** section, activate the **Created by** and the **Edited by** fields and choose **Anyone**

![](<../../.gitbook/assets/autotask13 (1).png>)

6. Scroll down to the **Actions** panel and in the **Then Execute Extension Callout** section choose the **iLert Callout** that you created above
7. Click on the **Save & Close** button

![](<../../.gitbook/assets/autotask14 (1).png>)

## Autotask Alert Lifecycle

| **When Autotask creates a ticket with status ...**                                                                                                                                                                                                                                                                                                        | **... then an ilert alert ...**                                       |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| <p><code>New</code> or<br><code>In Progress</code></p>                                                                                                                                                                                                                                                                                                    | is created                                                            |
| <p><code>Complete</code> or</p><p><code>Denied</code> or</p><p><code>Waiting Customer</code> or</p><p><code>Waiting Materials</code> or</p><p><code>Scheduled</code> or</p><p><code>Escalate</code> or</p><p><code>Waiting Vendor</code> or</p><p><code>Waiting Approva</code>l or</p><p><code>Waiting Dispatch</code> or</p><p><code>Approved</code></p> | <p>will not be created and a</p><p>400 (bad request) error occurs</p> |
| any other status                                                                                                                                                                                                                                                                                                                                          | is created                                                            |

| **When Autotask updates a ticket with status ...**                                                                                                                                                                                                                                                                                                        | .**.. and the ilert alert ...** | **... then the/an ilert alert ...**                                   |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------- | --------------------------------------------------------------------- |
| <p><code>New</code> or<br><code>In Progress</code></p>                                                                                                                                                                                                                                                                                                    | does not exist                  | is created                                                            |
| <p><code>Complete</code> or</p><p><code>Denied</code> or</p><p><code>Waiting Customer</code> or</p><p><code>Waiting Materials</code> or</p><p><code>Scheduled</code> or</p><p><code>Escalate</code> or</p><p><code>Waiting Vendor</code> or</p><p><code>Waiting Approva</code>l or</p><p><code>Waiting Dispatch</code> or</p><p><code>Approved</code></p> | does not exist                  | <p>will not be created and a</p><p>400 (bad request) error occurs</p> |
| any other                                                                                                                                                                                                                                                                                                                                                 | does not exist                  | is created                                                            |
| `New`                                                                                                                                                                                                                                                                                                                                                     | exists                          | doesn't change                                                        |
| <p><code>Complete</code> or</p><p><code>Denied</code></p>                                                                                                                                                                                                                                                                                                 | exists                          | change status to **Resolved** if not already resolved                 |
| <p><code>Waiting Customer</code> or</p><p><code>In Progress</code> or</p><p><code>Waiting Materials</code> or</p><p><code>Scheduled</code> or</p><p><code>Escalate</code> or</p><p><code>Waiting Vendor</code> or</p><p><code>Waiting Approval</code> or</p><p><code>Waiting Dispatch</code> or</p><p><code>Approved</code></p>                           | exists                          | change status to **Accepted** if not already accepted                 |
| any other status                                                                                                                                                                                                                                                                                                                                          | exists                          | doesn't change                                                        |

## Mapping Autotask ticket priority to ilert alert priority

| Autotask ticket priority                      | ilert alert priority |
| --------------------------------------------- | -------------------- |
| 1 - Low                                       | Low                  |
| <p>2 - High<br>3 - Medium<br>4 - Critical</p> | High                 |

## Bidirectional alert synchronisation

When providing credentials you may choose to activate bidirectional mode on the Autotask ticket source. This will cause your alert source to be automatically linked with an outbound connector and alert action. This way status changes to ilert alerts will synchronize to Autotask ticket.

<figure><img src="../../.gitbook/assets/ExampleAutotask.png" alt=""><figcaption></figcaption></figure>

When saving the Autotask alert source with bidirectional setting enabled, it will automatically create an outbound connector for you and take you to the creation page of the necessary alert action, please make sure to continue with the setup of the action to finish your bidirectional alert source setup.

## Setting up multi workflows in Autotask

To use Autotask workflows combined with holiday calendars to manage on-call availability, you will need to set up following 2 workflows:\


1. Go to Autotask and then to **Admin -> Workflow Rules**
2. In the **General -> Workflow Rule Name** section, enter a name eg. ilert (business hours)
3. Ensure that **Active** is selected
4. In the **Events -> CREATED/EDITED** section, activate the **Created by** and the **Edited by** fields and choose **Anyone**

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-17 at 22.29.39.png" alt=""><figcaption></figcaption></figure>

6. In the **Conditions** section, select **Status Equal to New**.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-17 at 22.33.38.png" alt=""><figcaption></figcaption></figure>

7. Scroll down to the **Actions** panel and in the **Then Execute Extension Callout** section choose the **iLert Callout** that you created above
8. Click on the **Save & New** button

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-17 at 22.34.04.png" alt=""><figcaption></figcaption></figure>

9. Enter a name eg. ilert (no business hours)
10. Ensure that **Active** is selected
11. In the **Events -> CREATED/EDITED** section, activate the **Created by** and the **Edited by** fields and choose **Anyone**

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-17 at 22.34.50.png" alt=""><figcaption></figcaption></figure>

12. In the **Conditions** section, select **Status Not equal to New**.
13. Tick the **Time Sensitive** checkbox and select **Outside Business Hours of**.

<figure><img src="../../.gitbook/assets/Screenshot 2023-04-17 at 22.36.21.png" alt=""><figcaption></figcaption></figure>

14. Scroll down to the **Actions** panel and in the **Then Execute Extension Callout** section choose the **iLert Callout** that you created above
15. Click on the **Save & New** button

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as an Autotask Ticket is completed, the alert in ilert will be resolved automatically.

**Can I connect Autotask with multiple alert sources from ilert?**

Yes, simply create more Extension Callouts in Autotask.

**Can I customize the alert messages?**

No.
