# append
Adds a single item to the end of a list.

#### Example
```jinja2
{% set numbers_under_5 = [1,2,3] %}
{% do numbers_under_5.append(4) %}
{{numbers_under_5}}
```

#### Output
```jinja2
[1, 2, 3, 4]
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| item | Any | Item to be appended to the list. | 

