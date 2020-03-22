# escapejson
Escapes strings so that they can be used as JSON values.

#### Example
```jinja2
{% set your_string = '\tTesting a \"quote for the week\"'
{{ your_string|escapejson }}
```

#### Output
```jinja2
\\tTesting a \\\"quote for the week\\\"
```

