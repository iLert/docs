---
title: E-mail Integration
seoTitle: 'iLert: E-mail Integration for Alerting | Incident Response | Uptime'
description: This page describes how to integrate iLert with any tool that can send emails.
date: '2018-12-29T05:02:05.000Z'
weight: 1
---

# Email Integration

Email integration is the easiest way to integrate iLert with your monitoring system. Each email alert source in iLert has its own email address \(e.g. _your-tool@your-domain.ilertnow.com_\). As soon as your monitoring system sends an e-mail to this address, iLert will create an incident.

## In iLert: create an email alert source <a id="create-alarm-source"></a>

1. Go to **Alert sources** and click on **Add a new alert source**
2. Enter a name and select an escalation policy
3. Chose **Email** as integation type
4. Enter an email address for the alert source
5. Save the email alert source

![](../../.gitbook/assets/screenshot-2020-06-18-at-16.21.49.png)

Your email alert source is now active. Any email sent to the  email address will create an incident in iLert and trigger the alerting process using the alert source's escalation policy. The default setting creates an incident in iLert for each incoming email. The next section explains advanced settings, such as deduplicating or filtering emails.

## Fine-tuning email integration <a id="advanced-settings"></a>

By default, iLert creates a new incident for every email sent to the alert source's email address. You can fine-tune this behavior by 

* adding email filter, which lets you filter emails based on defined conditions
* modifying incident creation options

### Email filters

Email filters allow you to ignore emails based on the content of the email's subject, body, or from address.

![In the above sttings, only emails from my-tool@acme.com that contain the word PROBLEM in the subject will be accepted.](../../.gitbook/assets/image.png)

### Incident creation

<table>
  <thead>
    <tr>
      <th style="text-align:left">Option</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Open a new incident for every email</td>
      <td style="text-align:left">Each email sent to the alert source&apos;s email address will create a
        new incident.</td>
    </tr>
    <tr>
      <td style="text-align:left">Open a new incident for every new email subject</td>
      <td style="text-align:left">
        <p>Incidents are de-duplicated based on the subject of the emails. Case sensivitiy
          and whitespaces are ignored. Deduplication considers only the emails of
          open incidents.
          <br />
        </p>
        <p>If, for example, a monitoring system sends two e-mails in succession with
          the same subject, a new incident is created for the first e-mail and the
          second e-mail is appended to the created incident in the event log.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Open a new incident only if all incidents in this alert source are in <code>RESOLVED</code> or <code>ACCEPTED OR RESOLVED</code>state</td>
      <td
      style="text-align:left">An email sent to the alert source&apos;s email address will only open
        a new incident if an open incident does not already exist; otherwise, the
        email will be appended to the last open incident.
        <br />
        <br />Example: You get alerted at 3 A.M. in the morning and accept the incident
        and decide to look at the problem the next morning. In the meantime, if
        a new (potentially critical) issue is reported to iLert, a new incident
        will be notified again. In this scenario, you need to chose <code>ACCEPTED ir RESOLVED</code> in
        the dropdown list.</td>
    </tr>
    <tr>
      <td style="text-align:left">Open and resolve incidents based incident keys extracted from emails</td>
      <td
      style="text-align:left">Use defined rules to link emails to the same incident based on matching
        substrings in the email subject or body. See <a href="automatically-resolve-incidents-with-emails.md">Automatically resolve Incidents with Emails</a>
        </td>
    </tr>
  </tbody>
</table>

### Incident Resolution based on Emails

{% page-ref page="automatically-resolve-incidents-with-emails.md" %}

## FAQ <a id="faq"></a>

**Does iLert also process e-mails that are sent by forwarding to an alert source address?**

Yes, iLert evaluates the `TO` , `CC` and `BCC` fields as well as the `DELIVERED-TO` header when processing email.

**My monitoring system sends emails when an issue is recovered  \(e.g. `RECOVERY` emails in Nagios\). Can iLert use these emails to resolve previously created incidents?**

Yes, see [Automatically resolve Incidents with Emails](automatically-resolve-incidents-with-emails.md) for further information

