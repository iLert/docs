# Migrating legacy email settings

In March 2025, we've reworked the infrastructure behind our email alert source, enabling all common features for an email alert source too. With this, some settings have changed and were replaced by new, even more powerful features. The following will cover the steps needed to achieve the equivalent in settings when migrating from old to new.

{% hint style="info" %}
The integration email domain changed from **ilertnow.com to** **ilertnotify.com**.
{% endhint %}

## Email filters

Conditions from the legacy email filter are defined in the same way with the alert source's [**event filter**](../../../alerting/alert-sources.md#event-filter). Using the [ICL](../../../rest-api/icl-ilert-condition-language.md), more fields and functions to build conditions are now available.

<figure><img src="../../../.gitbook/assets/image (281).png" alt=""><figcaption></figcaption></figure>

## Alert grouping

For time-based and no grouping the grouping options with the same name are used. Content-based grouping can be achieved through AI-based similarity grouping, more info [here](../../../alerting/alert-sources.md#alert-grouping).

<figure><img src="../../../.gitbook/assets/image (283).png" alt=""><figcaption></figcaption></figure>

### Alert key extraction

Previously, only the email subject and body could be used for alert key extraction, the new [ITL](../../../rest-api/itl-ilert-template-language.md) based definition allows for any of the event's fields plus new functions for extracting an alert key.

<figure><img src="../../../.gitbook/assets/image (285).png" alt=""><figcaption></figcaption></figure>

### Alert resolution

Adding rules for resolving an alert is now done by creating a resolve alert rule. They are defined like the event filter using [ICL](../../../rest-api/icl-ilert-condition-language.md). An improvement over the old design is the ability to create rules for not only resolving, but also creating and accepting alerts.

<figure><img src="../../../.gitbook/assets/image (286).png" alt=""><figcaption></figcaption></figure>

## Mail log

With the new email alert source, the mail log was replaced in favor of the [event explorer](../../../alerting/alert-sources.md#event-explorer). But as before all incoming mails plus more data for each received mail is shown there, even if they did not create an alert.
