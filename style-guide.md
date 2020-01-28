# Markdown Formatting Guide

## Heading One

### Heading Two

#### Heading Three

This sentence about formatting is important, as are these bullet points:

* This sentence uses **bold**.
* This one uses _italics_.
* It is unlikely that we will need ~~strikethrough text~~.
* This is an `inline code reference`.
* This is a link to [another doc](sandbox/test.md).
* This is a link to [another website](https://www.google.com).

🛑 Do not put emojis in documentation.

$$formula = 5+66/76(13^7)$$ 

Here is some more text, that has an image ![](.gitbook/assets/screen-shot-2020-01-10-at-3.25.20-pm.png) inline.

* This bullet is at the first level.
  * This is the second level.
* This is the first level again.
  * Again, the second.
    * This is the third level.
      * This is the fourth level.
        * Fifth.
          * Sixth.
            * Seventh.
              * Eighth
                * Ninth
                  * Tenth
                    * This is excessive, but eleventh.
                      * Twelfth
                        * Thirteenth
                          * Fourteenth
                            * I can't imagine we go down fifteen levels, but now we know we can.
* [ ] Here are some tasks in a checklist.
* [ ] Here is another task.
* [ ] Best of luck.

1. This is an ordered list.
   1. This is step 1a.
      1. This is step 1aa
      2. This is step 1ab
   2. This is step 1b
2. This is step two.
   1. You can't have bullets inside an ordered list, though we should test this from GitHub -&gt; GitBook as well.

{% tabs %}
{% tab title="C\#" %}
```cpp
This is a block of code. I can change the programming language if I want.
```
{% endtab %}

{% tab title="Bash" %}
```bash
Here is another tab
```
{% endtab %}

{% tab title="CSS" %}
```css
Here is another tab
```
{% endtab %}
{% endtabs %}

> This is a quote.
>
> There are two paragraphs in it.

![](.gitbook/assets/screen-shot-2020-01-13-at-1.55.48-pm.png)

| This table | Contents |
| :--- | :--- |
| Here is line one | Here is line two, with some more content. |
| There is another row here | It autodetermines the best place for the middle line of the two columns, and will auto wrap when necessary. |

{% hint style="info" %}
This is an information bubble.
{% endhint %}

{% hint style="warning" %}
This is a caution or warning.
{% endhint %}

{% hint style="danger" %}
This is definitely a warning.
{% endhint %}

{% hint style="success" %}
This is a checkmark to confirm something works.
{% endhint %}

{% api-method method="get" host="" path="" %}
{% api-method-summary %}
API Method
{% endapi-method-summary %}

{% api-method-description %}
This is an example of the markdown.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}
This is a string.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
Woo it worked.
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% tabs %}
{% tab title="First Tab" %}
Here are some random tabs in case you have different versions of a thing.
{% endtab %}

{% tab title="Second Tab" %}
Here is the second tab.

It doesn't have as much content.

$$
a = b
$$
{% endtab %}
{% endtabs %}

$$
a = b
$$



