# add
Adds a numeric value to another numeric value. This filter functions the same as the [+ operator](/docs/hubl/operators-and-expression-tests#math). The parameter in parentheses is the addend that you are combining with your initial numeric value.

#### Example
```jinja2
{% set my_num = 40 %} 
{{ my_num|add(13) }}
```

#### Output
```jinja2
53
```

