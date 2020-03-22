# urlencode
Escapes a url encodes a string using UTF-8 formatting.

#### Example
```jinja2
{% text "encode" value="Escape & URL encode this string", label="Enter slug", export_to_template_context=True %} 
{{ widget_data.encode.value|urlencode }}
```

#### Output
```jinja2
Escape+%26+URL+encode+this+string 
```

