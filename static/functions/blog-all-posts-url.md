# blog_all_posts_url
The `blog_all_posts_url` function returns a full URL to the listing page for all blog posts for the specified blog.

The example below shows how this function can be used as an anchor's `href`.

#### Example
```jinja2
<a href="{{ blog_all_posts_url('default') }}">All Marketing blog posts</a>
```

#### Output
```jinja2
<a href="http://www.hubspot.com/marketing/all">All Marketing blog posts</a>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| selected_blog | Blog id or 'default'	 | Specifies which blog to use. | 

