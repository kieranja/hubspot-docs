# pop
Removes the item at the index from the list. Also returns the removed item if printed.

#### Example
```jinja2
{% set even_numbers = [2,3,4,6,8,9,10]  %}
{% do even_numbers.pop(1) %}
{{even_numbers.pop(4)}}
{{even_numbers}}
```

#### Output
```jinja2
9
[2, 4, 6, 8, 10]
```

