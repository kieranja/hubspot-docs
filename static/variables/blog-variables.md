# Blog variables
The following variables are available for blog templates. Some variables are only available for post listings, while others may only be available for blog posts.
| Variable | Type | Description | 
|  ------  |  ------  |  ------  | 
| blog_author | String | This variable contains blog author information for blog author listing pages. It can be used to create conditional logic to render markup for blog author listings. It also contains the following properties:blog_author.avatar, blog_author.bio, blog_author.display_name, blog_author.email, blog_author.facebook, blog_author.google_plus, blog_author.has_social_profiles, blog_author.linkedin, blog_author.twitter, and blog_author.website | 
| content.blog_post_author | String | This variable contains individual blog post author information for a given post. It contains the following properties:content.blog_post_author.avatar, content.blog_post_author.bio, content.blog_post_author.display_name, content.blog_post_author.email, content.blog_post_author.facebook, content.blog_post_author.google_plus, content.blog_post_author.has_social_profiles, content.blog_post_author.linkedin, content.blog_post_author.slug, content.blog_post_author.twitter, and content.blog_post_author.website | 
| content.blog | String | An alias for group. | 
| content.comment_count | Integer | The number of comments for the current blog post.  | 
| content.comment_list | String | A list of the comments for the current blog post. | 
| current_page_num | Integer | The integer index of the current page of blog posts in the view.  | 
| content.featured_image | String | The source URL of the featured image, selected when the blog was published. | 
| content.featured_image_alt_text | String | The alt text of the featured image. | 
| last_page_num | Integer | The integer index of the last page of blog posts in the view. | 
| next_page_num | Integer | The integer index of the next page of blog posts in the view. | 
| content.next_post_featured_image | String | The URL of the featured image of the next blog post, if one exists. | 
| content.next_post_name | String | The name of the next blog post, if one exists. | 
| content.next_post_slug | String | The URL slug of the next blog post, if one exists. | 
| content.post_body | String | The body of the blog post. | 
| content.post_list_content | String | The body blog post content, modified for the listing page. The final output is affected by summary settings in Settings > Website > Blog. If featured images are enabled in settings, this variable will remove any images above the read more separator automatically. | 
| content.post_list_summary_featured_image | String | The featured image for listing layouts. This variable is affected by the settings in Settings > Website > Blog. | 
| content.post_summary | String | The blog post summary. This content is determined by the read more separator in the blog editor. | 
| content.previous_post_featured_image | String | The URL of the featured image of the previous blog post, if one exists. | 
| content.previous_post_name | String | The name of the previous blog post, if one exists. | 
| content.previous_post_slug | String | The URL slug of the previous blog post, if one exists. | 
| content.publish_date_localized | String | A string representing the date/time when the blog post was published, formatted according to the blog's language and date formatting settings. | 
| content.simple_list_page | Boolean | A boolean to indicate whether the requested page is the 'all posts' page containing links to all blog posts. | 
| contents | String | Contents is a sequence of your blog posts that are iterated through using a for loop, available on blog listing pages (is_listing_view).  | 
| contents.total_count | Integer | Total number of posts in a listing (regular, topics, authors, etc.). | 
| contents.total_page_count | Integer | Total number of pages of posts based on your number of posts per page. | 
| contents_topics | String | Get a list of all blog topics in the contents sequence of posts. | 
| group | Dict | The dictionary containing variables that pertain to an entire blog. | 
| group.absolute_url | String | The base URL of a blog. | 
| group.allow_comments | Boolean | Evaluates to True, if comments are allowed. | 
| group.description | String | The meta description of the blog from Settings > Website > Blog. Used for the meta description on certain listing pages. | 
| group.header | String | The header of the blog. | 
| group.html_title | String | The title of this blog as it should appear in the <title> tag. | 
| group.id | String | The unique ID of a blog. This ID can be found in the URL of the Blog Dashboard for a particular blog. | 
| group.public_title | String | The title of this blog as it should appear at the top of rendered pages. | 
| group.slug | String | The path to this blog. | 
| topic | Dict | The topic variable can be used to render markup for a topic listing. It also contains the properties: topic.name and topic.slug. | 

