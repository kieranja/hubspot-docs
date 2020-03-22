# cut
Removes a string from a value. This filter can be used to match and cut out a specific part of a string. The parameter specifies the part of the string that should be removed. The example below removes the space and the word world from the original variable value.
| Parameter | Description | 
|  ------  |  ------  | 
| characters_to_cut `Required` | The part of the string that should be removed. | 


#### Example
```jinja2
{% set my_string = "Hello world." %} 
{{ my_string|cut(' world') }}
```

#### Output
```jinja2
Hello.
```

