# Generating incidents using AI

This ilert AI feature helps you to generate contentful incidents quickly, even if your mind is somewhere else while you are in fire fighting mode working on resolving the issue that caused the incident in the first place. It can be hard and take way longer than usual to fill out a proper summary and details for the incident, when you are under stress.

The feature makes a smart guess on to which services should be included in the context of the generative AI, making this feature work as much privacy preserving as possible while also working for customers with a large amount of services.

<figure><img src="../.gitbook/assets/ilert_ai_incident_creation.gif" alt=""><figcaption></figcaption></figure>

### What kind of data is shared?

* Service **name**s for a small selection of services that ilert AI chooses based on the relation to the prompt or the context of the user entering the prompt e.g. services owned by related teams, no other service data is shared.
* The entered **summary** content is used as prompt.

### What model is used?

<table><thead><tr><th>Model</th><th width="200.66666666666669">Vendor</th><th data-type="checkbox">Available for this use case</th><th>Info</th></tr></thead><tbody><tr><td>il-LLaMA-1</td><td>ilert</td><td>true</td><td>ALPHA</td></tr><tr><td>il-ludwig-rnn-2</td><td>ilert</td><td>false</td><td></td></tr><tr><td>gpt-4</td><td>OpenAI</td><td>true</td><td>BETA</td></tr><tr><td>gpt-3.5-turbo</td><td>OpenAI</td><td>true</td><td>default</td></tr><tr><td>text-davinci-003</td><td>OpenAI</td><td>true</td><td>deprecated</td></tr></tbody></table>

