# Unless statements
`unless` statements are conditionals just like `if` statements, but they work on the inverse logic. They will render and compile the code between the opening and closing tags, unless the single boolean condition evaluates to true. Unless statements begin with an **`unless`** and end with an **`endunless`.** They do not support `elif` or `else`.

Below is an example that prints an "Under construction" header, unless the rich text field is valued. If the rich text field has content, then that content will display.

#### Example
```jinja2
{% module "my_page_content" path="@hubspot/rich_text", label='Enter your page content', html='' export_to_template_context=true %}

{{ widget_data.my_page_content.html }}

{% unless widget_data.my_page_content.html %}
<h1>This page is under construction.</h1>
<h3>Come back soon!</h3>
{% endunless %}
```

