# Generating incident updates through AI

Similar to the generation of fresh incidents this ilert AI feature helps you to create an incident update while you are under stress in fire fighting mode or as a quick hands on resolve message generation if you just want to quickly close an incident properly while addressing all affected services.

<figure><img src="../.gitbook/assets/ilert_ai_incident_update.gif" alt=""><figcaption></figcaption></figure>

### What kind of data is shared?

* Service **name**s of all services the current incident has affected in the past. No other service data is shared.
* The entered **message** content is used as prompt.
* The current **status** of the incident.

### What model is used?

<table><thead><tr><th>Model</th><th width="200.66666666666669">Vendor</th><th width="122" data-type="checkbox">Available for this use case</th><th>Info</th></tr></thead><tbody><tr><td>il-LLaMA-1</td><td>ilert</td><td>true</td><td>ALPHA</td></tr><tr><td>ludwig-rnn-2</td><td>ilert</td><td>false</td><td></td></tr><tr><td>gpt-4</td><td>OpenAI</td><td>false</td><td></td></tr><tr><td>gpt-3.5-turbo-0xxx</td><td>OpenAI</td><td>true</td><td>default</td></tr><tr><td>davinci-03</td><td>OpenAI</td><td>true</td><td>deprecated</td></tr></tbody></table>

