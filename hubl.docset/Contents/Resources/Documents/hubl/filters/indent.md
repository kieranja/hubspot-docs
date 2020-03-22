# indent
The indent filter uses whitespace to indent text within a given field length. This filter is not recommended or particularly useful since HubSpot's HTML compiler will automatically strip out the white space; however, it is included here for the sake of comprehensiveness. The example below shows a center filter being applied to a variable in a pre tag, so the whitespace isn't stripped out. The first parameter controls the amount of whitespace and the second boolean toggles whether to indent the first line.
| Parameter | Description | 
|  ------  |  ------  | 
| width `Required` | The amount of whitespace to be applied. | 
| boolean `Required` | A boolean value on whether to indent the first line. | 


#### Example
```jinja2
<pre>
{% set var = "string to indent" %}
{{ var|indent(2, true) }}
</pre>
```

#### Output
```jinja2
  string to indent
```

