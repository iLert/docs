---
icon: webhook
---

# API deployment pipeline

If you wish to integrate your custom deployment or CI & CD pipelines with ilert's deployment events, you can use the generic API deployment pipeline to generate an `integrationKey` and process your own events.&#x20;

## Setting up

### Creating your deployment pipeline in ilert

To create the pipeline and generate a new `integrationKey` required to route deployment events when they occur. Head to your ilert account and navigate to **Alert sources -> Deployment events**

<figure><img src="../../.gitbook/assets/image (126).png" alt=""><figcaption></figcaption></figure>

Head over to the deployment pipelines tab and click on **Create new pipeline**

<figure><img src="../../.gitbook/assets/image (127).png" alt=""><figcaption></figcaption></figure>

Provide a name for your pipeline

<figure><img src="../../.gitbook/assets/image (128).png" alt=""><figcaption></figcaption></figure>

Clicking on **Create** you should end up on the detail view of your new API deployment pipeline.

<figure><img src="../../.gitbook/assets/image (129).png" alt=""><figcaption></figcaption></figure>

Providing you with a freshly generated `integrationKey` and the copy & pastable **URL** ready for your client setup.

### Sending deployment events

To send deployment events to ilert and **POST HTTP** request is needed containing the `integrationKey` as body field. The full API docs can be found here: [https://api.ilert.com/api-docs/#tag/deployment-events/post/deployment-events](https://api.ilert.com/api-docs/#tag/deployment-events/post/deployment-events)

A sample curl request might look like this:

```sh
curl --request POST \
  --url https://api.ilert.com/api/deployment-events \
  --header 'Content-Type: application/json' \
  --data '{
  "integrationKey": "ilapid11124e2c79adac1ed4454890db0a7d3c20c66ba",
  "summary": "My custom deployment event",
  "timestamp": "2024-11-05T22:17:38Z",
  "customDetails": { "some": "customData" },
  "links": [
    {
      "href": "http://google.com",
      "text": "A custom link to the source of this deployment event"
    }
  ]
}'
```

Note that only the `integrationKey` and `summary` fields are required. All others are optional. The `timestamp` fields support epochSeconds, epochMilliseconds or ISO8601 datetime strings.
