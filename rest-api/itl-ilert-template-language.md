# ➿ ITL - ilert template language

The ITL enables you to customize and design alerts tailored to your specific use cases. In addition to offering flexibility in formatting and structuring alerts, it also provides a variety of built-in functions to further enhance the alerts' readablility.

In the UI's text mode, you may use the **Insert data...** dropdown to help you add template variables quickly—the text syntax works like this:

<table><thead><tr><th width="203">Type</th><th width="351.3333333333333">Sample</th><th>Description</th></tr></thead><tbody><tr><td>Text</td><td>Some text</td><td>You may, of course, add generic text content to your liking.</td></tr><tr><td>Variable</td><td><strong><code>{{</code></strong><code>var</code><strong><code>}}</code></strong></td><td>Extract content of the event and insert it. Note: there is no further sanitizing of the values.</td></tr><tr><td>Accessing nested variables</td><td><code>{{ var</code><strong><code>.</code></strong><code>subfield</code><strong><code>.</code></strong><code>evenMore }}</code></td><td>Access sub fields</td></tr><tr><td>Accessing fields of an array</td><td><code>{{ var.arrayField</code><strong><code>[0]</code></strong><code>.more }}</code></td><td>Access array contents</td></tr><tr><td>Applying functions to variables</td><td><code>{{var.lowerCase()}}</code></td><td></td></tr><tr><td>Passing arguments to functions</td><td><code>{{var.splitTakeAt("one two", 10)}}</code></td><td>We are in the process of reworking function calling in templates.</td></tr></tbody></table>



## Functions

ITL allows you to apply functions for different use cases, such as string manipulation, date-time formatting, joining arrays, and mustache conditions and loops. This flexibility makes it simple to handle text formatting, data extraction, and transformations, all within the same template.



### Descriptions

<table data-full-width="false"><thead><tr><th>Function</th><th>Description</th><th>Parameters</th></tr></thead><tbody><tr><td>substring</td><td>Displays characters from the given start index(1) to the specified end index(2). (It is required to provide at least one parameter.)</td><td>substring(<strong>Integer(1)</strong>)<br><br>substring(<strong>Integer(1)</strong>, <strong>Integer(2)</strong>)</td></tr><tr><td>lowerCase</td><td>Displays characters in lower case.</td><td></td></tr><tr><td>upperCase</td><td>Displays characters in upper case.</td><td></td></tr><tr><td>replaceAll</td><td>Replaces each of a given character sequence(1) with a new sequence(2).</td><td>replaceAll(<strong>String(1)</strong>, <strong>String(2)</strong>)</td></tr><tr><td>splitTakeAt</td><td>Divides a string into an array of substrings based on a character sequence as the delimiter. </td><td>splitTakeAt(<strong>String(1)</strong>, <strong>Integer(2)</strong>)</td></tr><tr><td>startsWithTake</td><td>Matches a given character sequence(1) with the start of a variable's value and replaces it with a different character sequence(2) if it matches.</td><td>startsWithTake(<strong>String(1)</strong>, <strong>String(2)</strong>)</td></tr><tr><td>equalsTake</td><td>Matches a given character sequence(1) with a variable's value and replaces it with a different character sequence(2) if it matches.</td><td>equalsTake(<strong>String(1)</strong>, <strong>String(2)</strong>)</td></tr><tr><td>endsWithTake</td><td>Matches a given character sequence(1) with the end of a variable's value and replaces it with a different character sequence(2) if it matches.</td><td>endsWithTake(<strong>String(1)</strong>, <strong>String(2)</strong>)</td></tr><tr><td>containsTake</td><td>Replaces a variable's value with a character sequence(2) if it contains a given character sequence(1).</td><td>containsTake(<strong>String(1)</strong>, <strong>String(2)</strong>)</td></tr><tr><td>startsWithTakeOrDrop</td><td>Matches a given character sequence(1) with the start of a variable's value and replaces it with a different character sequence(2) if it matches; otherwise, it does not display anything.</td><td>startsWithTakeOrDrop(<strong>String(1)</strong>, <strong>String(2)</strong>)</td></tr><tr><td>equalsTakeOrDrop</td><td>Matches a given character sequence(1) with a variable's value and replaces it with a different character sequence(2) if it matches; otherwise, it does not display anything.</td><td>equalsWithTakeOrDrop(<strong>String(1)</strong>, <strong>String(2)</strong>)</td></tr><tr><td>endsWithTakeOrDrop</td><td>Matches a given character sequence(1) with the end of a variable's value and replaces it with a different character sequence(2) if it matches; otherwise, it does not display anything.</td><td>endsWithTakeOrDrop(<strong>String(1)</strong>, <strong>String(2)</strong>)</td></tr><tr><td>containsTakeOrDrop</td><td>Replaces a variable's value with a character sequence(2) if it contains a given character sequence(1); otherwise, it does not display anything.</td><td>containsTakeOrDrop(<strong>String(1)</strong>, <strong>String(2)</strong>)</td></tr><tr><td>startsWithElse</td><td>Matches a given character sequence(1) with the start of a variable's value and replaces it with a different character sequence(2) if it doesn't match.</td><td>startsWithElse(<strong>String(1)</strong>, <strong>String(2)</strong>)</td></tr><tr><td>equalsElse</td><td>Matches a given character sequence(1) with the variable's value and replaces it with a different character sequence(2) if it doesn't match.</td><td>equalsElse(<strong>String(1)</strong>, <strong>String(2)</strong>)</td></tr><tr><td>endsWithElse</td><td>Matches a given character sequence(1) with the end of a variable's value and replaces it with a different character sequence(2) if it doesn't match.</td><td>endsWithElse(<strong>String(1)</strong>, <strong>String(2)</strong>)</td></tr><tr><td>containsElse</td><td>Replaces a variable's value with a character sequence(2) if it doesn't contain a given character sequence(1).</td><td>containsElse(<strong>String(1)</strong>, <strong>String(2)</strong>)</td></tr><tr><td>startsWithElseOrDrop</td><td>Matches a given character sequence(1) with the start of a variable's value and replaces it with a different character sequence(2) if it doesn't match; otherwise, it does not display anything.</td><td>startsWithElseOrDrop(<strong>String(1)</strong>, <strong>String(2)</strong>)</td></tr><tr><td>equalsElseOrDrop</td><td>Matches a given character sequence(1) with the variable's value and replaces it with a different character sequence(2) if it doesn't match; otherwise, it does not display anything.</td><td>equalsElseOrDrop(<strong>String(1)</strong>, <strong>String(2)</strong>)</td></tr><tr><td>endsWithElseOrDrop</td><td>Matches a given character sequence(1) with the end of a variable's value and replaces it with a different character sequence(2) if it doesn't match; otherwise, it does not display anything.</td><td>endsWithElseOrDrop(<strong>String(1)</strong>, <strong>String(2)</strong>)</td></tr><tr><td>containsElseOrDrop</td><td>Matches a given character sequence(1) with a variable's value and replaces it with a different character sequence(2) if it doesn't match; otherwise, it does not display anything.</td><td>containsElseOrDrop(<strong>String(1)</strong>, <strong>String(2)</strong>)</td></tr><tr><td>formatUnixMs</td><td><p>Formats a variable's value from milliseconds into <a href="https://www.iso.org/iso-8601-date-and-time-format.html">ISO-8601</a> date-time format. Additionally, it accepts a format style character (1) as a parameter.<br><br>Valid format characters are: </p><ul><li>F: Full text style (Sunday, January 29, 2023 at 12:05:37 AM Coordinated Universal Time)</li><li>L: Long text style(January 29, 2023 at 12:05:37 AM UTC)</li><li>M: Medium text style(Jan 29, 2023, 12:05:37 AM)</li><li>S: Short text style(1/29/23, 12:05 AM)</li></ul><p>Any other character will lead to medium text style as default.</p></td><td>formatUnixMs()<br><br>formatUnixMs(String(1))</td></tr><tr><td>formatUnixSec</td><td><p>Formats a variable's value from seconds into <a href="https://www.iso.org/iso-8601-date-and-time-format.html">ISO-8601</a> date-time format. Additionally, it accepts a format style character (1) as a parameter.<br><br>Valid format characters are: </p><ul><li>F: Full text style (Sunday, January 29, 2023 at 12:05:37 AM Coordinated Universal Time)</li><li>L: Long text style(January 29, 2023 at 12:05:37 AM UTC)</li><li>M: Medium text style(Jan 29, 2023, 12:05:37 AM)</li><li>S: Short text style(1/29/23, 12:05 AM)</li></ul><p>Any other character will lead to medium text style as default.</p></td><td>formatUnixSec()<br><br>formatUnixSec(String(1))</td></tr><tr><td>formatDateString</td><td><p>Formats a variable's value into <a href="https://www.iso.org/iso-8601-date-and-time-format.html">ISO-8601</a> date format. Additionally, it accepts a format style character (1) as a parameter.<br><br>Valid format characters are: </p><ul><li>F: Full text style (Sunday, January 29, 2023 at 12:05:37 AM Coordinated Universal Time)</li><li>L: Long text style(January 29, 2023 at 12:05:37 AM UTC)</li><li>M: Medium text style(Jan 29, 2023, 12:05:37 AM)</li><li>S: Short text style(1/29/23, 12:05 AM)</li></ul><p>Any other character will lead to medium text style as default.</p></td><td>formatDateString()<br><br>formatDateString(String(1))</td></tr><tr><td>join</td><td>Displays a text composed of array values joined by a given delimiter(1). If no delimiter is provided, the function defaults to <code>", "</code>.</td><td>join()<br><br>join(String(1))</td></tr><tr><td>joinFromObjectArray</td><td>Displays a text composed of object array(1) values joined by a given delimiter(2). If no delimiter is provided, the function defaults to a new line.</td><td>joinFromObjectArr(<strong>String(1)</strong>)<br><br>joinFromObjectArr(<strong>String(1)</strong>, <strong>String(2)</strong>)</td></tr></tbody></table>



### Examples

<table data-full-width="false"><thead><tr><th>Function</th><th>Sample</th><th>Input data</th><th>Output</th></tr></thead><tbody><tr><td>substring</td><td><code>{{ var.substring(3) }}</code><br><br><code>{{ var.substring(5, 7) }}</code></td><td><p></p><pre class="language-json"><code class="lang-json">{
    "var": "Test result"
}
</code></pre></td><td>result<br><br>res</td></tr><tr><td>lowerCase</td><td><code>{{ var.lowerCase() }}</code></td><td><p></p><pre class="language-json"><code class="lang-json">{
    "var": "Gavin Belson from Hooli"
}
</code></pre></td><td>gavin belson from hooli</td></tr><tr><td>upperCase</td><td><code>{{ var.upperCase() }}</code></td><td><p></p><pre class="language-json"><code class="lang-json">{
    "var": "Gavin Belson from Hooli"
}
</code></pre></td><td>GAVIN BELSON FROM HOOLI</td></tr><tr><td>replaceAll</td><td><code>{{ var.replaceAll("Gavin Belson", "Richard Hendricks") }}</code></td><td><p></p><pre class="language-json"><code class="lang-json">{
    "var": "Gavin Belson owns Hooli"
}
</code></pre></td><td>Richard Hendricks owns Hooli</td></tr><tr><td>splitTakeAt</td><td><code>{{ var.splitTakeAt("Belson, ", 1) }}</code></td><td><p></p><pre class="language-json"><code class="lang-json">{
    "var": "Gavin Belson, Richard Hendricks and Russ Hanneman are in the tres commas club"
}
</code></pre></td><td>Richard Hendricks and Russ Hanneman are in the tres commas club</td></tr><tr><td>startsWithTake</td><td><code>{{ var.startsWithTake("I am the best", "In your dreams - Bertram Gilfoyle") }}</code></td><td><p></p><pre class="language-json"><code class="lang-json">{
    "var": "I am the best software engineer at Pied Piper - Dinesh Chugtai"
}
</code></pre></td><td>In your dreams - Bertram Gilfoyle</td></tr><tr><td>equalsTake</td><td><code>{{ var.equalsTake("I am better than Gilfoyle - Dinesh Chugtai", "Not true - Bertram Gilfoyle") }}</code></td><td><p></p><pre class="language-json"><code class="lang-json">{
    "var": "I am better than Gilfoyle - Dinesh Chugtai"
}
</code></pre></td><td>Not true - Bertram Gilfoyle</td></tr><tr><td>endsWithTake</td><td><code>{{ var.endsWithTake("Dinesh Chugtai", "Lies - Bertram Gilfoyle") }}</code></td><td><p></p><pre class="language-json"><code class="lang-json">{
    "var": "I am the fastest coder - Dinesh Chugtai"
}
</code></pre></td><td>Lies - Bertram Gilfoyle</td></tr><tr><td>containsTake</td><td><code>{{ var.containsTake("rocks", "Pied Piper rocks") }}</code></td><td><p></p><pre class="language-json"><code class="lang-json">{
    "var": "Hooli rocks"
}
</code></pre></td><td>Pied Piper rocks</td></tr><tr><td>startsWithTakeOrDrop</td><td><code>{{ var.startsWithTakeOrDrop("I am the best", "In your dreams - Bertram Gilfoyle") }}</code></td><td><p>1:</p><pre class="language-json"><code class="lang-json">{
    "var": "I am the best software engineer at Pied Piper - Dinesh Chugtai"
}
</code></pre><p><br>2: </p><pre class="language-json"><code class="lang-json">{
    "var": "Pied Piper"
}
</code></pre></td><td>1: In your dreams - Bertram Gilfoyle<br><br>2:</td></tr><tr><td>equalsTakeOrDrop</td><td><code>{{ var.equalsTakeOrDrop("I am better than Gilfoyle - Dinesh Chugtai", "Not true - Bertram Gilfoyle") }}</code></td><td><p>1:</p><pre class="language-json"><code class="lang-json">{
    "var": "I am better than Gilfoyle - Dinesh Chugtai"
}
</code></pre><p><br>2:</p><pre class="language-json"><code class="lang-json">{
    "var": "Pied Piper"
}
</code></pre></td><td>1: Not true - Bertram Gilfoyle<br><br>2:</td></tr><tr><td>endsWithTakeOrDrop</td><td><code>{{ var.endsWithTakeOrDrop("Dinesh Chugtai", "Lies - Bertram Gilfoyle") }}</code></td><td><p>1:</p><pre class="language-json" data-full-width="false"><code class="lang-json">{
    "var": "I am the fastest coder - Dinesh Chugtai"
}
</code></pre><p><br>2:</p><pre class="language-json"><code class="lang-json">{
    "var": "Pied Piper"
}
</code></pre></td><td>1: Lies - Bertram Gilfoyle<br><br>2:</td></tr><tr><td>containsTakeOrDrop</td><td><code>{{ var.containsTakeOrDrop("rocks", "Pied Piper rocks") }}</code></td><td><p></p><p>1:</p><pre class="language-json" data-full-width="false"><code class="lang-json">{
    "var": "Hooli rocks"
}
</code></pre><p><br>2:</p><pre class="language-json"><code class="lang-json">{
    "var": "Pied Piper"
}
</code></pre></td><td>1: Pied Piper rocks<br><br>2:</td></tr><tr><td>startsWithElse</td><td><code>{{ var.startsWithElse("I am the best", "In your dreams - Bertram Gilfoyle") }}</code></td><td><p><br></p><p>1.</p><pre class="language-json"><code class="lang-json">{
    "var": "I am the best software engineer at Pied Piper - Dinesh Chugtai"
}
</code></pre><p><br>2: </p><pre class="language-json"><code class="lang-json">{
    "var": "Pied Piper"
}

</code></pre></td><td>1: I am the best software engineer at Pied Piper - Dinesh Chugtai<br><br>2: In your dreams - Bertram Gilfoyle</td></tr><tr><td>equalsElse</td><td><code>{{ var.equalsElse("I am better than Gilfoyle - Dinesh Chugtai", "Not true - Bertram Gilfoyle") }}</code></td><td><p></p><p>1:</p><pre class="language-json"><code class="lang-json">{
    "var": "I am better than Gilfoyle - Dinesh Chugtai"
}
</code></pre><p><br>2:</p><pre class="language-json"><code class="lang-json">{
    "var": "Pied Piper"
}
</code></pre></td><td>1: I am better than Gilfoyle - Dinesh Chugtai<br><br>2: Not true - Bertram Gilfoyle</td></tr><tr><td>endsWithElse</td><td><code>{{ var.endsWithElse("Dinesh Chugtai", "Lies - Bertram Gilfoyle") }}</code></td><td><p></p><p>1:</p><pre class="language-json" data-full-width="false"><code class="lang-json">{
    "var": "I am the fastest coder - Dinesh Chugtai"
}
</code></pre><p><br>2:</p><pre class="language-json"><code class="lang-json">{
    "var": "Pied Piper"
}
</code></pre></td><td>1: I am the fastest coder - Dinesh Chugtai<br><br>2: Lies - Bertram Gilfoyle</td></tr><tr><td>containsElse</td><td><code>{{ var.containsElse("rocks", "Pied Piper rocks") }}</code></td><td><p></p><p>1:</p><pre class="language-json" data-full-width="false"><code class="lang-json">{
    "var": "Hooli rocks"
}
</code></pre><p><br>2:</p><pre class="language-json"><code class="lang-json">{
    "var": "Pied Piper"
}
</code></pre></td><td>1: Hooli rocks<br><br>2: Pied Piper rocks</td></tr><tr><td>startsWithElseOrDrop</td><td><code>{{ var.startsWithElseOrDrop("I am the best", "In your dreams - Bertram Gilfoyle") }}</code></td><td><p></p><p>1.</p><pre class="language-json"><code class="lang-json">{
    "var": "I am the best software engineer at Pied Piper - Dinesh Chugtai"
}
</code></pre><p><br>2: </p><pre class="language-json"><code class="lang-json">{
    "var": "Pied Piper"
}
</code></pre></td><td>1:<br><br>2: In your dreams - Bertram Gilfoyle</td></tr><tr><td>equalsElseOrDrop</td><td><code>{{ var.equalsElseOrDrop("I am better than Gilfoyle - Dinesh Chugtai", "Not true - Bertram Gilfoyle") }}</code></td><td><p></p><p>1:</p><pre class="language-json"><code class="lang-json">{
    "var": "I am better than Gilfoyle - Dinesh Chugtai"
}
</code></pre><p><br>2:</p><pre class="language-json"><code class="lang-json">{
    "var": "Pied Piper"
}
</code></pre></td><td>1:<br><br>2: Not true - Bertram Gilfoyle</td></tr><tr><td>endsWithElseOrDrop</td><td><code>{{ var.endsWithElseOrDrop("Dinesh Chugtai", "Lies - Bertram Gilfoyle") }}</code></td><td><p></p><p>1:</p><pre class="language-json" data-full-width="false"><code class="lang-json">{
    "var": "I am the fastest coder - Dinesh Chugtai"
}
</code></pre><p><br>2:</p><pre class="language-json"><code class="lang-json">{
    "var": "Pied Piper"
}
</code></pre></td><td>1:<br><br>2: Lies - Bertram Gilfoyle</td></tr><tr><td>containsElseOrDrop</td><td><code>{{ var.containsElseOrDrop("rocks", "Pied Piper rocks") }}</code></td><td><p></p><p>1:</p><pre class="language-json" data-full-width="false"><code class="lang-json">{
    "var": "Hooli rocks"
}
</code></pre><p><br>2:</p><pre class="language-json"><code class="lang-json">{
    "var": "Pied Piper"
}
</code></pre></td><td>1:<br><br>2: Pied Piper rocks</td></tr><tr><td>formatUnixMs</td><td><code>{{ var.formatUnixMs() }}</code><br><br><code>{{ var.formatUnixMs("S") }}</code></td><td><p></p><pre class="language-json"><code class="lang-json">{
    "ms": 1674950737000
}
</code></pre></td><td>1: Jan 29, 2023, 12:05:37 AM<br><br>2: 1/29/23, 12:05 AM</td></tr><tr><td>formatUnixSec</td><td><code>{{ var.formatUnixSec() }}</code><br><br><code>{{ var.formatUnixSec("S") }}</code></td><td><p></p><pre class="language-json"><code class="lang-json">{
    "sec": 1674950737
}
</code></pre></td><td>1: Jan 29, 2023, 12:05:37 AM<br><br>2: 1/29/23, 12:05 AM</td></tr><tr><td>formatDateString</td><td><code>{{ var.formatDateString() }}</code><br><br><code>{{ var.formatDateString("S") }}</code></td><td><p></p><pre class="language-json"><code class="lang-json">{
    "str": "2021-05-25T21:24:56.771Z"
}
</code></pre></td><td>1: May 25, 2021, 9:24:56 PM<br><br>2: 5/25/21, 9:24 PM</td></tr><tr><td>join</td><td><code>{{ var.join() }}</code><br><br><code>{{ var.join("- ") }}</code></td><td><p></p><pre class="language-json"><code class="lang-json">{
    "array": ["PiedPiper", "Hooli", "Aviato"]
}
</code></pre></td><td>1: PiedPiper, Hooli, "Aviato"<br><br>2: PiedPiper- Hooli- Aviato</td></tr><tr><td>joinFromObjectArray</td><td><code>{{ companies.joinFromObjectArr("name") }}</code><br><br><code>{{ companies.joinFromObjectArr("ceo", "+") }}</code></td><td><p></p><pre class="language-json"><code class="lang-json">{
    "companies": [
        {
            "name": "PiedPiper",
            "ceo": "Richard Hendricks"
        },
        {
            "name": "Hooli",
            "ceo": "Gavin Belson"
        },
        {
            "name": "NewPiedPiper",
            "ceo": "Jian-Yang"
        },
        {
            "name": "Raviga",
            "ceo": "Peter Gregory"
        }
    ]
}
</code></pre></td><td>1: <br>PiedPiper<br>Hooli<br>NewPiedPiper<br>Raviga<br><br>2: <br>PiedPiper+Hooli+NewPiedPiper+Raviga</td></tr></tbody></table>



## Mustache in ITL

The ITL also supports mustache condition sections and loops, providing flexibility in handling complex templates and varying data sets efficiently.



{% hint style="info" %}
[ITL functions](itl-ilert-template-language.md#functions) inside mustache sections and loop blocks will be ignored.
{% endhint %}

### Sections

Sections in mustache allow for conditional rendering, where specific content is displayed only if a certain value exists or meets a given condition. Positive conditions check if a value is present or "true," while inverted conditions render content when the value is "false" or missing.\
\
A section begins with a hash `#` and ends with a slash `/`. Example:

{% tabs %}
{% tab title="True condition" %}
```mustache

{{ #isTrue }}
Hello
{{ /isTrue }}
World!
```
{% endtab %}

{% tab title="False condition" %}
```mustache

{{ #isFalse }}
Hello
{{ /isFalse }}
World!
```
{% endtab %}
{% endtabs %}

Using the following context:

```json
{
    "isTrue": true,
    "isFalse": false
}
```

{% tabs %}
{% tab title="True condition output" %}
```
Hello World!
```
{% endtab %}

{% tab title="False condition" %}
```
World!
```
{% endtab %}
{% endtabs %}



#### Inverted sections

Inverted sections only render content based on the inverse value of a context key.&#x20;

An inverted section begins with a caret `^` and ends with a slash `/`. Example:

{% tabs %}
{% tab title="True condition" %}
```mustache
Hello

{{ #isTrue }}
World!
{{ /isTrue }}
{{ ^isTrue }}
Tim!
{{ /isTrue }}
```
{% endtab %}

{% tab title="False condition" %}
```mustache
Hello

{{ #isFalse }}
World!
{{ /isFalse }}
{{ ^isFalse }}
Tim!
{{ /isFalse }}
```
{% endtab %}
{% endtabs %}

Using the following context:

```json
{
    "isTrue": true,
    "isFalse": false
}
```

{% tabs %}
{% tab title="True condition output" %}
```
Hello World!
```
{% endtab %}

{% tab title="False condition output" %}
```
Hello Tim!
```
{% endtab %}
{% endtabs %}



### Loops

Loops in mustache allow to iterate over each item of a list or array of data and display render them as text.

A loop in Mustache is written in the same way as a section. It begins with a hash # and ends with a slash /. Inside the loop, you place the key that represents the list or array to be iterated over. Mustache will then automatically loop through each element in the array.

{% tabs %}
{% tab title="Simple array" %}
```mustache

{{ #simple }}
{{.}}
{{ /simple }}
```
{% endtab %}

{% tab title="Nested array" %}
<pre class="language-mustache"><code class="lang-mustache">
<strong>{{ #nested }}
</strong>{{ name }}
{{ #nested }}
</code></pre>
{% endtab %}
{% endtabs %}

Using the following context:

```json
{
    "simple": ["Pied Piper", "Hooli", "Raviga"],
    "nested": [
        { "name": "Richard Hendricks" },
        { "name": "Gavin Belson" },
        { "name": "Peter Gregory" }
    ]
}
```

{% tabs %}
{% tab title="Simple array output" %}
```
Pied Piper
Hooli
Raviga
```
{% endtab %}

{% tab title="Nested array output" %}
```
Richard Hendricks
Gavin Belson
Peter Gregory
```
{% endtab %}
{% endtabs %}
