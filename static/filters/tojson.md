# tojson
Writes an object as a JSON string.

#### Example
```jinja2
{% for content in contents %}
  {{ content.blog_post_author|tojson }}
{% endfor %}
```

