---
description: >-
  IBM Cloud Function provides a service to run your application code without
  servers, scale it automatically, and pay nothing when it's not in use, with
  integrations with IBM Cloud services.
---

# IBM Cloud Functions Integration

## In ilert: Create a IBM Cloud Functions alert source

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **IBM Cloud Functions** in the search field, click on the IBM Cloud Functions tile and click on **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In IBM Cloud Functions

1. On IBM Cloud Functions dashboard, create an Action by clicking "**Actions**" -> "**Create**"

![](../../.gitbook/assets/ibmcloud-createaction.png)

2. Choose the name of your choice, in this case we will name it as "ilert-incidents", and choose "**Node.js 12**" as a runtime

![](../../.gitbook/assets/ibmcloud-functionaction.png)

3. Paste the following on the code, and please replace the "**ILERT\_URL**" with the **IBM Cloud Functions URL** that we got earlier on ilert's dashboard

```javascript
/**
  *
  * main() will be run when you invoke this action
  *
  * @param Cloud Functions actions accept a single parameter, which must be a JSON object.
  *
  * @return The output of this action, which must be a JSON object.
  *
  */
const request = require('request-promise');

function main(params) {

    if (!params.apiKey || !params.summary || !params.details) {
        throw new Error("params need to include 'apiKey', 'summary', and 'details'");
    }
    
    if (!params.eventType) {
        params.eventType = "ALERT";
    }

	console.log(`params: ${JSON.stringify(params)}`);

	// Set request options
	const options = {
		url: 'ILERT_URL',
		method: 'POST',
		json: true,
		body: params
	};

	// Make POST request
	return request(options)
	    .catch((error) => {
	        throw error;
	    });
}
```

4. To trigger it, we need to pass the params, in this case click on "**Invoke with parameters**" on top right

![](../../.gitbook/assets/ibmcloud-invokewithparams.png)

5. Put the following as a parameter, you can adjust the summary and details, however please replace the "**API\_KEY**" \*\*\*\* with the IBM Cloud Functions **API Key** that we go on ilert's dashboard earlier and **Apply** the parameters

```
{
    "apiKey":"API_KEY",
    "eventType": "ALERT",
    "summary": "Test IBM Function",
    "details": "Test IBM Function success"
}
```

6. To trigger the creation of incidents on ilert simple click "**Invoke**" on the top right, and it should create the incident on ilert

![](../../.gitbook/assets/ibmcloud-invokesuccess.png)

## FAQ

1.  How to trigger the incident creation from other service?

    For more information about invoking from trigger in IBM Cloud Service, please refer to IBM Documentation: [https://cloud.ibm.com/docs/openwhisk?topic=openwhisk-triggers](https://cloud.ibm.com/docs/openwhisk?topic=openwhisk-triggers)
2.  Is it possible to manage the incident, for example to accept or resolve the incident?

    Yes it is possible if the `eventType` is passed with value `ACCEPT` or `RESOLVE`, this should accept and resolve the issue respectively. In addition to that, you need to pass the `incidentKey` parameter on creation as well. All the parameter on event creation will be accepted. For more information, please refer to our API Documentation: [https://api.ilert.com/api-docs/#tag/Events/paths/\~1events/post](https://api.ilert.com/api-docs/#tag/Events/paths/~1events/post)
