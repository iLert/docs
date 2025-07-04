---
description: >-
  With the ilert Google Security Command Center integration, you can create
  alerts in ilert based on Google Security Command Center findings.
---

# Google Security Command Center

## In ilert: Create a Google Security Command Center alert source

1.  Go to **Alert sources** --> **Alert sources** and click on **Create new alert source**

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.21.10.png" alt=""><figcaption></figcaption></figure>
2.  Search for **Google Security Command Center** in the search field, click on the Google Security Command Center tile and click on **Next**.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 10.24.23.png" alt=""><figcaption></figcaption></figure>
3. Give your alert source a name, optionally assign teams and click **Next**.
4.  Select an **escalation policy** by creating a new one or assigning an existing one.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.37.47.png" alt=""><figcaption></figcaption></figure>
5.  Select you [Alert grouping](../../alerting/alert-sources.md#alert-grouping) preference and click **Continue setup**. You may click **Do not group alerts** for now and change it later.&#x20;

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.38.24.png" alt=""><figcaption></figcaption></figure>
6. The next page show additional settings such as customer alert templates or notification prioritiy. Click on **Finish setup** for now.
7.  On the final page, an API key and / or webhook URL will be generated that you will need later in this guide.

    <figure><img src="../../.gitbook/assets/Screenshot 2023-08-28 at 11.47.34 (1).png" alt=""><figcaption></figcaption></figure>

## In Google Security Command Center: Sending notifications via Google Cloud Functions

1. Enable finding notifications for Pub/Sub with the following guide: [https://cloud.google.com/security-command-center/docs/how-to-notifications#create-notification-config](https://cloud.google.com/security-command-center/docs/how-to-notifications#create-notification-config)
2. Create following function example in Google Cloud Functions. Make sure to replace `[WEBHOOK_URL]`with the Url generated in [this step](google-security-command-center.md#in-ilert-create-google-security-command-center-alert-source).

{% tabs %}
{% tab title="Go" %}
```go
import (
	"context"
	"log"
	"net/http"
	"github.com/go-resty/resty/v2"
)

type PubSubMessage struct {
	Data []byte `json:"data"`
}

func WebhookPubSub(ctx context.Context, m PubSubMessage) {

	// Send the webhook request with the Pub/Sub message as the content
	webhookURL := "[WEBHOOK_URL]"

	client := resty.New()
	resp, err := client.R().
		SetHeader("Content-Type", "application/json").
		SetBody(m.Data).
		Post(webhookURL)
	if err != nil {
		log.Printf("Error creating webhook request: %v", err)
		return
	}

	// Check the webhook response
	if resp.StatusCode() != http.StatusAccepted {
		log.Printf("Webhook request failed with status code: %d", resp.StatusCode())
		return
	}
}
```
{% endtab %}
{% endtabs %}

3. Deploy the Google Cloud Function by running the following command in the terminal:\
   \
   `gcloud functions deploy WebhookPubSub --runtime go116 --trigger-topic YOUR_PUBSUB_TOPIC`\
   \
   Replace `YOUR_PUBSUB_TOPIC` with the actual Pub/Sub topic name that you want the Cloud Function to be triggered by.

## FAQ <a href="#faq" id="faq"></a>

**Will alerts in ilert be resolved automatically?**

Yes, as soon as the state of an alert in Google Security Command Center is `RESOLVED`, the associated alert in ilert is resolved.

