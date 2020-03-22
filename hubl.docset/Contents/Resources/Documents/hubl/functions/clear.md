# clear
Removes all items from a list. Unlike `pop()`, it does not return anything.

#### Example
```jinja2
{% set words = ["phone","home"] %}
{% do words.clear() %}
{{words}}
```

#### Output
```jinja2
[]
```

