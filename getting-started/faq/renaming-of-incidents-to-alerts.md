# Renaming of Incidents to Alerts

We are renaming **Incidents** to **Alerts**. This change is fully backwards-compatible and will mainly affect our web and app user interfaces. No actions are required on your part.

### Why are we making this change?

We're doing this in preparation for upcoming changes to how our [stakeholder communication](broken-reference) feature works in iLert. Currently, incidents in iLert are usually created by monitoring or ticketing tools.  On-call teams are notified about incidents and once a responder acknowledges an incident, they can add stakeholders to it to inform them that the incident likely has an impact on their business area. \
\
This approach has several shortcomings:

* Incidents created by monitoring tools often contain technical details that are not relevant to non-technical stakeholders. Although you can change the summary of an incident, stakeholders can still be overwhelmed by the amount of information displayed in an incident. There are images from monitoring tools, links to external sources, dozens of log entries, comments from team members, etc.
* Stakeholder updates are currently hidden in the comments section of an incident and displayed along with other comments between team members.
* You cannot use pre-defined incident templates for incident communication

Therefore, we will rename incidents to what they really are: alerts! An alert is primarily targeted towards on-call responders and notifies them about potential incidents reported by monitoring or ticketing tools.&#x20;

But wait, this doesn't solve the aforementioned problems, you might think... Renaming will be the first step. In the next months, we will roll out several features to improve incident communication in iLert.&#x20;

Among other things, we will introduce ...

* **incidents** that are specifically designed for the purpose of communicating with your stakeholders
* **services** that are meant to model business capabilities and to which stakeholders can subscribe to receive updates.&#x20;
* **status pages** that help you inform stakeholders and users about outages and maintenances

### When will this change happen?

Starting Friday, Sep 17th, 2021, and for the following 7 days, we will gradually apply the renaming in different parts of our software, including our mobile apps, web UI, reporting UI and API.

### How will this affect our APIs?

Our APIs will remain fully backwards compatible. We will deprecate our current `/incidents` end point and introduce a new `/alerts` end point.

Once we start releasing the above features, we might introduce another version of our API.
