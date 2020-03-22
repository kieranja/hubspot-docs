# escapejs
Escapes strings so that they can be safely inserted into a JavaScript variable declaration.

#### Example
```jinja2
{% set escape_string = "\tThey said 'This string can safely be inserted into JavaScript.'" %}
{{ escape_string|escapejs }}
```

#### Output
```jinja2
They said \'\\tThis string can safely be inserted into JavaScript.\'
```

