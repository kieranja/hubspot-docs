# divide
Divide the current value by a divisor. The parameter passed is the divisor. This filter is an alternative to the / operator.
| Parameter | Description | 
|  ------  |  ------  | 
| divisor `Required` | The number to divide the variable by. | 


#### Example
```jinja2
{% set numerator = 106 %}
{{ numerator|divide(2) }}
```

#### Output
```jinja2
53
```

