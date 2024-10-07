# Routing calls using call flows

Call Routing 2.0 introduces a new visual call flow builder that allows you to visually construct custom call flows using pre-defined nodes, such as IVR Menus, PIN Code Verification, Audio Messages, Support Hours, and more to tailor the call routing logic to your specific needs.

{% embed url="https://www.youtube.com/watch?v=SA_F1p2bGDU" %}
[https://www.youtube.com/@ilertVideos](https://www.youtube.com/@ilertVideos)
{% endembed %}

## Create your first call flow with schedule based routing

This section outlines the steps to create a call flow that connects incoming calls to the current on-call person via an ilert [on-call schedule](../on-call-management-and-escalations/on-call-schedules/). If the on-call individual fails to respond, the call is then redirected to a designated fallback contact, in this example, Cathy Hugh.

1.  In the navigation bar, go to **Call flows** and click on **Create call flow**&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2024-03-19 at 22.22.13.png" alt=""><figcaption></figcaption></figure>
2.  Add a node by clicking on the ➕ icon and select **Route call**.&#x20;

    <figure><img src="../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>
3.  In the **Route call** configuration, select the desired schedule and user and save the node configuration.

    <figure><img src="../.gitbook/assets/Screenshot 2024-03-19 at 22.27.42.png" alt=""><figcaption></figcaption></figure>
4. Assign the call flow a phone number by clicking the **Incoming call** node at the top and clicking **Publish.**&#x20;

## Which node types are available, and what do they do?

* **Support hours:** enables your branch be based on defined [support hours](../alerting/support-hours.md). This node will add two branches: `During support hours` and `Outside support hours`.
* **IVR menu:** adds up to 11 branches (`0-9`, `*`, `#`) and branches based on the callers' DTMF input ("Press 1 for ...").
* **Voicemail:** lets callers leave a voicemail. Voicemails will be appended to alerts created by subsequent **Create alert** nodes. The Voicemail node adds two branches: `Voicemail left` and `No voicemail left`.
* **Create alert:** creates an alert in the selected alert source. The alert will be escalated according to the alert source's priority setting and escalation policy.
* **Ask for PIN code:** Asks callers to enter a PIN code and adds two branches: `Code match` and `No code match` to the flow. You can enter multiple PIN codes and associate each PIN code with a label (e.g. if you would like to assign a PIN code to individual customers).
* **Audio message:** Plays an audio message to the caller
* **Route call:** Connects the caller with a user.  Users can be selected directly or indirectly through a schedule. This node adds two branches to the flow: `Call completed` and `No one available`.

{% hint style="info" %}
💡 **Helpful Tip: Use ilert AI to turn text into speech.**

Make your automatic call routing responses sound human-like. Type your message and choose one of six available voice options from the dropdown menu. Click ▶️ to preview the message.

<img src="../.gitbook/assets/Call Flow AI TTS high rez.gif" alt="" data-size="original">
{% endhint %}

## FAQ

### What are the differences between the new and legacy Call Routing?

Call Routing 2.0 introduces a radical transformation in how call flows are created and managed compared to legacy call routing. Here's an overview of the key differences:

#### Call Flow Design

* **Legacy Call Routing** implemented a static call flow design, typically following a linear sequence: Greeting -> IVR Menu -> Voicemail.
* **Call Routing 2.0** offers a dynamic and visual interface for building call flows. This flexibility allows for the design of complex scenarios, including multi-level IVR menus and multi-language call flows.

#### Nodes and Features

* **Legacy Call Routing** lacked the versatility in customizing call flows beyond the basic configurations.
* **Call Routing 2.0** introduces nodes, a set of new features that expand functionality. For example, the "Ask for PIN code" node adds an extra layer of security by requiring callers to enter a PIN code.

#### Alert Creation

* In **Legacy Call Routing**, incoming calls might automatically generate alerts based on predefined conditions.
* **Call Routing 2.0** changes this approach by not creating alerts by default. Instead, it employs a **Create Alert** node within the call flow to generate alerts, offering more control over when and how alerts are created.

#### Use of Escalation Policies

* **Legacy Call Routing** was somewhat restrictive in including users or schedules into call flows and required you to use [escalation policies](../on-call-management-and-escalations/escalation-policies.md).&#x20;
* **Call Routing 2.0** simplifies this process, allowing for the direct inclusion of users or schedules, facilitating a more streamlined approach to call routing based on schedules or static user rules.

In summary, Call Routing 2.0 provides a more adaptable, feature-rich platform for call flow management, moving away from the limitations of our old call routing to embrace flexibility, enhanced security, and improved user experience.

### When do I need to migrate to Call Routing 2.0?

Upon the general availability release of Call Routing 2.0, existing users must transition from their previous call routing setups to the new version. This migration must be completed within **12 months** of the release date.

### How to migrate an existing phone number to the new call routing?

Follow the steps below to seamlessly transition your incoming call routing to the new Call Routing 2.0:

**Prepare your new call flow**

1. Rebuild your legacy configuration using the new Call Flow builder. Do not assign a phone number to it yet. Save your Call Flow by clicking the **Save** button in the top right.
2. (Optional) If you need assistance, our support team is here to help. Email suppport@ilert.com with a link to your legacy routing number and the call flow you've created for a review.

**Publish your call flow**

1. Once your Call Flow is ready, assign a phone number to it. Click on the Incoming call node within your Call Flow and select the number you'd like to use:\
   ![](<../.gitbook/assets/image (4) (1).png>)
2. Publish your call flow by clicking on the **Publish** button.&#x20;
3. A warning will appear if the phone number is already in use by the legacy routing system. Proceed by clicking **Publish anyway**.
4. Incoming calls will now use your new call flow.&#x20;

### &#x20;

