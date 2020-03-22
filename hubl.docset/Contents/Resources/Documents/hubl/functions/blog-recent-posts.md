# blog_recent_posts
The `blog_recent_posts` function returns a sequence of blog post objects for the specified blog, sorted by most recent first. This sequence of posts can be saved into a variable and iterated through with a for loop, creating a custom post listing of your most popular posts.

The function takes two parameters. The first parameter specifies which blog to collect popular posts from. The value should be `'default'` or the blog ID of a particular blog (available in the URL of the Blog dashboard). The second parameter specifies how many posts are retrieved.

The first line of the example below demonstrates how the function returns a sequence. The sequence is saved in a variable and looped through. [Any blog post variables](/docs/hubl/variables#blog-variables) should use the name of the individual loop item rather than `content.`. In the example, `rec_post.name` is used. This technique can be used, not only on blog templates, but also regular pages.

#### Example
```jinja2
{{ blog_recent_posts('default', 5) }}
{% set rec_posts = blog_recent_posts('default', 5) %}
{% for rec_post in rec_posts %}
    <div class="post-title">{{ rec_post.name }}</div>
{% endfor %}
```

#### Output
```jinja2
[Recent post title 1, Recent post title 2, Recent post title 3, Recent post title 4, Recent post title 5]

<div class="post-title">Recent post title 1</div>
<div class="post-title">Recent post title 2</div>
<div class="post-title">Recent post title 3</div>
<div class="post-title">Recent post title 4</div>
<div class="post-title">Recent post title 5</div>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| selected_blog | Blog id or 'default' | Specifies which blog to use. | 
| limit | Integer | Specifies the number of posts to add to the sequence, maximum 200. | 

