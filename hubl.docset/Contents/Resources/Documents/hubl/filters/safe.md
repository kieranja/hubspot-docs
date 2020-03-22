# safe
Mark the value as safe which means that in an environment with automatic escaping enabled this variable will not be escaped.

#### Example
```jinja2
{{ content.post_list_content|safe }} 
```

#### Output
```jinja2
<p>HTML post content that is not escaped. </p>
```

