---
description: >-
  iLert's intelligent Email alert source allows you to parse incident keys and
  resolve open incidents based on incoming emails.
---

# Automatically resolve Incidents with Emails

## Configuring auto Email Incident-Resolution

When creating or editing your email alert sources in iLert,  choose the incident creation type **Open and resolve incidents based incident keys extracted from emails**.

![](../../.gitbook/assets/screenshot-2020-06-17-at-14.46.18.png)

You will be granted with 2 new configuration options, when choosing this incident creation type: incident key extraction and email resolve filters.

![](../../.gitbook/assets/screenshot-2020-06-17-at-14.50.48.png)

## Incident Key extraction configuration

For this example we will demonstrate the incident key / identifier extraction based on a UUID version 4. We will use the following regex to extract the incident key from the subject of the incoming emails: 

`[a-f0-9]{8}-[a-f0-9]{4}-4[a-f0-9]{3}-[89aAbB][a-f0-9]{3}-[a-f0-9]{12}`

By selecting the incident key method **extract through regex** we tell iLert to cut out the text that is matched by the provided regex from the incoming email subject. We can simply pass the regex into the input field.

![](../../.gitbook/assets/screenshot-2020-06-17-at-14.51.58.png)

Every incoming email with now extract the incident key based on the provided regex. In case that no match for the regex is found, the email is dropped. In case that there is already an open incident for the extracted incident key, the email will not create a new incident, instead it will be attached to the existing incident. In case the email resolve filter \(see below\) will match and there is no open incident for the incident key, the email will also be dropped.

## Incident resolution

Now that we have configured our incident key extraction, we can set up our automatic email resolve filter. To enable the conditions we have to tick the checkbox.

![](../../.gitbook/assets/screenshot-2020-06-17-at-14.56.54.png)

We are now able to configure as much conditions at we like \(note that you can swap between applying **ALL** conditions **OR** single one of them, just like the accept filter\).

In our example case we choose to scan the incoming email subjects for the text `resolve me` in case it is found and the incident key could be extracted \(and an open incident for the same key exists\) the incoming email will cause the incident to be resolved.

## Debugging Emails / Mail log

In case your email alert source is not resolving as you would expect. You can always check the Mail Log to see how and why incoming emails where treated.

![](../../.gitbook/assets/screenshot-2020-06-17-at-15.01.41.png)





