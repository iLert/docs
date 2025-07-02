# ICL - ilert condition language

Customize and fine tune your automation experience across the platform - if needed.

```
event.summary not contains 'dev stage' and (
    event.customDetails.location in ["DE", "CH", "AT"]
        or resetting_trigger_count.10m >= 100
)
```

The ICL is a flexible tool that appears in many places as events or calls flow through the ilert platform. It is is supported in:

* **Event flow**
* **Alert source event filter**
* **Alert action conditional execution**
* **Call flow branch conditions**

Usually the UI offers a condition builder for easy access to the powerful features of the ICL, however users that want more control over their flows can switch to the editor mode (or use the API/terraform to provide their customized expressions)

<figure><img src="../.gitbook/assets/image (212).png" alt=""><figcaption><p>The UI ICL builder helps users get started quickly</p></figcaption></figure>

Use the toggle on the top right to switch to the code editor mode:

<figure><img src="../.gitbook/assets/image (213).png" alt=""><figcaption><p>The code editor allows for more advanced and fine tuned control</p></figcaption></figure>

{% hint style="success" %}
Note that the editor will automatically switch to code mode if it encounters advanced syntax that is not easily displayable in the simplified view
{% endhint %}



## Syntax

### Expression

An ICL expression includes paths, literals, built-in operations, and custom functions. When evaluating an ICL expression, certain precedence rules are followed. In the end, the full ICL expression needs to either be `true` or `false`. Sub-expressions within it can produce other types of values, like integers or strings. If these non-boolean values are used correctly, no errors will occur. While evaluating, a sub-expression might fail to evaluate correctly. It won’t stop the entire expression from being evaluated. For more information, refer to the section on Non-Boolean Evaluation.

### Precedence

ICL expressions consist of boolean sub-expressions and the final result must also be a boolean value. You can combine sub-expressions using "and," "or," and "not" to create more complex boolean expressions. An example to keep in mind when forming expressions:

`event.x > 1 and (event.y < 2 or event.z == 3)`

is treated like

`(event.x > 1) and ((event.y < 2) or (event.z == 3))`

### Paths

An ICL expression is evaluated in the context of an **event** or **alert** depending on where the filter is placed (alert source or alert action). You use a path in your ICL expression to access nested objects and arrays within the context payload. For example, an event path can access fields like `event.summary` or `alert.priority`. A customDetails path can be used to access values from the original JSON Event payload sent to ilert (e.g. `event.customDetails.alerts[0].severity`).

In event flows and call flows the variable extraction entrypoint starts with **context** (e.g. `context.integrationType == 'PRTG'`). Note that event flows offer the `context.event.` to access the current state of the event payload (e.g. `context.event.customDetails.tags`).

You can access object fields using dot notation ("."). Field names used with dot notation must be valid identifiers. Valid identifiers start with an ASCII letter (a-z, A-Z) or an underscore ("\_"), and the following characters can include these plus numerical digits (0-9).

For object field names that don't follow this identifier rule, you can use bracket notation by providing the field name as a single-quoted string inside square brackets, for example, object\['an identifier']. Array elements can be accessed using numbers inside square brackets.

When a path is used in an expression, it gets evaluated to the value at that path within the data context before being used in the expression. If the path does not exist, the value is replaced with `nil`. You can check for nil e.g. `event.customDetails.dontExist == nil` .

Imagine the following payload being sent to the ilert event API:

```json
{
   "summary": "An alert summary",
   "customDetails": {
      "locationX": 0.54,
      "key wi:th spaces": {
         "some_field": "Hello there"
      }    
  },
  "links": [
    { "href": "https://awebsite.de/some/page", "text": "A title" }
  ]
}
```

You can extract data from the ^ payload using these ICL paths:

```
event.summary -> "An alert summary"

event.customDetails.locationX -> 0.54

event.customDetails[key\ wi:th\ spaces].some_field -> "Hello there"

event.links[0].href -> "https://awebsite.de/some/page"

event.customDetails.dontExist -> nil
```

## Types

ICL understands the following types:

* String
* Number (Integer/Float)
* Boolean
* Datetime
* Array
* Object
* nil

Explicit casting is not supported, however (depending on the provided operator) ICL will try to implicitely cast types e.g. `'1' == 1` will result in `true`.

Datetimes and array types are only supported by specific operators.

### String

A string can be any sequence of UTF-8 characters, in case it contains whitespace characters enclosing in single quotes is required. To include a single quote within the string, use a backslash (\\) before the quote to escape it. You can also escape a backslash by using another backslash.

```
'hey a string'
Platin
'the system\'s up'
'an escaped \\ backslash'
```

### Number

A number can be an integer or a float. A number can be positive or negative.

* Integers are 64-bit signed integers between `-2^63` and `2^63 - 1`
* Floats are double precision (64-bit) IEEE floating point numbers. They must begin with a digit and must have a decimal point.

```
42
0.42
-24
```

### Boolean

The values `true` or `false`. Written without quotes.

```
true
false
```

### Datetime

Absolute datetime values in ISO format `YYYY-MM-DDThh:mm:SSZ` and epoch second as well as milliseconds are supported by the time operators e.g. `is_in` . You can use `now` to refer to the current datetime at the moment of expression evaluation.

```
'2024-05-15T15:18:00Z'
1715786280
1715786280000
now
```

### Array

Inline JSON arrays are supported by some operators as right hand values e.g. `starts_with_any`

Often used to enable multi value inputs for operators `event.key starts_with hey` -> `event.key starts_with_any ["hey", "hi"]`

```
["one", "two"]
```

### Object

Inline JSON objects are supported by some operators as right hand values e.g. `is_in`

Often used to reference account entities e.g. check if current time is within a support hour.

```
{"id": 1, "type": "SUPPORT_HOUR"}
{"id": 1, "type": "ON_CALL_SCHEDULE"}
```

### nil

A value representing the absense of any other value type.

## Operators

There a different operators in ICL that support specific types:

* `and`, `or` -> Boolean (on expression blocks)
* `not` -> negates a following operator (e.g. `not matches` -> `!=`) _may also be prefixed to any supported operator_ `not matches` == `not_matches`
* `>`, `>=`, `<`, `<=` -> Number (and trigger counts)
* `matches`, `contains`, `regex` , `starts_with`, `ends_with`, `exact_matches`, `exact_contains` -> String _(matches is an alias of ==)_
* `==,` `!=` -> Global (work on almost all types)
* `in` -> Array
* `is_in` , `now` -> Time
* `contains_any`, `starts_with_any`, `ends_with_any` -> String multi
* `trigger_count.*`, `resetting_trigger_count.*` -> Threshold condition



### and



```
[boolean] and [boolean] -> [boolean]
```

### or



```
[boolean] or [boolean] -> [boolean]
```

### not



```
[any] not [operator] [any] -> ![boolean]
[any] not_[operator] [any] -> ![boolean]
```

### >, >=, <, <= (Number)



```
[number] > [number] -> [boolean]
[number] >= [number] -> [boolean]
[number] < [number] -> [boolean]
[number] <= [number] -> [boolean]
```

### matches, contains, regex (String)

By default string operators are case insensitive, you may use exact\_matches or exact\_contains in case you need to perform a case sensitive check.

```
[string] matches [string] -> [boolean]
[string] exact_matches [string] -> [boolean]
[string] contains [string] -> [boolean]
[string] exact_contains [string] -> [boolean]
[string] regex [string] -> [boolean]
[string] starts_with [string] -> [boolean]
[string] ends_with [string] -> [boolean]
```

### ==, !=



```
[string] == [string] -> [boolean]
[string] != [string] -> [boolean]
[number] == [number] -> [boolean]
[number] != [number] -> [boolean]
[boolean] == [boolean] -> [boolean]
[boolean] != [boolean] -> [boolean]
[number] == [string] -> [boolean]
[string] != [number] -> [boolean]
```

### in (Array)

Note that the right side might be an inline JSON array, \
however a path is supported as well `'u-turn' in event.car`

```
[string] in [string[]] -> [boolean]
```

### is\_in (Time)



```
[string] is_in [object{id, type: SUPPORT_HOUR|ON_CALL_SCHEDULE}] -> [boolean]
[string] not is_in [object{id, type: SUPPORT_HOUR|ON_CALL_SCHEDULE}] -> [boolean]
```

### \*\_any (Multi string)



```
[string] contains_any [string[]] -> [boolean]
[string] starts_with_any [string[]] -> [boolean]
[string] ends_with_any [string[]] -> [boolean]
```

### trigger\_count

{% hint style="info" %}
Threshold conditions will require ilert's AIOps Addon in the near future
{% endhint %}

The duration supports an ISO period value e.g. PT3M = 3 minutes, however we support a shorthand version 3m as well. It needs to be at **minimum 5 seconds** and at **maximum 2 days**. You can use multiple trigger\_counts in the same ICL expression, however they are only unique to their duration value (and to the context their evaluated in e.g. alert source). The counter is incremented at the moment of each evaluation, therefor it will start at `1`.&#x20;

trigger\_count will reset at the end of the running window duration.\
resetting\_trigger\_count will reset as soon as the limit on the right hand side is reached.

```
trigger_count.[duration] > [number] -> [boolean]
resetting_trigger_count.[duration] > [number] -> [boolean]
```



## Edge cases

### Non-Boolean evaluation

Evaluation of an ICL sub-expression may produce unclear or nonsensical results. For instance, consider an invalid type comparison like `3 > 'three'`.

Since ICL will be employed within the event processing pipeline, encountering an error and abandoning the entire event evaluation wouldn’t be practical, as there's no user to manage the error. Therefore, ICL treats any non-boolean evaluation as false. This approach ensures that the ICL expression can be evaluated consistently and without errors.

```
3 > 'three' -> false
3 >= 'three' or 3 < 9 -> true
3 <= 'three' and 3 < 9 -> false
```

### Comparing Integers, Floats, Doubles, Longs

When an integer is compared with a float, ICL attempts to compare both on the precision level of the float e.g. `9007199254740992 == 9007199254740992.0` -> true

Floating point numbers can't represent every integer greater than 2^53 (which is 9007199254740992). This limitation causes some strange behaviors, but it's not a bug. It's a known issue with how floating point numbers work. This problem exists in all programming languages that use floating point numbers. Below, you'll find some examples and explanations:\
\
`9007199254740992 == 9007199254740993.0` -> true

In this situation, the number 9007199254740993.0 can't be exactly represented using floating-point numbers. Instead, the closest possible floating-point number is chosen, which is 9007199254740992.0. When you check if the two numbers are equal, they're seen as the same because the floating-point representation rounded them to the same value.

`9007199254740992 == 9007199254740994.0` -> false

As expected, 9007199254740994.0 is the next number that can be accurately represented in floating point. This allows ICL to determine that they are different. Keep in mind that as floating point numbers become larger, the gap between the numbers that can be represented also increases.

We recommend checking out [https://0.30000000000000004.com/](https://0.30000000000000004.com/) for more information on the topic.

### Reserved words

A few words are not allowed in unqoted strings or operator places. If you want to use them, make sure to quote them e.g. `'for'`

```
break, at, do, as, const, continue, def, else, end, eq, function, for, gte, gt, if, import, is, let, lte, lt, loop, namespace, package, require, return, var, void, when, while
```

### Limits

{% hint style="info" %}
We are still collecting data together with our customers to identify fair usage limits for everybody.
{% endhint %}

