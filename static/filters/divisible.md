# divisible
An alternative to the divisibleby expression test, the filter divisible will evaluate to true if the value is divisible by the given number.
| Parameter | Description | 
|  ------  |  ------  | 
| divisor `Required` | The number to use when evaluating if the value is divisible. | 


#### Example
```jinja2
{% set num = 10 %}
{% if num|divisible(2) %}
The number is divisble by 2
{% endif %}
```

#### Output
```jinja2
The number is divisible by 2
```

