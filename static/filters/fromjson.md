# fromjson
Converts a JSON string to an object.

#### Example
```jinja2
{% set obj ='{ "name":"Brian","role":"Owner" }' %}
{{ obj|fromjson }}
```

#### Output
```jinja2
{role=Owner, name=Brian}
```

