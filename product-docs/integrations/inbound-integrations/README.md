# Inbound integrations

Inbound integrations, or [alert sources](https://docs.ilert.com/alerting/alert-sources), refer to the process of receiving events from external systems, like monitoring, observability, or ticketing solutions, into ilert. ilert provides more than 100 integrations with third-party tools in its catalog to ensure reliable incident alerting. If you haven't found a tool you regularly use and want to connect with ilert, contact our [support team](mailto:support@ilert.com).

## Integration Categories

### 🔍 **Monitoring & Observability**

Connect your monitoring tools to get reliable alerts when metrics exceed thresholds or services go down.

**Popular Integrations:**

* [Prometheus](prometheus.md) - Open-source monitoring and alerting
* [Amazon CloudWatch](amazon-cloudwatch.md) - AWS monitoring service
* [Datadog](datadog.md) - Cloud monitoring and analytics
* [New Relic](new-relic/) - Application performance monitoring
* [Grafana](grafana/) - Metrics visualization and alerting

### 🚨 **Uptime Monitoring**

Monitor website and service availability from multiple locations for comprehensive incident coverage.

**Popular Integrations:**

* [Pingdom](pingdom.md) - Website monitoring
* [UptimeRobot](uptime-robot.md) - Free uptime monitoring
* [StatusCake](statuscake.md) - Website monitoring and testing
* [Hyperping](hyperping.md) - Real-time uptime monitoring

### 🛡️ **Security & Compliance**

Get alerted about security threats and compliance violations for proactive incident response.

**Popular Integrations:**

* [AWS GuardDuty](guardduty.md) - AWS threat detection
* [Azure Sentinel](azure-alerts/sentinel.md) - Microsoft security information
* [CrowdStrike](crowdstrike.md) - Endpoint protection
* [Google Security Command Center](google-security-command-center.md) - Google Cloud security

### 🐛 **Application Monitoring**

Monitor application errors, performance issues, and user experience for reliable incident management.

**Popular Integrations:**

* [Sentry](sentry.md) - Error tracking and performance monitoring
* [Rollbar](rollbar.md) - Error monitoring and debugging
* [Raygun](raygun.md) - Crash reporting and performance monitoring
* [AppSignal](appsignal.md) - Application performance monitoring

### 🎫 **Ticketing & ITSM**

Connect your ticketing systems to create tickets automatically from incidents for streamlined incident response.

**Popular Integrations:**

* [Jira](jira.md) - Issue and project tracking
* [ServiceNow](service-now.md) - IT service management
* [Zendesk](zendesk.md) - Customer service platform
* [FreshService](freshservice.md) - IT service desk

### ☁️ **Cloud Platforms**

Monitor cloud infrastructure and services for comprehensive incident coverage.

**Popular Integrations:**

* [Azure Alerts](azure-alerts/) - Microsoft Azure monitoring
* [Google Cloud Monitoring](google-stackdriver.md) - Google Cloud monitoring
* [Alibaba Cloud](alibaba-cloud.md) - Alibaba Cloud monitoring

## Integration Types

### 1. **Pre-built Integrations**

Most tools have dedicated integration pages with step-by-step setup instructions. These provide the best experience with automatic field mapping and alert grouping for reliable incident management.

### 2. **Email Integration**

Forward emails to ilert to create alerts. Useful for tools that don't have webhook support.

[**Learn more →**](email/)

### 3. **Event API**

Use our REST API to send custom events and alerts programmatically for flexible incident management.

[**Learn more →**](https://api.ilert.com/api-docs/#tag/Events)

### 4. **SMS Integration**

Send incidents to ilert via SMS for tools that support SMS notifications.

### 5. **Heartbeat Monitoring**

Monitor connectivity between your infrastructure and ilert for reliable incident response.

[**Learn more →**](../../alerting/heartbeat-monitoring/)

## Getting Started

1. **Choose your integration** from the categories above
2. **Follow the setup guide** for your specific tool
3. **Test the integration** by sending a test alert
4. **Configure alert grouping** to reduce noise and improve incident management
5. **Set up escalation policies** to route incidents to the right people for reliable incident response

## Need Help?

* **Missing an integration?** Contact us at [support@ilert.com](mailto:support@ilert.com)
* **Setup issues?** Check our [FAQ](../../getting-started/faq/)
* **Custom integration?** Use our [Event API](https://api.ilert.com/api-docs/#tag/Events)
