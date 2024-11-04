# AWS Cloudtrail Integration

AWS CloudTrail is a service that records and monitors all actions taken within an AWS account, providing detailed logs of API calls and activity across resources. When connected to ilert, CloudTrail enhances incident response by triggering real-time alerts for critical changes or suspicious activity, such as unauthorized access attempts or modifications to security settings.

## How this integration works <a href="#create-alert-source" id="create-alert-source"></a>

AWS CloudTrail logs and monitors account activity across your AWS infrastructure. Activity logs are published to specific Amazon Simple Notification Service (SNS) topics; the events are sent to ilert.

### Architecture <a href="#create-alert-source-2" id="create-alert-source-2"></a>

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

## In ilert: Create an Amazon SNS alert source <a href="#create-alert-source-2" id="create-alert-source-2"></a>

1.  Go to **Alert sources** -> **Alert sources** and click on **Create new alert source**

    ![](https://docs.ilert.com/\~gitbook/image?url=https%3A%2F%2F3394882078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-M76ygPnS4HUcFSX8ulm%252Fuploads%252FjX0cS4q7woTXKajZmc1W%252FScreenshot%25202023-08-28%2520at%252010.21.10.png%3Falt%3Dmedia%26token%3D8ef3666b-84eb-4b51-abee-f07303313941\&width=768\&dpr=4\&quality=100\&sign=4247e46e\&sv=1)
2.  Search for **Amazon SNS** in the search field, click on the Amazon SNS tile, and click on **Next**.

    ![](https://docs.ilert.com/\~gitbook/image?url=https%3A%2F%2F3394882078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-M76ygPnS4HUcFSX8ulm%252Fuploads%252FlXzQlJpaTFSR49AZk0xA%252FScreenshot%25202023-08-28%2520at%252010.24.23.png%3Falt%3Dmedia%26token%3Dcffeacb4-57b9-47d4-827d-b0f6b1afd914\&width=768\&dpr=4\&quality=100\&sign=c064114f\&sv=1)
3. Give your alert source a name, optionally assign teams, and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    ![](https://docs.ilert.com/\~gitbook/image?url=https%3A%2F%2F3394882078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-M76ygPnS4HUcFSX8ulm%252Fuploads%252FNnuZqONaIhbOf6fn4OkZ%252FScreenshot%25202023-08-28%2520at%252011.37.47.png%3Falt%3Dmedia%26token%3D8a74f7b5-5bd2-4eea-97fa-1c1dbb041333\&width=768\&dpr=4\&quality=100\&sign=a01e4bae\&sv=1)
5.  Select your [Alert grouping](https://docs.ilert.com/\~/changes/vPSzQFfkdJCVWGT5AL1m/alerting/alert-sources#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.

    ![](https://docs.ilert.com/\~gitbook/image?url=https%3A%2F%2F3394882078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-M76ygPnS4HUcFSX8ulm%252Fuploads%252FueugN4JgHn1c90ggFA6u%252FScreenshot%25202023-08-28%2520at%252011.38.24.png%3Falt%3Dmedia%26token%3Db8009daf-3ca8-4264-a6fa-e42ef7333205\&width=768\&dpr=4\&quality=100\&sign=4f5486f8\&sv=1)
6. The next page shows additional settings, such as customer alert templates or notification priority. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated, which you will need later in this guide.

    ![](https://docs.ilert.com/\~gitbook/image?url=https%3A%2F%2F3394882078-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F-M76ygPnS4HUcFSX8ulm%252Fuploads%252Fq8AY87k6gfWEvNXuyKx5%252Fil-1.png%3Falt%3Dmedia%26token%3D2a93f17d-fb37-4a50-a9ac-acd877b06582\&width=768\&dpr=4\&quality=100\&sign=b65be3a5\&sv=1)

## In AWS Simple Notification Service(SNS): Create a new topic <a href="#create-topic" id="create-topic"></a>

1. On the sidebar, click on **Topics** **->** **Create topic**.&#x20;

<figure><img src="../.gitbook/assets/1.png" alt=""><figcaption></figcaption></figure>

2. Choose **Standard** and enter a topic **Name**.
3. Save the topic.

<figure><img src="../.gitbook/assets/1 (1).png" alt=""><figcaption></figcaption></figure>

4. Now click on **Create subscription**.

<figure><img src="../.gitbook/assets/2 (1).png" alt=""><figcaption></figcaption></figure>

5. Select 'HTTPS' as **Protocol** and enter the alert source URL previously generated in ilert into the **Endpoint** field.

<figure><img src="../.gitbook/assets/3 (1).png" alt=""><figcaption></figcaption></figure>

## In AWS Cloudtrail: Enable a SNS Notification <a href="#create-topic" id="create-topic"></a>

1. Choose a desired trail by clicking on the name.

<figure><img src="../.gitbook/assets/3 (2).png" alt=""><figcaption></figcaption></figure>

2. In the **General details** tab, click on **Edit**.

<figure><img src="../.gitbook/assets/4 (1).png" alt=""><figcaption></figcaption></figure>

3. Under **Additional settings**, enable **SNS notification delivery**.
4. Choose **Existing** and search for the newly created topic from before.

<figure><img src="../.gitbook/assets/6.png" alt=""><figcaption></figcaption></figure>

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

No, but you can use the **eventType** custom attribute to resolve an incident in specified **incidentKey**.
