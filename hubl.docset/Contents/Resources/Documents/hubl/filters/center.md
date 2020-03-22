# center
The center filter uses whitespace to center text within a given field length. This filter is not recommended or particularly useful since HubSpot's HTML compiler will automatically strip out the white space; however, it is included here for the sake of comprehensiveness.
| Parameter | Description | 
|  ------  |  ------  | 
| width `Required` | Specifies the length of whitespace to center the text in. | 

The example below shows a center filter being applied to a variable in a pre tag, so the whitespace isn't stripped out.

#### Example
```jinja2
<pre>
{% set var = "string to center" %}
before{{ var|center(80) }}after
</pre>
```

#### Output
```jinja2
<pre>
before                                string to center                                after
</pre>
```

