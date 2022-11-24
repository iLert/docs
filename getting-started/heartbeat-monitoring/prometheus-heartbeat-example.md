---
description: To ensure and monitor the uptime of your Prometheus Alert Manager
---

# Prometheus Heartbeat Example

A recipe for the Prometheus alert manager configuration to support liveness check of your alert manager using ilert's heartbeat alert sources.

Alter your **AM.yml**

```text
route:
  receiver: default
  group_by:
  - job
  routes:
  - receiver: ilert
    match:
      alertname: ilert
    repeat_interval: 1m 

receivers:
 - name: ilert
   webhook_configs:
   - url: 'https://api.ilert.com/api/v1/heartbeats/${YOUR-APIKEY}'
     send_resolved: true
```



