---
description: Our open source client is available under MIT and Apache 2.0 License.
---

# Javascript / Node.js Client

You can find the official ilert JS client on our Github organization: [https://github.com/iLert/ilert-js](https://github.com/iLert/ilert-js)

Install as usual with NPM `npm install ilert`

```javascript
const { ILert } = require("ilert");
const ilert = new ILert();

// creating a new event
const { data } = await ilert.event().create(
    "il1api0460d849fcdc753d4f",
    ILert.EVENT_TYPES.ALERT,
    "My test incident summary",
    { incidentKey: "123456" } // optional
);

// resolving a pending incident
await ilert.incident(45678).resolve();

// ping a heartbeat
await ilert.heartbeat("il1hbt0460d849fcdc753").ping();
```

The ilert JS client also ships with Typescript definitions.

Please feel free to [reach out to us ](../../contact.md)with a Github issue in case you need help or have feature requests.

