# insert
Places an element into a list at the specific index provided.

This function accepts 2 parameters:

- `Index`: the position where an element is to be inserted
- `Element`: the item to be inserted

#### Example
```jinja2
{% set even_numbers = [2,4,8,10]  %}
{% do even_numbers.insert(2,6) %}
{{even_numbers}}
```

#### Output
```jinja2
[2, 4, 6, 8, 10]
```

