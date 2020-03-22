# Color
The color module generates a color picker in the page editor UI that prints a HEX color value to a template. Please note that this module can only be used in templates, not CSS files. If using this tag in a &lt;style&gt; or inline CSS, you will want to use the no\_wrapper=True parameter to remove the wrapper &lt;span&gt; wrapper.

#### Example
```jinja2
{% color "color" %}
{% color "my_color_picker" label='Choose a color', color='#000000', no_wrapper=True %}
```

#### Output
```jinja2
#000000
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| color | String | A default HEX color value for the color picker | 

