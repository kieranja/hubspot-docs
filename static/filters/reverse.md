# reverse
Reverse the object or return an iterator the iterates over it the other way round. To reverse a list use [.reverse()](/docs/hubl/functions#reverse)

#### Example
```jinja2
{% set nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10] %}
{% for num in nums|reverse %}
{{ num }}
{% endfor %}
```

#### Output
```jinja2
10 9 8 7 6 5 4 3 2 1
```

