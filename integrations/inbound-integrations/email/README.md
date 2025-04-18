---
description: This page describes how to integrate ilert with any tool that can send emails.
---

# Email Inbound Integration

Email integration is the easiest way to integrate ilert with your monitoring system. Each email alert source in ilert has its own email address (e.g. _your-tool@your-domain.ilertnow.com_). As soon as your monitoring system sends an e-mail to this address, ilert will create an alert.

## In ilert: create an email alert source <a href="#create-alarm-source" id="create-alarm-source"></a>

1. Go to **Alert sources** and click on **Add a new alert source**
2. Enter a name and select an escalation policy
3. Chose **Email** as integation type
4. Enter an email address for the alert source
5. Save the email alert source

![](<../../../.gitbook/assets/Screenshot 2020-06-18 at 16.21.49.png>)

Your email alert source is now active. Any email sent to the email address will create an alert in ilert and trigger the alerting process using the alert source's escalation policy. The default setting creates an alert in ilert for each incoming email. The next section explains advanced settings, such as deduplicating or filtering emails.

## Fine-tuning email integration <a href="#advanced-settings" id="advanced-settings"></a>

By default, ilert creates a new alert for every email sent to the alert source's email address. You can fine-tune this behavior by

* adding email filter, which lets you filter emails based on defined conditions
* modifying alert creation options

### Email filters

Email filters allow you to ignore emails based on the content of the email's subject, body, or from address.

![In the above sttings, only emails from my-tool@acme.com that contain the word PROBLEM in the subject will be accepted.](<../../../.gitbook/assets/image (40).png>)

### Alert creation

| Option                                                                                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Open a new alert for every email                                                                          | Each email sent to the alert source's email address will create a new alert.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Open a new alert for every new email subject                                                              | <p>Alerts are de-duplicated based on the subject of the emails. Case sensivitiy and whitespaces are ignored. Deduplication considers only the emails of open alerts.<br></p><p>If, for example, a monitoring system sends two e-mails in succession with the same subject, a new alert is created for the first e-mail and the second e-mail is appended to the created alert in the event log.</p>                                                                                                                                       |
| Open a new alert only if all alerts in this alert source are in `RESOLVED` or `ACCEPTED OR RESOLVED`state | <p>An email sent to the alert source's email address will only open a new alert if an open alert does not already exist; otherwise, the email will be appended to the last open alert.<br><br>Example: You get alerted at 3 A.M. in the morning and accept the alert and decide to look at the problem the next morning. In the meantime, if a new (potentially critical) issue is reported to ilert, a new alert will be notified again. In this scenario, you need to chose <code>ACCEPTED ir RESOLVED</code> in the dropdown list.</p> |
| Open and resolve alerts based alert keys extracted from emails                                            | Use defined rules to link emails to the same alert based on matching substrings in the email subject or body. See [Automatically resolve Alerts with Emails](automatically-resolve-incidents-with-emails.md)                                                                                                                                                                                                                                                                                                                              |

### Incident Resolution based on Emails

{% content-ref url="automatically-resolve-incidents-with-emails.md" %}
[automatically-resolve-incidents-with-emails.md](automatically-resolve-incidents-with-emails.md)
{% endcontent-ref %}

### Representation of Non-ASCII text in the headers

Note that [RFC 822](https://datatracker.ietf.org/doc/html/rfc822) headers must contain only US-ASCII characters. To use non-ASCII characters in the headers, they must be encoded by the caller according to the rules of [RFC 1342](https://datatracker.ietf.org/doc/html/rfc1342).

## FAQ <a href="#faq" id="faq"></a>

**Does ilert also process e-mails that are sent by forwarding to an alert source address?**

Yes, ilert evaluates the `TO` , `CC` and `BCC` fields as well as the `DELIVERED-TO` header when processing email.

**My monitoring system sends emails when an issue is recovered (e.g. `RECOVERY` emails in Nagios). Can ilert use these emails to resolve previously created alerts?**

Yes, see [Automatically resolve Alerts with Emails](automatically-resolve-incidents-with-emails.md) for further information

**I need more examples that illustrate regex alert key extraction from emails, where can I find them?**

Take a look [here](email-key-extraction-and-resolve-examples.md).\
\
**Why do my alerts contain odd characters such as `'Ã¶'` ?**

It seems like your email message does not follow the [RFC 822](https://datatracker.ietf.org/doc/html/rfc822) standard and contains Non-ASCII characters. Please refer to [this section](./#representation-of-non-ascii-text-in-the-headers).



## Related articles

{% content-ref url="../../outbound-integrations/email.md" %}
[email.md](../../outbound-integrations/email.md)
{% endcontent-ref %}
