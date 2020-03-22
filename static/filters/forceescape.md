# forceescape
Strictly enforce HTML escaping. In HubSpot's environment there isn't really a use case for double escaping, so this is generally behaves the same as the escape filter.

#### Example
```jinja2
{% set escape_string = "<div>This markup is printed as text</div>" %} 
{{ escape_string|forceescape }}
```

#### Output
```jinja2
<div>This markup is printed as text</div>
```

