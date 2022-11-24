---
title: How to integrate ilert?
seoTitle: 'iLert: How to integrate ilert? | Alerting | Incident Response | Uptime'
description: How is the integration of ilert with my existing monitoring tools carried out?
date: '2018-12-29T05:02:05.000Z'
weight: 3
---

# How to integrate ilert?

**How is the integration of ilert with my existing monitoring tools carried out?**

Each alert source within ilert has its own email address \(for example, [nagios@example.ilertnow.com](mailto:nagios@example.ilertnow.com)\). When the monitoring system sends an email to this address, ilert immediately creates an alert and initiates the alerting process.

In addition, we make available plugins for certain monitoring systems \(currently Nagios and Icinga\) that enable close interoperability with ilert. For example, with Nagios, this enables the handling of not just `PROBLEM` events but also `RECOVERY` and `ACKNOWLEDGEMENT` events. This means that whenever an alert is taken on or fixed by Nagios, this development is automatically reflected in ilert.

