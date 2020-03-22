# float
Convert the value into a floating point number. If the conversion doesn’t work it will return 0.0. You can override this default using the first parameter.
| Parameter | Description | 
|  ------  |  ------  | 
| default `Optional` | Integer to return if the conversion doesn't work.  | 


#### Example
```jinja2
{% text "my_text" value='25', export_to_template_context=True %} 
{{ widget_data.my_text.value|float + 28 }}
```

#### Output
```jinja2
53.0
```

