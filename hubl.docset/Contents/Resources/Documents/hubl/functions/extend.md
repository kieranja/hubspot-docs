# extend
Extend a list by appending all items from an iterable. In other words, insert all list items from one list into another list.

#### Example
```jinja2
{% set vehicles = ["boat","car","bicycle"] %}
{% set more_vehicles = ["airplane","motorcycle"] %}
{% do vehicles.extend(more_vehicles) %}
{{vehicles}}
```

#### Output
```jinja2
[boat, car, bicycle, airplane, motorcycle]
```

