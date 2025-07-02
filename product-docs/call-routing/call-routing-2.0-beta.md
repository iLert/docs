---
description: Use intuitive call flow builder and create routing logic of any complexity.
---

# Routing calls using call flows

Call Routing 2.0 introduces a new visual call flow builder that allows you to visually construct custom call flows using pre-defined nodes, such as IVR Menus, PIN Code Verification, Audio Messages, Support Hours, and more to tailor the call routing logic to your specific needs.

{% embed url="https://www.youtube.com/watch?v=SA_F1p2bGDU" %}
[https://www.youtube.com/@ilertVideos](https://www.youtube.com/@ilertVideos)
{% endembed %}

### Create your first call flow with schedule-based routing

This section outlines the steps to create a call flow that connects incoming calls to the current on-call person via an ilert [on-call schedule](../on-call-management-and-escalations/on-call-schedules/). If the on-call individual fails to respond, the call is then redirected to a designated fallback contact, in this example, Cathy Hugh.

1.  In the navigation bar, go to **Call flows** and click on **Create call flow.**

    <figure><img src="../.gitbook/assets/Screenshot 2024-03-19 at 22.22.13.png" alt=""><figcaption></figcaption></figure>
2.  Add a node by clicking on the ➕ icon and select **Route call**.&#x20;

    <figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>
3.  In the **Route call** configuration, select the desired schedule and user and save the node configuration.

    <figure><img src="../.gitbook/assets/Screenshot 2024-03-19 at 22.27.42.png" alt=""><figcaption></figcaption></figure>
4. Assign the call flow a phone number by clicking the **Incoming call** node at the top and clicking **Publish.**&#x20;

### Which node types are available, and what do they do?

* **Support hours:** enables your branch to be based on defined [support hours](../alerting/support-hours.md). This node will add two branches: `During support hours` and `Outside support hours`.
* **IVR menu:** adds up to 11 branches (`0-9`, `*`, `#`) and branches based on the callers' DTMF input ("Press 1 for ...").
* **Voicemail:** lets callers leave a voicemail. Voicemails will be appended to alerts created by subsequent **Create alert** nodes. The Voicemail node adds two branches: `Voicemail left` and `No voicemail left`.
* **Create alert:** creates an alert in the selected alert source. The alert will be escalated according to the alert source's priority setting and escalation policy.
* **Ask for PIN code:** Asks callers to enter a PIN code and adds two branches: `Code match` and `No code match` to the flow. You can enter multiple PIN codes and associate each PIN code with a label (e.g. if you would like to assign a PIN code to individual customers).
* **Audio message:** Plays an audio message to the caller
* **Route call:** Connects the caller with a user.  Users can be selected directly or indirectly through a schedule. This node adds two branches to the flow: `Call completed` and `No one available`.
* **Block numbers:** Enables ilert users to create blacklists and reject calls from specific numbers.
* **AI Voice Agent (Beta)**: A human-like agent for natural conversations and intelligent routing. The Agent handles the first communication with callers, processes the information provided, and, depending on the input, creates an incident or calls an on-duty engineer.

{% hint style="info" %}
ilert hotlines can **forward calls directly to external support numbers, even if they use IVR menus—no confirmation needed from the other end**. This feature ensures smooth call handoffs without requiring manual workarounds or dedicated ilert users. It’s a simple way to connect your callers with third-party support while keeping your workflows clean and efficient.
{% endhint %}

### **Use ilert AI to turn text into speech**

Make your automatic call routing responses sound human-like. Choose one of the available voice options from the dropdown menu at the top of the call flow editor. The chosen voice will be applied to all the nodes.&#x20;

<figure><img src="../.gitbook/assets/ilert call flow voice choice.png" alt=""><figcaption></figcaption></figure>

### Quick actions with nodes and subtrees

<figure><img src="../.gitbook/assets/ilert call flow quick actions.png" alt="ilert call flow quick actions"><figcaption></figcaption></figure>

&#x20;Each node has a menu of actions to simplify the editing process. Click a three-dot icon in front of the node; you will see the following actions:

* Copy node
* Copy subtree
* Cut subtree

These actions are especially useful for complex scenarios with many branches.&#x20;

### FAQ

#### _Question: What are the differences between the new and legacy Call Routing?_

Call Routing 2.0 introduces a radical transformation in how call flows are created and managed compared to legacy call routing. Here's an overview of the key differences:

_Call Flow Design_

* Legacy Call Routing implemented a static call flow design, typically following a linear sequence: Greeting -> IVR Menu -> Voicemail.
* Call Routing 2.0 offers a dynamic and visual interface for building call flows. This flexibility allows for the design of complex scenarios, including multi-level IVR menus and multi-language call flows.

_Nodes and Features_

* Legacy Call Routing lacked the versatility in customizing call flows beyond the basic configurations.
* Call Routing 2.0 introduces nodes, a set of new features that expand functionality. For example, the "Ask for PIN code" node adds an extra layer of security by requiring callers to enter a PIN code.

_Alert Creation_

* In Legacy Call Routing, incoming calls might automatically generate alerts based on predefined conditions.
* Call Routing 2.0 changes this approach by not creating alerts by default. Instead, it employs a Create Alert node within the call flow to generate alerts, offering more control over when and how alerts are created.

_Alert Acknowledgement_

* In Legacy Call Routing the related alert was automatically accepted by the first agent to answer and confirm the call.
* As described in "_Alert Creation_" above, Call Routing 2.0 does not create an alert by default and it also does not track the agent answer to this alert by default - however, due to many customers asking, we have introduced a feature that you can enable on the Create alert node to automatically accept the alert on any agent answer to replicate the legacy behaviour.

_Use of Escalation Policies_

* Legacy Call Routing was somewhat restrictive in including users or schedules into call flows and required you to use [escalation policies](../on-call-management-and-escalations/escalation-policies.md).&#x20;
* Call Routing 2.0 simplifies this process, allowing for the direct inclusion of users or schedules, facilitating a more streamlined approach to call routing based on schedules or static user rules.

In summary, Call Routing 2.0 provides a more adaptable, feature-rich platform for call flow management, moving away from the limitations of our old call routing to embrace flexibility, enhanced security, and improved user experience.

####

#### _Question: When do I need to migrate to Call Routing 2.0?_

Upon the general availability release of Call Routing 2.0, existing users must transition from their previous call routing setups to the new version. This migration must be completed within **12 months** of the release date.

####

#### _Question: How to migrate an existing phone number to the new call routing?_

Follow the steps below to seamlessly transition your incoming call routing to the new Call Routing 2.0:

_Prepare your new call flow_

1. Rebuild your legacy configuration using the new Call Flow builder. Do not assign a phone number to it yet. Save your Call Flow by clicking the **Save** button in the top right.
2. (Optional) If you need assistance, our support team is here to help. Email suppport@ilert.com with a link to your legacy routing number and the call flow you've created for a review.

_Publish your call flow_

1. Once your Call Flow is ready, assign a phone number to it. Click on the Incoming call node within your Call Flow and select the number you'd like to use:\
   ![](<../.gitbook/assets/image (15).png>)
2. Publish your call flow by clicking on the **Publish** button.&#x20;
3. A warning will appear if the phone number is already in use by the legacy routing system. Proceed by clicking **Publish anyway**.
4. Incoming calls will now use your new call flow.&#x20;



