# type
This function accepts one argument and returns the type of an object. The return value is one of "bool", "datetime", "dict", "float", "int", "list", "long", "null", "str" or "tuple".

#### Example
```jinja2
{{ type("Blog") }}
{% set my_type = type("Blog") %}
<p>{{my_type}}</p>
```

#### Output
```jinja2
<p>str</p>
```

