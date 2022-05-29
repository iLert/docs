# Incidents

## What is an incident?

Incidents are the main way to communicate with your users when you are experiencing user impacting issues with the services you provide to them. Incidents in iLert are specifically designed for the purpose of communicating with your users, as opposed to e.g. alerting on-call teams.

An incident has one or more affected services and will be

* posted an all status pages that contain at least one of the affected services
* and will be communicated to all subscribers of either the status page or the service
* and additionally inform subscribers that were manually added to the incident

### Incidents vs alerts

* An alert in iLert is primarily targeted towards on-call responders and notifies them about potential incidents reported by monitoring, ticketing tools, or any other observability tool.&#x20;
* Alerts are technical in nature and often contain technical details that are not relevant to non-technical users
* An incident in iLert is the primary way to communicate with non-technical users and they are designed exactly for that purpose.

## Create and communicate incidents

There are 3 ways to create an incident

1. Automatically when an alert is created through [automation rules](services.md#automation-with-alert-sources) of a service
2. Manually from the **New incident** page
3. Manually from a pending alert

To manually create an incident

1. Go to **Incidents** and click on the **Create incident** button&#x20;
2. Enter the incident summary and select the incident status
3. Optionally a message to include in the incident update
4. Select the services that are affected by this incident along with their impact level. At least one service must be selected in order to create an incident.
5. Select whether to send notifications about this incident. Enabling **Notify subscribers about this incident**, will notify all users
   * that are subscribed to any of the affected services and
   * that are subscribed to status pages where any of the affected service is included
6. Click **Create incident**. You will see a preview of how many subscribers will be notified and on how many status pages the incident will be posted. ****&#x20;

## Incident templates

Create incident templates to&#x20;

* use as a starting point when manually creating incidents
* to automatically create incidents using [alert source automation rules](services.md#automation-with-alert-sources)

During incident creation, you will be able to select from your templates as seen below:

![](<../.gitbook/assets/Screenshot 2022-01-08 at 00.20.19.png>)

Once you select a template, all fields will be pre-filled using the values from the template.

### Create an incident template <a href="#create-an-incident-template" id="create-an-incident-template"></a>

1. Go to **Incidents** and click on the **Incidents templates** tab
2. Click on **Create new template**
3. Give the template a name and fill out the fields that you would like to have pre-filled when creating an incident
4. Click **Create template**

### Using alert placeholders in incident templates <a href="#use-an-incident-template" id="use-an-incident-template"></a>

When an incident is created from an alert (**using alert source automation rules**), the placeholder variables will be substituted with their corresponding values.

The following variables are available for substitution:

| Variable               | Description                                                                                                                                                                                                                                |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `serviceId`            | The id of the service that is affected                                                                                                                                                                                                     |
| `serviceName`          | The name of the service that is affected                                                                                                                                                                                                   |
| `serviceDescription`   | The description of the service that is affected                                                                                                                                                                                            |
| `serviceStatus`        | The statu of the service that is affected                                                                                                                                                                                                  |
| `teamNames`            | A comma separated list of team names. This corresponds to the same value that is shown in the teams field of an incident and is resolved by traversing the ownerships of the affected service and the alert source that created the alert. |
| `alertId`              | The id of the alert that triggered this incident                                                                                                                                                                                           |
| `alertDetails`         | The details of the alert that triggered this incident                                                                                                                                                                                      |
| `alertSummary`         | The summary of the alert that triggered this incident                                                                                                                                                                                      |
| `alertStatus`          | The status of the alert that triggered this incident                                                                                                                                                                                       |
| `alertPriority`        | The priority of the alert that triggered this incident                                                                                                                                                                                     |
| `alertSourceId`        | The id of the alert source of the alert that triggered this incident                                                                                                                                                                       |
| `alertSourceName`      | The name of the alert source of the alert that triggered this incident                                                                                                                                                                     |
| `escalationPolicyId`   | The id of the escalation policy of the alert that triggered this incident                                                                                                                                                                  |
| `escalationPolicyName` | The name of the escalation policy of the alert that triggered this incident                                                                                                                                                                |

