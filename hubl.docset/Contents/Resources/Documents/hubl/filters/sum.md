# sum
Adds numeric values in a sequence. The first parameter can specify an optional attribute and the second parameter sets a value to return if there is nothing in the variable to sum.
| Parameter | Description | 
|  ------  |  ------  | 
| attribute `Optional` | Attribute to sum. | 
| return_if_nothing `Optional` | Value to return if there is nothing in the variable to sum. | 


#### Example
```jinja2
{% set sum_this = [1, 2, 3, 4, 5] %}
{{ sum_this|sum }}
Total: {{ items|sum(attribute='price') }}
```

#### Output
```jinja2
15
Total: 20
```

