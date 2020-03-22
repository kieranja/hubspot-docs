# rejectattr
Filters a sequence of objects by applying a test to an attribute of an object and rejecting the ones with the test succeeding.
| Parameter | Description | 
|  ------  |  ------  | 
| attribute_name `Required` | Specifies the attribute to select. You can access nested attributes using dot notation. | 
| exp_test `Optional` | The expression to test | 
| val `Optional` | Value to test against. | 


#### Example
```jinja2
{% for content in contents|rejectattr('post_list_summary_featured_image') %}
<div class="post-item">
{% if content.post_list_summary_featured_image %}
    <div class="hs-featured-image-wrapper">
            <a href="{{content.absolute_url}}" title="" class="hs-featured-image-link">
            <img src="{{ content.post_list_summary_featured_image }}" class="hs-featured-image">
            </a>
    </div>
{% endif %}
{{ content.post_list_content|safe }}
</div>
{% endfor %}
```

#### Output
```jinja2
<div class="post-item">Post with no featured image</div>
<div class="post-item">Post with no featured image</div>
<div class="post-item">Post with no featured image</div>
```

