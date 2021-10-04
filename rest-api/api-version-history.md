---
description: >-
  This page describes changes made to the API and potential migration strategies
  if required.
---

# API Version History

## In general

We treat the API as first class part of our product and are looking foward to any customer or partner that decides to integrate with us, which is why we are taking API versioning and preventing any kind of breaks or interruptions very seriously.

We try to prevent breaking changes for our API, however sometimes these are necessary in an evolving world and product space, so in the case that we do: we will release a new version of the API.

We consider the following changes to be backwards-compatible:

* Adding new API resources
* Adding new optional request parameters to existing API methods
* Adding new properties to existing API responses
* Changing the order of properties in existing API responses

## Notable changes

### Dropping URL versions globally

While renaming incidents to alerts in October 2021 we dediced that the best way to migrate the API to the new resources and fields was to introduce a new API version, however continuing further we did not want to stick to versioning through url paths in favor of developer experience. Which is why we decided to migrate the new resources away from the version path.

#### What did we do to keep backwards compatibility?

All old resources running on `/v1/...` are still available. Meaning the new resource and fields that are now available under e.g. `/api/alert-sources` are still available in their old format under `/api/v1/alert-sources`.

#### Which migration strategy do we suggest?

Integrations that have been developed using the old API version do not have to be migrated, the v1 resources are still available. When developing new integrations however, make sure to use the new resources - which is also why we have removed any old endpoint from our API documentation.

### Renaming incidents to alerts

In September 2021 we announced that we would rename incidents to alerts. Explaining that incidents would be reborn as new entity for the next big product extension incident communication v2 and status pages. Of course this also required us to change the API resources. `/api/1/incidents` became `/api/alerts` and `/api/incidents` will hold the new entity.

#### What did we do to keep backwards compatibility?

The old incident endpoints `/api/v1/incidents` is still available and delivers the old/new incident/alert objects.

#### Which migration strategy do we suggest?

Integrations that have been developed using the old API version to not have to be migrated, the v1 resources are still available. When developing new integrations however, make sure to use the new resources. **Please also note**: that for the new API \(all resources without url versioning\) the entities might contain changed field names e.g. `AlertSource.incidentCreation` =&gt; `AlertSource.alertCreation` a few fields were subject to this change our API docs are already reflecting this change, you can find them below.

| Entity | Old key / value | New key / value |
| :--- | :--- | :--- |
| User | subscribedIncidentUpdateStates | subscribedAlertUpdateStates |
| User | subscribedIncidentUpdateNotificationTypes | subscribedAlertUpdateNotificationTypes |
| Connection | triggerTypes | All values e.g. incident-created have been renamed accordingly e.g. alert-created |
| UptimeMonitor | createIncidentAfterFailedChecks | createAlertAfterFailedChecks |
| AlertSource | incidentCreation | alertCreation |
| AlertSource | incidentPriorityRule | alertPriorityRule |
| AlertSource.supportHours | autoRaiseAlerts | autoRaiseAlerts |
| Incident -&gt; Alert | incidentKey | alertKey |
| Notification | incidentId | alertId |
| LogEntry | incidentId | alertId |
| LogEntry | logEntryType | All values e.g. IncidentLogEntry have been renamed accordingly e.g. AlertLogEntry |
| Event | incidentKey | alertKey |

### Removing XML support

In June 2020 we decided to deprecate XML support for request and response schemas, as JSON was widely preferered by our customers. We began removing support from older `/v1/...` endpoints in August 2020. XML is **not** supported in new url version-less resources as of 2021.

#### What did we do to keep backwards compatibility?

Resources containing v1 in their url that were receiving XML traffic were kept available.

#### Which migration strategy do we suggest?

We suggest to send the `accept: application/json` header and providing `content-type: application/json` while switching your clients to JSON processing.

