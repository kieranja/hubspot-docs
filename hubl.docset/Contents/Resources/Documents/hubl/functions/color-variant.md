# color_variant
This function lightens or darkens a HEX value or color variable by a set amount. The first parameter is the hex color (for example ("#FFDDFF") or a variable storing a HEX value. The second parameter is the amount to adjust it by, from 0 to 255. This function can be used in CSS files to create a color variation. Another good use case is to use it with a color parameter of a color module, to allow users to specify a primary color that automatically generates a color variation.

In the example below, the HEX color #3A539B is stored in a variable called `base_color`. The color is modified by -80 resulting in a darker blue (#00034B).

#### Example
```jinja2
{% set base_color ="#3A539B" %} 
{{ color_variant(base_color, -80) }}
```

#### Output
```jinja2
#00034b
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| base_color | HEX color string | The starting color to be altered (Example: #F7F7F7). | 
| brightness_offset | Integer | A positive or negative number used to lighten or darken the base color. | 

