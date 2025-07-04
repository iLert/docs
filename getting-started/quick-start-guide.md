---
description: >-
  Get up and running with ilert's incident management platform in 5 minutes with
  this step-by-step guide.
---

# Quick Start Guide

This guide will help you set up ilert's incident management platform and create your first incident alert in under 5 minutes.

## Prerequisites

* An ilert account ([sign up here](https://app.ilert.com/signup))
* A monitoring tool or service you want to connect (optional for testing)

## Step 1: Sign Up and Log In

1. Go to [app.ilert.com](https://app.ilert.com/signup)
2. Create your account with your email address
3. Verify your email and log in to the ilert dashboard

## Step 2: Create Your First Alert Source

An alert source connects your monitoring tools to ilert for reliable incident alerting. Let's create one:

1. In the ilert dashboard, click **Alert sources** → **Alert sources**
2. Click **Create new alert source**
3. Choose your integration type:
   * **For testing**: Select "Email" or "Event API"
   * **For production**: Select your monitoring tool (e.g., Prometheus, CloudWatch, Datadog)
4. Give your alert source a descriptive name (e.g., "Production Server Monitoring")
5. Click **Next**

## Step 3: Set Up Escalation Policy

An escalation policy defines who gets notified when incidents are triggered to ensure reliable incident response:

1. Click **Create new escalation policy**
2. Name your policy (e.g., "Primary On-Call")
3. Add yourself as the first responder
4. Set escalation delays (e.g., 5 minutes)
5. Click **Save** and then **Next**

## Step 4: Configure Alert Grouping

Choose how alerts should be grouped to reduce noise:

1. Select **Do not group alerts** for now (you can change this later)
2. Click **Continue setup**

## Step 5: Configure Notifications

Set up how you want to receive incident notifications for reliable alerting:

1. Go to **User settings** → **Notification settings**
2. Add your phone number for SMS/calls
3. Configure your preferred notification channels
4. Set up notification rules (when to use high vs low priority)

## Step 6: Test Your Setup

Send a test alert alert to verify everything works:

### Option A: Using Email Integration

1. Copy the email address from your alert source
2. Send a test email to that address
3. Check your notifications

### Option B: Using Event API

```bash
curl -X POST https://api.ilert.com/api/events \
  -H "Content-Type: application/json" \
  -d '{
    "integrationKey": "<paste key here>"
    "eventType": "ALERT",
    "summary": "Test alert from Quick Start Guide",
    "details": "This is a test alert to verify your ilert incident management setup"
  }'
```

## Step 7: Install the Mobile App

Download the ilert mobile app for iOS or Android to manage incidents on the go:

* **iOS**: [App Store](https://apps.apple.com/app/ilert/id542915864)
* **Android**: [Google Play](https://play.google.com/store/apps/details?id=de.ilert.client.iphone)

## What's Next?

Now that you have the basics set up, explore these incident management features:

* [**Connect more monitoring tools**](integrations/types-of-integrations.md) - Add your existing monitoring stack for comprehensive incident coverage
* [**Set up on-call schedules**](on-call-management-and-escalations/on-call-schedules/) - Create rotation schedules for your team
* [**Configure status pages**](incident-comms-and-status-pages/getting-started.md) - Communicate incidents to stakeholders and customers
* [**Explore ChatOps**](chatops/overview.md) - Integrate with Slack or Microsoft Teams for incident collaboration
* [**Set up heartbeat monitoring**](alerting/heartbeat-monitoring/) - Monitor connectivity to ilert for reliable incident response

## Need Help?

* **Documentation**: Browse our [comprehensive incident management guides](./)
* **Support**: Contact us at [support@ilert.com](mailto:support@ilert.com)
* **Live Chat**: Available in the ilert app

***

**Congratulations!** You've successfully set up ilert's incident management platform and are ready to respond to incidents faster and more effectively.
