---
description: >-
  Switching agent call behaviour automatically between office hours is possible
  for Premium and Enterprise customers.
---

# Managing office hours call behaviour

Another possible configuration for support hour based routing is the use of different call behaviours for agents, based on office hours.

In the example below the **Ops Team** routing option has been configured to use the `Simultaneous calling` feature, where **Duty Team** has not. The time-based routing options have been configured to skip the **IVR menu**.

![](../../.gitbook/assets/image%20%2824%29.png)

In case an incoming call is made during office hours \(_support hours in this case_\) the Ops Team route will be used and based on the simultaneous calling option all agents in the escalation policy we be called at the same time.

In case an incoming call is made after office hours \(_outside support hours in this case_\) the Duty Team route will be used and all agents will be called on an escalating principle one-by-one.

Additionally with this setup, individual escalations can be configured \(in the used escalation policies\) to handle cases where all agents did not accept calls outside of support hours.

**To put in simple terms**: During office hours all team members get called simultaneously, the incident is no further escalated - Outside of office hours the one person on duty is called and the incident may be escalated further.

{% hint style="info" %}
Please note that the `simultaneous calling` feature is only available for Premium and Enterprise customers.
{% endhint %}

