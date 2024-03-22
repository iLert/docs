# Call Routing 2.0 (BETA)

{% hint style="info" %}
**Call Routing 2.0 Availability**\
Call Routing 2.0 is currently available through our Early Access Program. To request access, please contact support@ilert.com.
{% endhint %}

Call Routing 2.0 introduces a new visual call flow builder that allows you to visually construt custom call flows using pre-defined nodes, such as such as IVR Menus, PIN Code Verification, Audio Messages, Support Hours, and more to tailor the call routing logic to your specific needs.

## Create your first call flow with schedule based routing

This section outlines the steps to create a call flow that connects incoming calls to the current on-call person via an ilert [on-call schedule](../on-call-management-and-escalations/on-call-schedules/). If the on-call individual fails to respond, the call is then redirected to a designated fallback contact, in this example, Cathy Hugh.

1.  In the navigation bar, go to **Call flows** and click on **Create call flow**&#x20;

    <figure><img src="../.gitbook/assets/Screenshot 2024-03-19 at 22.22.13.png" alt=""><figcaption></figcaption></figure>
2.  Add a node by clicking on the ➕ icon and select **Route call**&#x20;

    <figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>
3.  In the **Route call** configuration, select the desired schedule and user., and save the node configuration.

    <figure><img src="../.gitbook/assets/Screenshot 2024-03-19 at 22.27.42.png" alt=""><figcaption></figcaption></figure>
4. Assign the call flow a phone number by clicking on the **Incoming call** node at the top and click on **Publish.**&#x20;

## Which node types are available and what do they do?

* **Support hours:** lets your branch based on defined [support hours](../alerting/support-hours.md). This node will add two branches `During support hours` and `Outside support hours`&#x20;
* **IVR menu:** adds up to 11 branches (`0-9`, `*`, `#`) and branches based on the callers DTMF input ("Press 1 for ...").
* **Voicemail:** lets callers leave a voicemail. Voicemails will be appended to alerts created by subsequent **Create alert** nodes. The Voicmail node adds two branches `Voicemail left` and `No voicemail left`
* **Create alert:** creates an alert in the selected alert source. The alert will be escalated according to the alert source's priority setting and escalation policy.
* **Ask for PIN code:** Asks callers to enter a PIN code and adds two branches: `Code match` and `No code match` to the  flow. You can enter multiple code PIN codes and associate each PIN code with a label (e.g. if you would like assign PIN code to indidivual customers).
* **Audio message:** Plays an audio message to the caller
* **Route call:** Connects the caller with a user.  Users can be selected directly or indirectly through a schedule. This node adds two branches to the flow `Call completed` and `No one available`

### What are the differences between the new and legacy Call Routing experience?

* With Call Routing 2.0, incoming calls do not create alerts by default. To create alerts, you need to use a **Create Alert** node in your call flow
* Call Routing 2.0 no longer relies on [escalation policies](../on-call-management-and-escalations/escalation-policies.md) to route calls. Instead, you can include users or schedules one by one
* Call Routing 2.0 allows you to build complex call flows that were not possible with legacy call routing, e.g. multi-level IVR menus, PIN codes, or multi-language call flows.

### When do I need to migrate to Call Routing 2.0?

Once Call Routing 2.0 is released from Beta and becomes generally available, current users will need to transition from their old call routing configurations to Call Routing 2.0. They will have **12 months** to complete this migration to Call Routing 2.0.

### How can I migrate my current legacy call configuration to Call Routing 2.0

The legacy call routing and new call routing will live side by side and are independent from each other. We recommend the following approach to migrate your legacy configuration to Call Routing 2.0:

1. Rebuild your legacy configuration using the new Call Flow builder. Do not assign a number yet.
2. Save your Call Flow. If you are unsure about your call flow, feel free to ask our support to double check your configuration. Send an email to suppport@ilert.com and include a link to your legacy call routing number and the call flow that you have built.
3. Once you're ready to publish your new call flow
   1. Open the edit view of your call flow
   2. Click on the **Incoming call** node and assign the phone number that you'd like to use for this call flow\
      ![](<../.gitbook/assets/image (4).png>)
   3. Click on the **Publish** button. You'll see a warning that your phone number is already being used by the legacy call routing. Click on **Save anyway**.
   4. Incoming call will now use your new call flow. \


