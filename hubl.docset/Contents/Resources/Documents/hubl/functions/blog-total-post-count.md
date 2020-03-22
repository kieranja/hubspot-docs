# blog_total_post_count
This function returns the total number of published posts in the specified blog. If no parameter is specified, it will count your default blog posts. Alternatively, you can specify `'default'` or a blog ID of a different blog to count. The blog ID is available in the URL of your blog dashboard for a particular blog.

#### Example
```jinja2
{{ blog_total_post_count }} 
{{ blog_total_post_count(359485112) }}
```

#### Output
```jinja2
16
54
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| selected_blog | Blog id or 'default' | Specifies which blog to count. | 

