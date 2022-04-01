---
description: Paoloalto Network Prisma Cloud Integration
---

# Prisma Cloud Integration

## In iLert

### Create a Prisma Cloud alert source

![](<../.gitbook/assets/image (50).png>)

Navigate to **Services -> Alert sources -> Create new alert source** (top right button)\
Choose **Pa Prisma Cloud** as integration type and create an alert source to your liking.

![](<../.gitbook/assets/image (49).png>)

After the creation of the alert source you will be able to copy the generated **url** which will be needed to setup the integration in Palo Alto Networks Prisma Cloud.



## In Prisma Cloud

Open your console and navigate to Mange -> Alerts\
You may also follow the official guide ([which can be found here](https://docs.paloaltonetworks.com/prisma/prisma-cloud/prisma-cloud-admin-compute/alerts/webhook.html#))

Create a **new webhook alert** and make sure to paste your alert source's url as **incoming webhook url.** We suggest the following template that should be used as **custom json** for your webhook:

```
{
    "type": #type,
    "time": #time,
    "container": #container,
    "image": #image,
    "host": #host,
    "fqdn": #fqdn,
    "function": #function,
    "region": #region,
    "runtime": #runtime,
    "appID": #appID,
    "rule": #rule,
    "message": #message,
    "forensics": #forensics,
    "accountID": #accountID,
    "cluster": #cluster,
    "labels": #labels,
    "collections": #collections
}
```

Feel free to test your configuration with **Send test alert**.

Setup the alert channels and triggers to your liking and click **Save**.

