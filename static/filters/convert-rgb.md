# convert_rgb
Converts a HEX value to an RGB string. This is useful if you need to convert color variables to RGB to be used with a RGBA CSS declaration. In the example below, the value set by a color module is converted to an RGB value and used in an RGBA CSS declaration.

#### Example
```jinja2
{% set my_color = "#FFFFFF" %}
{{ my_color|convert_rgb }}

{% color "my_color" color="#000000", export_to_template_context=True %}
<div style="background: rgba({{ widget_data.my_color.color|convert_rgb }}, .5)"></div>
```

#### Output
```jinja2
255, 255, 255

<div style="background: rgba(0, 0, 0, .5)"></div>
```

