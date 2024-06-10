# ➿ ITL - ilert template language

In the UI's text mode you may use the **Insert data...** dropdown to help you add template variables quickly - the text syntax works like this:

<table><thead><tr><th width="203">Type</th><th width="351.3333333333333">Sample</th><th>Description</th></tr></thead><tbody><tr><td>Text</td><td>Some text</td><td>You may of course add generic text content to your liking</td></tr><tr><td>Variable</td><td><strong><code>{{</code></strong><code>var</code><strong><code>}}</code></strong></td><td>Extract content of the event and insert it. Note: there is no further sanitizing of the values</td></tr><tr><td>Accessing nested variables</td><td><code>{{ var</code><strong><code>.</code></strong><code>subfield</code><strong><code>.</code></strong><code>evenMore }}</code></td><td>Access sub fields</td></tr><tr><td>Accessing fields of an array</td><td><code>{{ var.arrayField</code><strong><code>[0]</code></strong><code>.more }}</code></td><td>Access array contents</td></tr><tr><td>Applying functions to variables</td><td>{{<code>var.lowerCase}}</code></td><td></td></tr><tr><td>Passing arguments to functions</td><td><code>{{var.splitTakeAt('one two', 10)}}</code></td><td></td></tr></tbody></table>





{% hint style="info" %}
This page is WIP we are working on an improved template experience
{% endhint %}
