# int
Convert the value into an integer. If the conversion doesn’t work it will return 0. You can override this default using the first parameter.
| Parameter | Description | 
|  ------  |  ------  | 
| default `Required` | Integer to return if the conversion doesn't work. | 


#### Example
```jinja2
{% text "my_text" value='25', export_to_template_context=True %} 
{{ widget_data.my_text.value|int + 28 }}
```

#### Output
```jinja2
53
```

