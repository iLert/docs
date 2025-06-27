---
description: Official ilert API client libraries for popular programming languages to support incident management and reliable alerting.
---

# Client Libraries

ilert provides official client libraries for popular programming languages to make it easier to integrate with our incident management platform. These libraries handle authentication, request formatting, and response parsing for reliable incident alerting.

## Available Libraries

### [Go Client](go-client.md)
Official Go client with full API coverage and idiomatic Go patterns for incident management.

```go
import "github.com/iLert/ilert-go"

client := ilert.NewClient(apiKey)
event, err := client.Events.Create(&ilert.CreateEventInput{
    EventType: ilert.EventTypeAlert,
    Summary:   "Server down",
    Details:   "Production server is not responding",
})
```

### [Rust Client](rust-client.md)
Rust client with async/await support and strong typing for reliable incident response.

```rust
use ilert_rs::ILert;

let client = ILert::new(api_key);
let event = client.events()
    .create("alert", "Server down", "Production server is not responding")
    .await?;
```

### [JavaScript/Node.js Client](javascript-node.js-client.md)
Node.js client with TypeScript support and Promise-based API for incident management.

```javascript
const { ILert } = require("ilert");
const ilert = new ILert(apiKey);

const event = await ilert.event().create(
    "il1api0460d849fcdc753d4f",
    ILert.EVENT_TYPES.ALERT,
    "Server down",
    { incidentKey: "123456" }
);
```

### [ilert Agent (ilagent)](ilagent.md)
Command-line tool for sending incidents and managing ilert resources for reliable incident response.

```bash
# Send an incident
ilagent alert create --summary "Server down" --details "Production server is not responding"

# Ping a heartbeat
ilagent heartbeat ping il1hbt0460d849fcdc753
```

## Quick Start Examples

### Send an Incident
```bash
# Using curl
curl -X POST https://api.ilert.com/api/v1/events/YOUR_API_KEY \
  -H "Content-Type: application/json" \
  -d '{
    "eventType": "ALERT",
    "summary": "Database connection failed",
    "details": "Unable to connect to production database"
  }'
```

### Resolve an Incident
```bash
# Using curl
curl -X POST https://api.ilert.com/api/v1/incidents/12345/resolve \
  -H "Authorization: Bearer YOUR_API_KEY"
```

### Ping a Heartbeat
```bash
# Using curl
curl -X POST https://api.ilert.com/api/v1/heartbeats/YOUR_HEARTBEAT_KEY/ping
```

## API Reference

- **[Interactive API Docs](https://api.ilert.com/api-docs/)** - Explore all endpoints
- **[API Version History](api-version-history/README.md)** - Track API changes
- **[Rate Limiting](alertsource-throttle.md)** - Understand API limits
- **[Authentication](https://api.ilert.com/api-docs/#section/Authentication)** - Learn about API keys

## Common Use Cases

### 1. **Custom Monitoring Scripts**
```python
import requests

def send_incident(api_key, summary, details):
    response = requests.post(
        f"https://api.ilert.com/api/v1/events/{api_key}",
        json={
            "eventType": "ALERT",
            "summary": summary,
            "details": details
        }
    )
    return response.json()
```

### 2. **Health Check Monitoring**
```bash
#!/bin/bash
if ! curl -f http://localhost:8080/health; then
    curl -X POST https://api.ilert.com/api/v1/events/YOUR_API_KEY \
      -H "Content-Type: application/json" \
      -d '{
        "eventType": "ALERT",
        "summary": "Application health check failed",
        "details": "Health endpoint returned non-200 status"
      }'
fi
```

### 3. **Deployment Notifications**
```javascript
const { ILert } = require("ilert");

async function notifyDeployment(environment, version) {
    const ilert = new ILert(process.env.ILERT_API_KEY);
    
    await ilert.event().create(
        process.env.ILERT_API_KEY,
        "INFO",
        `Deployment to ${environment}`,
        {
            details: `Version ${version} deployed successfully`,
            incidentKey: `deploy-${environment}-${version}`
        }
    );
}
```

## Best Practices

1. **Use Environment Variables** for API keys
2. **Implement Retry Logic** for failed requests to ensure reliable incident response
3. **Set Appropriate Timeouts** for your use case
4. **Use Incident Keys** to prevent duplicate incidents
5. **Monitor API Usage** to stay within rate limits

## Need Help?

- **Documentation**: Browse our [incident management API guides](README.md)
- **Examples**: Check our [API samples](api-samples/README.md)
- **Support**: Contact us at [support@ilert.com](mailto:support@ilert.com)
- **Community**: Join our [Discord](https://discord.gg/ilert)

{% hint style="info" %}
Missing a client library for your language? Let us [know](../../contact.md) and we'll consider adding it!
{% endhint %}



