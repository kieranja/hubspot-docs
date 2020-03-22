# join
Return a string which is the concatenation of the strings in the sequence. The separator between elements is an empty string per default, you can define it with the optional parameter. The second parameter can be used to specify an attribute to join.
| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| delimiter `Optional` | String | The delimiter to use when concatenating strings. | 
| attribute `Optional` | HubL Variable | An attribute to use as a delimiter. | 


#### Example
```jinja2
{% set my_list = [1, 2, 3] %}
{% set sep = "---" %}
{{ my_list|join }}
{{ my_list|join('|') }}
{{ my_list|join(sep) }}
```

#### Output
```jinja2
123
1|2|3
1---2---3
```

