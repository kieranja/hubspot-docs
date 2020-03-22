# selectattr
Filters a sequence of objects by applying a test to an attribute of an object and only selecting the ones with the test succeeding.
| Parameter | Description | 
|  ------  |  ------  | 
| attribute_name `Required` | Specifies the attribute to select. You can access nested attributes using dot notation. | 
| exp_test `Optional` | The expression to test | 
| val `Optional` | Value to test against. | 


#### Example
```jinja2
{% for content in contents|selectattr('post_list_summary_featured_image') %}
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
<div class="post-item">
  <div class="hs-featured-image-wrapper">
     <a href="http://blog.hubspot.com/marketing/how-to-get-a-job" title="" class="hs-featured-image-link">
       <img src="//cdn2.hubspot.net/hub/53/hubfs/00-Blog-Related_Images/landing-a-job-featured-image.png?t=1431452322770&width=761" class="hs-featured-image">
     </a>
   </div>
Post with featured image
</div>
```

