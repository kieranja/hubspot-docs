# pprint
Pretty print a variable. This prints the type of variable and other info that is useful for debugging.

#### Example
```jinja2
{% set this_var ="Variable that I want to debug" %} 
{{ this_var|pprint }}
```

#### Output
```jinja2
(String: Variable that I want to debug)
```

