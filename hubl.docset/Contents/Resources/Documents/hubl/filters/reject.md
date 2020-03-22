# reject
Filters a sequence of objects by applying an [expression test](/docs/hubl/operators-and-expression-tests?hsLang=en) to the object and rejecting the ones with the test succeeding.
| Parameter | Description | 
|  ------  |  ------  | 
| exp_text | The expression test to apply to the object. | 


#### Example
```jinja2
{% set some_numbers = [10, 12, 13, 3, 5, 17, 22] %} 
{{ some_numbers|reject('even') }}
```

#### Output
```jinja2
[13, 3, 5, 17]
```

