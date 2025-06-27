---
description: Common issues and solutions for ilert incident management platform setup and configuration.
---

# Troubleshooting Guide

This guide helps you resolve common issues when setting up and using ilert's incident management platform.

## Alert Sources

### Alerts Not Being Created

**Symptoms:**
You’ve sent an alert, but nothing appears in ilert.

**Possible Causes & Solutions:**

1. **Check for Incoming Events**
   Go to the alert source's Event Explorer and verify whether any events have been received.

   * **If events are visible**: The alert source settings may be preventing alert creation. This can happen due to:

     * Grouping settings that suppress duplicate alerts
     * Filters that block certain event types
       Review and adjust the alert source configuration as needed.
   * **No Events Showing Up?**: If you don’t see any events at all in the alert source, continue with the next steps.


2. **Incorrect API Key or Webhook URL**
   - Verify you're using the correct API key or webhook URL from your alert source
   - Check that the URL is copied completely without extra spaces

3. **Network Connectivity Issues**
   - Test connectivity: `curl -I https://api.ilert.com/api`
   - Check firewall rules and proxy settings
   - Verify DNS resolution

4. **Invalid Request Format**
   - Check the integration documentation for correct payload format
   - Verify Content-Type headers are set correctly
   - Ensure required fields are included

5. **Rate Limiting**
   - Check if you've exceeded API rate limits
   - Implement exponential backoff in your integration

### Alerts not being resolved automatically

**Symptoms:** Alerts remain open even after the issue is fixed.

**Solutions:**
- Verify your monitoring tool sends resolve events, e.g. check that `send_resolved: true` is configured (for Prometheus)
- Ensure the same `alertKey` is used for both alert and resolve events

## Notifications

### Not receiving notifications

**Symptoms:** Alerts are created but you don't get notified.

**Possible Causes & Solutions:**

First, check the alert's timeline for notification entries. If there are no notification entries, check the following steps:

1. **Notification Settings**
   - Check your [notification settings](../../alerting/notification-settings/README.md)
   - Verify your phone number is correct and verified
   - Ensure notification rules are configured properly

2. **Escalation Policy**
   - Verify you're included in the escalation policy
   - Check that the escalation policy is assigned to the alert source
   - Ensure you're on-call if using schedules

3. **Support Hours**
   - Check if support hours are configured and you're within them
   - Verify notification priority settings

4. **Mobile App Issues**
   - Reinstall the mobile app
   - Check device notification settings
   - Verify push notification permissions

### SMS/Phone calls not working

**Symptoms:** You receive email/push notifications but not SMS or calls.

**Solutions:**
- Verify your phone number is correct and verified
- Check your country's SMS/voice support
- Ensure you haven't exceeded SMS/voice limits (Free plan)
- Test with a different phone number

## Mobile App

### App not working

**Symptoms:** App crashes, won't load, or can't connect.

**Solutions:**
- Update to the latest version
- Clear app cache and data
- Check internet connectivity
- Reinstall the app

### Push notifications not working

**Symptoms:** You don't receive push notifications on mobile.

**Solutions:**
- Check device notification settings
- Verify app has notification permissions
- Enable critical alerts (iOS)
- Check Do Not Disturb settings

## Performance Issues

### Slow response times

**Symptoms:** Dashboard loads slowly or API calls are slow.

**Solutions:**
- Check your internet connection
- Clear browser cache
- Try a different browser or device
- Contact support if issues persist

### High alert volume

**Symptoms:** Too many alerts causing notification fatigue.

**Solutions:**
- Configure [alert grouping](../../alerting/alert-sources.md#alert-grouping)
- Set up [event filters](../../alerting/alert-sources.md#event-filter)
- Use [support hours](../../alerting/support-hours.md)
- Implement [notification priority](../../alerting/alert-sources.md#notification-priority-and-support-hours)

## API Issues

### Authentication errors

**Symptoms:** API calls return 401 or 403 errors.

**Solutions:**
- Verify API key is correct and active
- Check API key permissions
- Ensure proper Authorization header format
- Contact support to verify account status

### Rate limiting

**Symptoms:** API calls return 429 errors.

**Solutions:**
- Implement exponential backoff
- Reduce request frequency
- Check rate limit headers
- Consider upgrading your plan

## Getting Help

### Before contacting support

1. **Check this troubleshooting guide**
2. **Review the relevant documentation**
3. **Test with a simple example**
4. **Gather relevant logs and error messages**

### Contacting support

When contacting support, include:

- **Error messages** and logs
- **Steps to reproduce** the issue
- **Expected vs actual behavior**
- **Environment details** (browser, OS, etc.)
- **Screenshots** if applicable

**Support Channels:**
- **Email:** [support@ilert.com](mailto:support@ilert.com)
- **Live Chat:** Available in the ilert dashboard