# random
Return a random item from the sequence. The random function does NOT break caching. It is best used for scenarios where you are okay with the random item is selected when the server-side cache refreshes, not on page load. If you do need to return a random item every page load you should use javascript.

#### Example
```jinja2
{% for content in contents|random %}
<div class="post-item">Post item markup</div>
{% endfor %}
```

#### Output
```jinja2
<div class="post-item">Random post</div>
```

