---
description: Create StatusPage inicdents from ilert alerts.
---

# StatusPage Integration

## In StatusPage: Create an API key <a href="#create-alarm-source" id="create-alarm-source"></a>

1. Go to your StatusPage, click on the **Profile** tile and then on the **API info** button

![](../../.gitbook/assets/Screenshot_16_03_21__17_38.png)

2. On the next page click on the **Create key**

![](../../.gitbook/assets/Screenshot_16_03_21__17_40.png)

3. On the modal window, name the key e.g. ilert and click on the **Confirm** button

![](../../.gitbook/assets/Screenshot_16_03_21__17_42.png)

4. On the next page, a API key is generated. You will need this key and the page id below when setting up the connector in ilert.

![](../../.gitbook/assets/Screenshot_16_03_21__17_52.png)

## In ilert: Create the Statuspage Connector and link it to the alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1. **\*\*Click the gear icon and then click on the** Connectors\*\* link

![](../../.gitbook/assets/Screenshot_16_03_21__15_46.png)

2. Click the **Add Connector** button

![](../../.gitbook/assets/Screenshot_16_03_21__15_48.png)

3. On the next page, choose **StatusPage** as type, name the connector, paste the **API Key** that you generated in StatusPage and click on the **Save** button.

![](../../.gitbook/assets/Screenshot_16_03_21__17_49.png)

4. Go to the alert sources tab and open the alert source whose alerts you want to create StatusPage Incidents. Click on the **Alert actions** tab and then on the **Add new alert action** button

![](../../.gitbook/assets/Screenshot_16_03_21__16_04.png)

5. On the next page choose **StatusPage** as the type, choose the connector created in step 3, name it, choose **Trigger mode,** paste the **Page Id** and click on the **Save** button.

![](../../.gitbook/assets/Screenshot_16_03_21__17_51.png)

6. Finished! Now an StatusPage alert will be created for each alert in automatic trigger mode or via manual alert action.

## StatusPage Incident Lifecycle

| When an ilert alert ... event occurs                                                            | ...and the StatusPage alert... | ...then the/an StatusPage alert...       |
| ----------------------------------------------------------------------------------------------- | ------------------------------ | ---------------------------------------- |
| <p><strong>Created, re-assigned,</strong></p><p><strong>escalated, priority raised</strong></p> | does not exist                 | is created with status **investigating** |
| **Accepted**                                                                                    | does not exist                 | is created with status **identified**    |
| **Resolved**                                                                                    | does not exist                 | is created with status **resolved**      |
| **Comment added**                                                                               | does not exist                 | is created with status **identified**    |
| <p><strong>Re-assigned, escalated,</strong></p><p><strong>priority raised</strong></p>          | exists                         | change status to **investigating**       |
| **Accepted**                                                                                    | exists                         | change status to **identified**          |
| **Resolved**                                                                                    | exists                         | change status to **resolved**            |
| **Comment added**                                                                               | exists                         | add update with comment content          |

## FAQ <a href="#faq" id="faq"></a>

**Can I link multiple StatusPage Accounts to an ilert account?**

Yes.
