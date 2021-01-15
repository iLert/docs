---
description: >-
  To provide a more stable throughput and fairness among different accounts in
  terms of resource consumption, iLert applies rate limiting to API and
  integration requests.
---

# Rate Limiting

If a request exceeds the defined rate limit, the request is rejected with the HTTP status code `429 Too many requests`.

The following rate limits apply:

| Target | Max Number of Requests \(Limit\) | Time Window |
| :--- | :--- | :--- |
| API | 700 | 1 Minute |
| UI | 250 | 1 Minute |
| Integration Key \(Alert source\) | 50 | 1 Minute |
| Heartbeat Key | 5 | 1 Minute |

Exceeding a limit will cause a client to be rejected with 429 responses until a new window starts. There are no other consequences.

Clients may retry their requests on 429 responses with a backoff timeout, 10-30 seconds are suggested.

In case of integration key limits for alert sources, we will show a warning message on alert sources \(and their related incidents\) which limits exceeded. This message will disappear automatically after 48 hours.

{% hint style="info" %}
In case your use-case requires a higher rate limit, feel free to [reach out](../contact.md) to us.
{% endhint %}

