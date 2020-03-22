# reverse
Reverses the order of items in a list. Does not take any parameters. To reverse an object or return an iterator to iterate over the list in reverse, use [`|reverse`](/docs/hubl/filters#reverse)

#### Example
```jinja2
{% set numbers = [1,2,3,4] %}
{% do numbers.reverse() %}
{{numbers}}
```

#### Output
```jinja2
[4, 3, 2, 1]
```

