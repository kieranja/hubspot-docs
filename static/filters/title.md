# title
Return a titlecased version of the value. I.e. words will start with uppercase letters, all remaining characters are lowercase.

#### Example
```jinja2
{% text "my_title" label='Enter a title', value='My title should be titlecase', export_to_template_context=True %} 
{{ widget_data.my_title.value|title }}
```

#### Output
```jinja2
My Title Should Be Titlecase
```

