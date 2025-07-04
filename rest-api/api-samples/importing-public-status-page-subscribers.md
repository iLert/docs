# Importing public status page subscribers

By default public status page subscribers need to confirm their subscription in the channel that they have subscribed too - a confirmation notification is send at creation.

When moving from other providers to ilert, you might want to migrate your existing subscribers that have already opted-in to their channels - without bothering your customers / subscribers with a resubscription.

{% hint style="info" %}
In case you are an Atlassian Statuspage customer, you may use our import UI [https://statuspage-import.ilert.net/](https://statuspage-import.ilert.net/) to move your status page resources to ilert (_we do not recommend to do this, if you already have created a status page in ilert_)
{% endhint %}

### You may use the public status page subscription bulk API for this operation:

Send a **POST** request to&#x20;

```
https://api.ilert.com/api/status-pages/{status-page-id}/subscribers_bulk?import=true
```

```json
[
    {
        "target": "+49171123123", // EMAIL, PHONE NUMBER, URL
        "type": "SMS" // EMAIL, SMS, WEBHOOK
        "locale": "en-GB", // en-GB | de-DE
        "services": [1, 2, 3] // optional list of service (id) restrictions (just leave out the whole key if not needed)
    },
    ...
]
```

{% hint style="danger" %}
Do not forget the **import=true** query parameter, otherwise you will send out confirmation notifications to your subscribers! We recommend testing with your own sample targets first, before bulking through thousands of subscribers. We suggest sending a maximum of 100-250 subscribers per HTTP call.
{% endhint %}

Visit the web UI (Status page -> Subscribers tab) to confirm your import.

{% hint style="warning" %}
Note that removing a confirmed subscriber will send an unsubscription notification to the target.
{% endhint %}
