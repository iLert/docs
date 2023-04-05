---
description: >-
  Dynamic alert actions offer the opportunity to extend manual alert actions on
  alerts or even notifications right as users are interacting with them.
---

# Dynamic Alert Actions

{% hint style="info" %}
Dynamic alert actions are in closed **BETA**, [reach out to us](../../contact.md) if you are interested in trying them out. **Note**: depending on the feedback of our BETA users this feature and its API are subject to potential change.
{% endhint %}

## Getting started

As dynamic actions are part of our application hooks, you will need to provide a webservice that is capable of dealing with the defined HTTP requests and will respond with the appropriate HTTP response bodies that the application can use to continue the user's flow.

{% hint style="success" %}
You may find the full demo webservice for the code samples described in this documentation [here](https://github.com/iLert/dynamic-action-provider).
{% endhint %}

## The alert action flow

1. a user interacts with an alert
2. he/she opens the actions menu
3. the actions are gathered based on all available manual alert actions for the alert's alert source
4. if a _dynamic action connection_ is present using its **requestUrl** the external service is fetched, while providing information about the alert and potentially the current user interacting with it
5. the external service provides _additional alert actions_ in its response
6. the actions are embedded into the alert actions offered to the user in ilert
7. if the user chooses to execute an alert action that was provided dynamically, ilert will call either the provided **url** for the specific action or fallback to the provided **responseUrl** of the dynamic action connection
8. the external service will receive the response call including the **actionId** which will help it to further execute any tasks e.g. `restart a VM`
9. the HTTP response of the external service is used to give the user feedback about his action e.g. inform him that the `VM restart has been successfully triggered`

## The external service

Our alert action flow above shows that 2 things are needed from the external service:

* giving out potential dynamic alert actions under the requestUrl
* triggering actions based on actionId during calls to responseUrl

### Action request API documentation

The HTTP request used by ilert to fetch additional actions for an alert.

{% hint style="info" %}
The `alert` sub object is equal to our [API resource /alerts](https://api.ilert.com/api-docs/#tag/Alerts/paths/\~1alerts\~1{id}/get)

The `user` sub object is optional, it is only present in a notification context
{% endhint %}

#### HTTP request

{% tabs %}
{% tab title="Sample handler" %}
```javascript
app.post("/api/action-requests", (req, res) => {

            const {
                alert,
                user,
                locale
            } = req.body;
            
            // analyse alert and identify qualified response actions

            res.json({
                actions: [
                    {
                        id: "abc",
                        text: locale === "de" ? "Aus ALB nehmen" : "Remove from ALB",
                        url: `https://some-domain.com/some-other-endpoint`
                    },
                    {
                        id: "def",
                        text: locale === "de" ? "Kafka-Playback ausführen" : "Run Kafka playback"
                    },
                    {
                        id: "ghi",
                        text: locale === "de" ? "Kubernetes pod skalieren" : "Scale Kubernetes pod"
                    }
                ]
            });
        });
```
{% endtab %}

{% tab title="Sample request" %}
```shell
curl --request POST \
  --url http://some-domain.com/api/action-requests \
  --header 'Authorization: some-optional-auth' \
  --header 'Content-Type: application/json' \
  --data '{
	"user": {
		"id": 0,
		"email": "string"
	},
	"locale": "de",
	"alert": {...}
}'
```
{% endtab %}
{% endtabs %}

#### Expected HTTP response

{% hint style="warning" %}
Your service must respond within 3000 ms, or the request is dropped.

In the event of a timeout or invalid response data, the alerts are provided without dynamic additions, no error is shown to the user.

You can provide a maximum of 3 actions.

Your actions might differ for any request, however responses for the same alert (and in notifications user) are cached for up to 1 hour. Note: this cache is cleared, as soon as an action is triggered.

If your service is continuously unavailable for requests, we might disable your dynamic alert connection.

We **highly recommend** that your webservice provides **deterministic action ids** for subsequent requests. e.g. _"Restart VM" action in context of the alert / alert source will always have id 12345._
{% endhint %}

{% tabs %}
{% tab title="Dynamic actions response schema" %}
```javascript
[
    {
        id: "string",
        text: "string",
        url: "string" | null
    }
]
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Note that providing the **url** field is optional and only needed if you do not wish to handle responses with the same web service that provides the actions. Not providing the url will cause ilert to use the **responseUrl** provided in your dynamic action connection. If both are missing, the action will fail.
{% endhint %}

### Action response API documentation

#### HTTP request

{% hint style="info" %}
The `alert` sub object is equal to our [API resource /alerts](https://api.ilert.com/api-docs/#tag/Alerts/paths/\~1alerts\~1{id}/get)

The `user` sub object is optional, it is only present in a notification context
{% endhint %}

{% tabs %}
{% tab title="Sample handler" %}
```javascript
app.post("/api/action-responses", (req, res) => {

            const {
                actionId: id,
                alert,
                user,
                locale
            } = req.body;

            let text = null;
            switch(id) {
                case "abc": text = locale === "de" ? "Aus ALB genommen" : "Removed from ALB"; break;
                case "def": text = locale === "de" ? "Kafka topic wurde eingespielt" : "Kafka topic has been replayed"; break;
                case "ghi": text = locale === "de" ? "Kubernetes deployment wurde skaliert" : "Kubernetes deployment has been scaled"; break;
                default: return res.status(400).end();
            }
            // run action for id e.g. restart server...

            res.json({
                success: true,
                text
            });
        });
```
{% endtab %}

{% tab title="Sample request" %}
```shell
curl --request POST \
  --url http://some-domain.com/api/action-responses \
  --header 'Authorization: some-optional-auth' \
  --header 'Content-Type: application/json' \
  --data '{
	"user": {
		"id": 0,
		"email": "string"
	},
	"locale": "en",
	"alert": {...},
	"actionId": "string"
}'
```
{% endtab %}
{% endtabs %}

#### Expected HTTP response

{% tabs %}
{% tab title="Response schema" %}
```javascript
{
    "success": true,
    "text": "string"
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
The provided text will be used as feedback for the user that has invoked the action. It will also become part of the alert's timeline as action log entry.
{% endhint %}

## Creating a dynamic alert action connection

Navigate to your alert source and switch to the **Alert actions** tab. Click on **Create new alert action**.

![](<../../.gitbook/assets/image (53) (1).png>)

If this is the first time you are creating a dynamic alert action. You will need to create a new connector (_requires Admin permissions_) that holds the information and optional credentials for your web service.

![](<../../.gitbook/assets/image (61) (1).png>)

Enter the urls for your webservice and optional credentials (will be sent via HTTP **Authorization** header). Then save your connector.

![](<../../.gitbook/assets/image (58) (2).png>)

Using your dynamic action connector you may now create a dynamic action alert connection, which will link the alert source to your webservice.

Your actions are now fetched and rendered on alerts.

![](<../../.gitbook/assets/image (60) (1).png>)

### Enhancing notifications with dynamic actions

Enable the checkbox **Enhance notifications** in your alert action's settings.\
Currently only voice alert notifications are supported.

{% hint style="warning" %}
If a user triggers any dynamic action during a voice call, ilert will automatically **ACCEPT** the alert in his name.
{% endhint %}

## FAQ

### Can I create multiple dynamic action connections per alert source ?

You can, however, only the first one will be used.

### What happens when my connection gets disabled?

You can simply enable it again, by updating the dynamic alert action.

### Can I create mulitple dynamc actions for different alert sources?

You may add an dynamic action for each of your alert sources.

### When do fetched alert actions timeout?

Currently ilert caches dynamic alert actions for up to 1 hour, from the first time they are fetched. If the view you are using e.g. Slack chat is older than 1 hour, invoking the action will fail, if your webservice is not providing deterministic action ids on subsequent requests. If your webservice is always providing deterministic ids for its actions, alert actions wont timeout.

### Are dynamic actions available in voice notifications?

Yes, if you enable the checkbox (dynamic alert action setttings) to enhance your notifications, the provided actions of your web service will become available as digits 7, 8 and 9 during voice alerts.

### May I choose digits or ids for actions?

No, digits and ids for alert actions are generated by ilert and mapped back to ids of your service before responding.
