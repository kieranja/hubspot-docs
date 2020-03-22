# striptags
Strip SGML/XML tags and replace adjacent whitespace by one space. This filter can be used to remove any HTML tags from a variable.

#### Example
```jinja2
{% set some_html = "<div><strong>Some text</strong></div>" %} 
{{ some_html|striptags }}
```

#### Output
```jinja2
  some text  
```

