# unique
This filter extracts a unique set from a sequence or dict of objects. When filtering a dict, such as a list of posts returned by a function, you can specify the which attribute should be used to deduplicate items in the dict.
| Parameter | Description | 
|  ------  |  ------  | 
| attr `Optional` | Specifies the attribute that should be used when filtering a dict value | 


#### Example
```jinja2
{% set my_sequence = ['one', 'one', 'two', 'three' ] %} 
{{ my_sequence|unique }}
```

#### Output
```jinja2
[one, two, three]
```

