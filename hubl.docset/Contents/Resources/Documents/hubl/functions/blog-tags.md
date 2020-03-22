# blog_tags
The `blog_tags` function returns a sequence of the 250 most blogged-about tags (based on number of associated blog posts) for the specified blog, sorted by blog post count.  
  
This sequence can be stored in a variable and iterated through to create custom tag post filters. The number of posts for each tag can be accessed with `tag.live_posts`.

This function accepts two parameters. The first parameter specifies which blog to fetch tags from. The second parameter sets a limit on the number of tags fetched.

The first line of the example below demonstrates how the function returns a sequence of tag objects. The rest of the example demonstrates a use case of saving a sequence into a variable and then iterating though the tag objects, printing a set of author tag links. The example assumes that the blog has 4 tags.

#### Example
```jinja2
{{ blog_tags('default', 250) }}

{% set my_tags = blog_tags('default', 250) %}
<ul>
{% for item in my_tags %}
<li><a href="{{ blog_tag_url(group.id, item.slug) }}">{{ item }}</a></li>
{% endfor %}
</ul>
```

#### Output
```jinja2
[ Blogging, Inbound Marketing, SEO, Social Media]

<ul>
    <li><a href="http://blog.hubspot.com/marketing/tag/blogging"></a></li></li>
    <li><a href="http://blog.hubspot.com/marketing/tag/inbound-marketing">Inbound Marketing</a></li></li>
    <li><a href="http://blog.hubspot.com/marketing/tag/seo">SEO</a></li>
    <li><a href="http://blog.hubspot.com/marketing/tag/social-media">Social Media</a></li></li>
</ul>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| selected_blog | Blog id or 'default'	 | Specifies which blog to use. | 
| limit | Integer | Max tags to return. | 

