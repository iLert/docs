---
description: >-
  API Fortress offers continuous API testing and monitoring that unifies
  functional, integration, and load testing across internal, partner, and third
  party APIs.
---

# API Fortress Integration

## In ilert: Create an API Fortress alert source

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FjX0cS4q7woTXKajZmc1W%2FScreenshot%202023-08-28%20at%2010.21.10.png?alt=media&#x26;token=8ef3666b-84eb-4b51-abee-f07303313941" alt=""><figcaption></figcaption></figure>
2.  Search for **API Fortress** in the search field, click on the API Fortress tile and click on **Next**.

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FlXzQlJpaTFSR49AZk0xA%2FScreenshot%202023-08-28%20at%2010.24.23.png?alt=media&#x26;token=cffeacb4-57b9-47d4-827d-b0f6b1afd914" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FNnuZqONaIhbOf6fn4OkZ%2FScreenshot%202023-08-28%20at%2011.37.47.png?alt=media&#x26;token=8a74f7b5-5bd2-4eea-97fa-1c1dbb041333" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](https://docs.ilert.com/alerting/alert-sources#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2FueugN4JgHn1c90ggFA6u%2FScreenshot%202023-08-28%20at%2011.38.24.png?alt=media&#x26;token=b8009daf-3ca8-4264-a6fa-e42ef7333205" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.​

    <figure><img src="https://4017197022-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-M76ygPnS4HUcFSX8ulm%2Fuploads%2Fi3TIOBvNYBQfDtNpmm0A%2FScreenshot%202023-08-28%20at%2011.47.34.png?alt=media&#x26;token=6cae965a-e448-4443-8c20-37cf501c43b2" alt=""><figcaption></figcaption></figure>

## In API Fortress

1. Click the gear icon in the top right corner to access the settings menu

![](../.gitbook/assets/apifortress-settings.png)

2. Navigate to "**Alert groups**" and create a new alert group if no Alert Group exists yet

![](../.gitbook/assets/apifortress-alertgroup.png)

3. Click "**Socket icon**" -> "**+ Connector to this group**"

![](../.gitbook/assets/apifortress-connector.png)

4. Select "**JSON Alert**" or "**JSON Alert /w threshold**", in this case we chose "JSON Alert /w threshold"

![](../.gitbook/assets/apifortress-jsonalert.png)

5. Put the URL Settings based on the API Fortress URL that we've got earlier in ilert Dashboard

More Details for "JSON Alert /w threshold" configs

**URL:** Webhook URL

**Counter:** Number of error before the alert is sent out

**TTL:** Time window in seconds before the alert is sent out (Ex. 2 errors counter over a time window of 60sec - 1 Minute)

![](../.gitbook/assets/apifortress-settingsproject.png)

6. Save the Config and go back to main dashboard

![](../.gitbook/assets/apifortress-project.png)

7. Click "**Settings**" on the project and assign the alert group
8. Upon meeting the alert criteria, JSON payload will be sent to the webhook URL, and Incident will be created in ilert
