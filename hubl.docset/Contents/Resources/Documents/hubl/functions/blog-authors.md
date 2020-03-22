# blog_authors
The `blog_authors` function returns a sequence of blog author objects for the specified blog, sorted by slug ascending. This sequence can be stored in a variable and iterated through to create custom author post filters.

The number of live posts by each author can be accessed with author.live\_posts.

#### Example
```jinja2
{{ blog_authors('default', 250) }}

{% set my_authors = blog_authors('default', 250) %}
<ul>
{% for author in my_authors %}
<li><a href="{{ blog_author_url(group.id, author.slug) }}">{{ author }}</a></li>
{% endfor %}
</ul>
```

#### Output
```jinja2
[ Brian Halligan, Dharmesh Shah, Katie Burke, Kipp Bodnar]

<ul>
    <li><a href="http://blog.hubspot.com/marketing/author/brian-halligan">Brian Halligan</a></li></li>
    <li><a href="http://blog.hubspot.com/marketing/author/dharmesh-shah">Dharmesh Shah</a></li></li>
    <li><a href="http://blog.hubspot.com/marketing/author/katie-burke">Katie Burke</a></li></li>
    <li><a href="http://blog.hubspot.com/marketing/author/kipp-bodnar">Kipp Bodnar</a></li></li>
</ul>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| selected_blog | Blog id or 'default' | Specifies which blog to use. | 
| limit | Integer | Sets the limit on the number of authors fetched. | 

The first line of the example below demonstrates how the function returns a sequence of author objects. The rest of the example demonstrates a use case of saving a sequence into a variable and then iterating though the author objects, printing a set of author listing links. The example assumes that the blog has 4 authors.
