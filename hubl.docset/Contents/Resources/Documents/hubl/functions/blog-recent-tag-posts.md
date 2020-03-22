# blog_recent_tag_posts
The `blog_recent_tag_posts` function returns a sequence of blog post objects for a specified tag or tags, sorted by most recent first. This sequence of posts can be saved into a variable and iterated through with a for loop, creating a custom post listing of posts by a particular tag or tags.

The function takes three parameters. The first parameter specifies which blog to collect posts from. The value should be `'default'` or the blog ID of a particular blog (available in the URL of the Blog dashboard).  
  
The second parameter specifies which tags to use, either a single tag or an array of up to 10 tags separated by commas. This parameter can use **`tag.slug`** for a particular tag from `content.tag_list` or accepts a lowercase hyphenated name such as `'marketing-tips'`.   
  
The third parameter specifies how many posts are retrieved.

The first line of the example below demonstrates how the function returns a sequence of posts by tag. The second line shows the function used to save a sequence in a variable which is then looped through. [Any blog post variables](/docs/hubl/variables#blog-variables) should use the name of the individual loop item rather than `content.`. In the example, `tag_post.name` is used. This technique can be used, not only on blog templates, but also regular pages.

You can use this function as the foundation for a related posts section of an individual blog post layout. To learn more about creating a related posts section, [check out this tutorial](/tutorials/creating-a-related-post-listing).

#### Example
```jinja2
{{ blog_recent_tag_posts('default', 'marketing-tips', 5 ) }}
{% set tag_posts = blog_recent_tag_posts('default', ['marketing', 'fun', 'inbound'], 3) %}
{% for tag_post in tag_posts %}
    <div class="post-title">{{ tag_post.name }}</div>
{% endfor %}
```

#### Output
```jinja2
[Post about Marketing 1, Post about Marketing 2, Post about Marketing 3, Post about Marketing 4, Post about Marketing 5]

<div class="post-title">Post about Marketing</div>
<div class="post-title">Post about Fun</div>
<div class="post-title">Post about Inbound</div>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| selected_blog | Blog id or 'default' | Specifies which blog to use. | 
| tag_slug | String | Specifies which tag to filter on. | 
| limit | Integer | Specifies the number of posts to add to the sequence. | 

