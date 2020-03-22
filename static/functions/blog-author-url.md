# blog_author_url
The `blog_author_url` function returns a full URL to the specified blog author's listing page.

The example below shows how this function can be used as an anchor's `href`. This can be combined with `blog_authors` as shown in that function's examples.

#### Example
```jinja2
<a href="{{ blog_author_url('default', 'brian-halligan') }}">Brian Halligan</a>
```

#### Output
```jinja2
<a href="http://blog.hubspot.com/marketing/author/brian-halligan">Brian Halligan</a>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| selected_blog | Blog id or 'default' | Specifies which blog the author's listing page exists in. | 
| author_slug | String or HubL Var | Specifies which author to link to. Can use either content.blog_post_author.slug or a lowercase hyphenated name. Example: 'jane-doe'. | 

