# cycle
The cycle tag can be used within a for loop to cycle through a series of string values and print them with each iteration. One of the most practical applications to this technique is applying alternating classes to your blog posts in a listing. This tag can be used on more than two values and will repeat the cycle if there are more loop iterations than cycle values. In the example below, a class of `odd` and `even` are applied to posts in a listing (the example assumes that there are 5 posts in the loop).

Please note that there are **no spaces** between the comma-separated cycle string values.

#### Example
```jinja2
{% for content in contents %}
    <div class="post-item {% cycle 'odd','even' %}">Blog post content</div>
{% endfor %}
```

#### Output
```jinja2
<div class="post-item odd">Blog post content</div>
<div class="post-item even">Blog post content</div>
<div class="post-item odd">Blog post content</div>
<div class="post-item even">Blog post content</div>
<div class="post-item odd">Blog post content</div>
```

