---
description: Create StatusPage inicdents from ilert alerts.
---

# StatusPage Integration

## In StatusPage <a href="#create-alarm-source" id="create-alarm-source"></a>

### Create an API key

1. Go to your StatusPage, click on the **Profile** tile and then on the **API info** button

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_17\_38.png)

1. On the next page click on the **Create key**

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_17\_40.png)

1. On the modal window, name the key e.g. ilert and click on the **Confirm** button

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_17\_42.png)

1. On the next page, a API key is generated. You will need this key and the page id below when setting up the connector in ilert.

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_17\_52.png)

## In ilert <a href="#create-alarm-source" id="create-alarm-source"></a>

### Create the Statuspage Connector and link it to the alert source

1. **\*\*Click the gear icon and then click on the** Connectors\*\* link

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_15\_46.png)

1. Click the **Add Connector** button

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_15\_48.png)

1. On the next page, choose **StatusPage** as type, name the connector, paste the **API Key** that you generated in StatusPage and click on the **Save** button.

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_17\_49.png)

1. Go to the alert sources tab and open the alert source whose alerts you want to create StatusPage Incidents. Click on the **Alert actions** tab and then on the **Add new alert action** button

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_16\_04.png)

1. On the next page choose **StatusPage** as the type, choose the connector created in step 3, name it, choose **Trigger mode,** paste the **Page Id** and click on the **Save** button.

![](../.gitbook/assets/Screenshot\_16\_03\_21\_\_17\_51.png)

1. Finished! Now an StatusPage alert will be created for each alert in automatic trigger mode or via manual alert action.

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
