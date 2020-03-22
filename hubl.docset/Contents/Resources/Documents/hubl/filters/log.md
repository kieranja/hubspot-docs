# log
Calculates the natural logarithm of a number.
| Parameter | Description | 
|  ------  |  ------  | 
| base `Optional` | Calculate the logarithm at the nth base. | 


#### Example
```jinja2
{{ 10|log }}
{{ 65536|log(2) }}
```

#### Output
```jinja2
2.302585092994046
16.0
```

