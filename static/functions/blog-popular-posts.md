# blog_popular_posts
The `blog_popular_posts` function renders a set number of popular posts into a sequence. This sequence of posts can be saved into a variable and iterated through with a for loop, creating a custom post listing of your most popular posts.

The function takes up to 3 parameters. The first parameter specifies which blog to collect popular posts from. The value should be `'default'` or the blog ID of a particular blog (available in the URL of the Blog dashboard). The second (optional) parameter specifies how many posts to retrieve - if not specified, defaults to 10. The third (optional) parameter specifies a topic by which to filter the results - if specified, only popular posts associated with this topic will be returned.

The first line of the example below demonstrates how the function returns a sequence. The sequence is saved in a variable and looped through. [Any blog post variables](/docs/hubl/variables#blog-variables) should use the name of the individual loop item rather than `content.`. In the example, `pop_post.name` is used. This technique can be used, not only on blog templates, but also regular pages.

#### Example
```jinja2
{% set pop_posts = blog_popular_posts('default', 5, 'marketing-tips') %}
{% for pop_post in pop_posts %}
    <div class="post-title">{{ pop_post.name }}</div>
{% endfor %}
```

#### Output
```jinja2
[Popular post title 1, Popular post title 2, Popular post title 3, Popular post title 4, Popular post title 5]

<div class="post-title">Popular post title 1</div>
<div class="post-title">Popular post title 2</div>
<div class="post-title">Popular post title 3</div>
<div class="post-title">Popular post title 4</div>
<div class="post-title">Popular post title 5</div>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| selected_blog | Blog id or 'default' | Specifies which blog to use. | 
| limit | Integer | Specifies the number of posts to add to the sequence up to a limit of 200. | 
| tag_slug | String | Optional tag to filter posts by. | 
| time_frame | String | Optional timeframe to filter posts by (must be one of 'popular_all_time', 'popular_past_year', 'popular_past_six_months', 'popular_past_month'). | 

