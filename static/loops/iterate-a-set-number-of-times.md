# Iterate a set number of times
Sometimes you want to iterate a set number of times, this can be useful in generating HTML or CSS. You can do this using the range function.

#### Example
```jinja2
{% for x in range(0,5) %}
	{{loop.index}}
{% endfor %}
```

#### Output
```jinja2
1 2 3 4 5
```

