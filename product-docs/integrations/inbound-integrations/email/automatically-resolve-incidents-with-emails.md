---
description: >-
  ilert's intelligent Email alert source allows you to parse alert keys and
  apply alert rules to create, accept or resolve open alerts based on incoming
  emails.
---

# Automatically resolve Alerts with Emails

## Alert Key extraction configuration

For this example we will demonstrate the alert key / identifier extraction based on a UUID version 4. We will use the following regex to extract the alert key from the subject of the incoming emails:

`[a-f0-9]{8}-[a-f0-9]{4}-4[a-f0-9]{3}-[89aAbB][a-f0-9]{3}-[a-f0-9]{12}`

When selecting the **subject** field, the extraction through regex is done by using the function **extractRegex()** from the [ITL](../../../rest-api/itl-ilert-template-language.md). This will cut out the text that is matched by the provided regex from the incoming email subject. We can simply pass the regex into the input field.

<figure><img src="../../../.gitbook/assets/image (269).png" alt=""><figcaption></figcaption></figure>

Every incoming email with now extract the alert key based on the provided regex. Providing a sample payload leads to the desired extraction.

<div><figure><img src="../../../.gitbook/assets/image (273).png" alt=""><figcaption></figcaption></figure> <figure><img src="../../../.gitbook/assets/image (272).png" alt=""><figcaption></figcaption></figure></div>

In case that no match for the regex is found, the email is dropped. In case that there is already an open alert for the extracted alert key, the email will not create a new alert, instead it will be attached to the existing alert. In case the email resolve filter (see below) will match and there is no open alert for the alert key, the email will also be dropped.

## Alert resolution

Now that we have configured our alert key extraction, we can set up our automatic email resolve filter. To enable the conditions we have to tick the checkbox for the resolve alert rule.

<figure><img src="../../../.gitbook/assets/image (274).png" alt=""><figcaption></figcaption></figure>

We are now able to configure as much conditions at we like (note that you can swap between applying **ALL** conditions **OR** single one of them, just like the accept filter).

In our example case we choose to scan the incoming email subjects for the text `resolve me` in case it is found and the alert key could be extracted (and an open alert for the same key exists) the incoming email will cause the alert to be resolved.

<figure><img src="../../../.gitbook/assets/image (275).png" alt=""><figcaption></figcaption></figure>

## Debugging Emails

In case your email alert source is not resolving as you would expect, you can always check the [Event Explorer](../../../alerting/alert-sources.md#event-explorer) to see how and why incoming emails where treated.

<figure><img src="../../../.gitbook/assets/image (276).png" alt=""><figcaption></figcaption></figure>
