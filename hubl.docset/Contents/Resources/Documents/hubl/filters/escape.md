# escape
Convert the characters &amp;, &lt;, &gt;, ‘, and ” in string to HTML-safe sequences. Use this if you need to display text that might contain such characters in HTML. Marks return value as markup string.

#### Example
```jinja2
{% set escape_string = "<div>This markup is printed as text</div>" %} 
{{ escape_string|escape }}
```

#### Output
```jinja2
<div>This markup is printed as text</div>
```

