# shuffle
Randomizes the order of iteration through a sequence. The example below shuffles a standard blog loop.

#### Example
```jinja2
{% for content in contents|shuffle %}
<div class="post-item">Markup of each post</div>
{% endfor %}
```

#### Output
```jinja2
<div class="post-item">Markup of each post 5</div>
<div class="post-item">Markup of each post 3</div>
<div class="post-item">Markup of each post 1</div>
<div class="post-item">Markup of each post 2</div>
<div class="post-item">Markup of each post 4</div>
```

