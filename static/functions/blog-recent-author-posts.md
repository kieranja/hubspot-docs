# blog_recent_author_posts
The `blog_recent_author_posts` function returns a sequence of blog post objects for the specified author, sorted by most recent. This sequence of posts can be saved into a variable and iterated through with a for loop, creating a custom post listing of posts by a particular author.

The function takes three parameters. The first parameter specifies which blog to collect posts by an author from. The value should be `'default'` or the blog ID of a particular blog (available in the URL of the Blog dashboard). The second parameter specifies which author to use. This parameter can use the **`content.blog_post_author.slug`** to use the author of the current post or accepts a lowercase hyphenated name such as `'brian-halligan'`. The third parameter specifies how many posts are retrieved.

The first line of the example below demonstrates how the function returns a sequence of posts by an author. In this example, rather than specifying an exact author name, the current post author is used. The sequence is saved in a variable and looped through. [Any blog post variables](/docs/hubl/variables#blog-variables) should use the name of the individual loop item rather than `content.`. In the example, `author_post.name` is used. This technique can be used, not only on blog templates, but also regular pages.

#### Example
```jinja2
{{ blog_recent_author_posts('default', content.blog_post_author.slug, 5 ) }}
{% set author_posts = blog_recent_author_posts('default', content.blog_post_author.slug, 5) %}
{% for author_post in author_posts %}
    <div class="post-title">{{ author_post.name }}</div>
{% endfor %}
```

#### Output
```jinja2
[Post by author title 1, Post by author title 2, Post by author title 3, Post by author title 4, Post by author title 5]

<div class="post-title">Post by author title 1</div>
<div class="post-title">Post by author title 2</div>
<div class="post-title">Post by author title 3</div>
<div class="post-title">Post by author title 4</div>
<div class="post-title">Post by author title 5</div>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| selected_blog | Blog id or 'default' | Specifies which blog to use. | 
| author_slug | String | Specifies which author to filter on. | 
| limit | Integer | Specifies the number of posts to add to the sequence up to a limit of 200. | 

