# select
Filters a sequence of objects by applying a test to the object and only selecting the ones with the test succeeding.
| Parameter | Description | 
|  ------  |  ------  | 
| exp_text | The expression test to apply to the object. | 


#### Example
```jinja2
{% set some_numbers = [10, 12, 13, 3, 5, 17, 22] %} 
{{ some_numbers|select('even') }}
```

#### Output
```jinja2
[10, 12, 22] 
```

