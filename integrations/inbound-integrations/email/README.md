---
description: This page describes how to integrate ilert with any tool that can send emails.
---

# Email Inbound Integration

Email integration is the easiest way to integrate ilert with your monitoring system. Each email alert source in ilert has its own email address (e.g. _your-tool@your-domain.ilertnotify.com_). As soon as your monitoring system sends an email to this address, ilert will create an alert.

{% hint style="info" %}
If you are migrating from legqcy email settings, please follow [this](migrating-legacy-email-settings.md) guide for more info.
{% endhint %}

## Create an email alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1. Go to **Alert sources** and click on **Create new alert source**
2. Select **Email**
3. Enter a name and select an escalation policy
4. Enter an email address for the alert source
5. Click on **Continue Setup**

Your email alert source is now active. Any email sent to the email address will create an alert in ilert and trigger the alerting process using the alert source's escalation policy. The default setting creates an alert in ilert for each incoming email.&#x20;

<figure><img src="../../../.gitbook/assets/image (146).png" alt=""><figcaption></figcaption></figure>

## Fine-tuning email integration <a href="#advanced-settings" id="advanced-settings"></a>

All basic features of an alert source are available for the email alert source as well, but there are a couple of options to further fine-tune your alert source to the email use-case. Additionally, there are settings for custom processing rules only available for the email integration type.&#x20;

### Event filter

The event filter allows you to ignore emails based on the content of the email's properties, such as subject, body, cc, bcc and from.

<figure><img src="../../../.gitbook/assets/Screenshot 2025-06-02 at 17.20.07.png" alt=""><figcaption><p>In the above settings, only emails from my-tool@acme.com that contain the word PROBLEM in the subject will be accepted.</p></figcaption></figure>

More information on event filters can be found [here](../../../alerting/alert-sources.md#event-filter).

### Alert key extraction

You can choose any email field to be used as an alert key, serving as a unique identifier for open alerts. When another email with the same alert key is received, it will be correlated to any open alert with the same alert key, resulting in correlation and deduplication of emails. The alert key field makes use of the [ITL](../../../rest-api/itl-ilert-template-language.md).

<figure><img src="../../../.gitbook/assets/image (144).png" alt=""><figcaption><p>The subject of the email will be used as the alert key.</p></figcaption></figure>

### Custom processing rules

The email alert source allows for email-specific processing rules, determining when an incoming email should create, accept, or resolve an alert. A configuration via the [ICL](../../../rest-api/icl-ilert-condition-language.md) allows for complex rule setups.

Examples of such setups can be found here:

{% content-ref url="automatically-resolve-incidents-with-emails.md" %}
[automatically-resolve-incidents-with-emails.md](automatically-resolve-incidents-with-emails.md)
{% endcontent-ref %}

{% content-ref url="email-key-extraction-and-resolve-examples.md" %}
[email-key-extraction-and-resolve-examples.md](email-key-extraction-and-resolve-examples.md)
{% endcontent-ref %}

### Representation of Non-ASCII text in the headers

Note that [RFC 822](https://datatracker.ietf.org/doc/html/rfc822) headers must contain only US-ASCII characters. To use non-ASCII characters in the headers, they must be encoded by the caller according to the rules of [RFC 1342](https://datatracker.ietf.org/doc/html/rfc1342).

## FAQ <a href="#faq" id="faq"></a>

**Does ilert also process emails that are sent by forwarding to an alert source address?**

Yes, ilert evaluates the `TO` , `CC` and `BCC` fields as well as the `DELIVERED-TO` header when processing emails.

**My monitoring system sends emails when an issue is recovered (e.g. `RECOVERY` emails in Nagios). Can ilert use these emails to resolve previously created alerts?**

Yes, see [Automatically resolve Alerts with Emails](automatically-resolve-incidents-with-emails.md) for further information.

**I need more examples that illustrate regex alert key extraction from emails, where can I find them?**

Take a look [here](email-key-extraction-and-resolve-examples.md).\
\
**Why do my alerts contain odd characters such as `'Ã¶'` ?**

It seems like your email message does not follow the [RFC 822](https://datatracker.ietf.org/doc/html/rfc822) standard and contains Non-ASCII characters. Please refer to [this section](./#representation-of-non-ascii-text-in-the-headers).



## Related articles

{% content-ref url="../../outbound-integrations/email.md" %}
[email.md](../../outbound-integrations/email.md)
{% endcontent-ref %}
