# round
Round the number to a given precision.
| Parameter | Description | 
|  ------  |  ------  | 
| precision `Optional` | Specifies the precision of the rounding. | 
| rounding_method `Optional` | Options include common round either up or down (default); ceil always rounds up; floor always rounds down.
If you don’t specify a method common is used. | 


#### Example
```jinja2
{{ 52.5|round }} 
{{ 52.5|round(0, 'floor') }}
```

#### Output
```jinja2
53
52
```

