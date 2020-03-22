# split
Splits the input string into a list on the given separator. The first parameter specifies the separator to split the variable by. The second parameter determines how many times the variable should be split. Any remaining items would remained group. In the example below, a string of names is split at the ";" for the first 4 names.
| Parameter | Description | 
|  ------  |  ------  | 
| character_to_split_by `Required` | Specifies the separator to split the variable by. | 
| number_of_splits `Required` | Determines how many times the variable should be split. Any remaining items would remain grouped. | 


#### Example
```jinja2
{% set string_to_split = "Stephen; David; Cait; Nancy; Mike; Joe; Niall; Tim; Amanda" %}
{% set names = string_to_split|split(';', 4) %}
<ul>
{% for name in names %}
  <li>{{ name }}</li>
{% endfor %}
</ul>
```

#### Output
```jinja2
<ul>
  <li>Stephen</li>
  <li>David</li>
  <li>Cait</li>
  <li>Nancy; Mike; Joe; Niall; Tim; Amanda</li>
</ul>
```

