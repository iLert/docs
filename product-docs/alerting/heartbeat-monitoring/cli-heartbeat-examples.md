---
description: Command line interface heartbeat examples
---

# CLI Heartbeat Examples

## Simple Heartbeat

Simple heartbeat call using curl

```
curl https://api.ilert.com/api/v1/heartbeats/${YOUR-APIKEY}
```

## Cronjob Backup

Heartbeat after successful backup script cronjob execution

```
run_backup.sh && curl https://api.ilert.com/api/v1/heartbeats/${YOUR-APIKEY}

```

