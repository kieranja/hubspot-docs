# Functions
## 
Functions in HubL are similar to filters in that they accept parameters and generate a value; however, not all functions need to be applied to an initial template value. Instead they interact with other areas of your HubSpot environment.

## append
Adds a single item to the end of a list.

#### Example
```jinja2
{% set numbers_under_5 = [1,2,3] %}
{% do numbers_under_5.append(4) %}
{{numbers_under_5}}
```

#### Output
```jinja2
[1, 2, 3, 4]
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| item | Any | Item to be appended to the list. | 


## blog_all_posts_url
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


## blog_author_url
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


## blog_authors
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

## blog_by_id
The `blog_by_id` function returns a blog by ID. The below example code shows this function in use to generate a hyperlinked list item.

#### Example
```jinja2
{% set my_blog = blog_by_id(47104297) %}
<ul>
    <li>
        <a href="{{ my_blog.absolute_url }}">{{my_blog.html_title}}</a>
	</li>
</ul>
```

#### Output
```jinja2
<ul>
    <li>
        <a href="http://blog.bikinginearnest.com/outdoors">Outdoor biking for the earnest</a>
    </li>
</ul>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| selected_blog | Integer | Numeric ID of a blog. | 


## blog_page_link
The `blog_page_link` function generates the URL of a paginated view of your blog listing. The function takes a numeric parameter, which allows you to generate links for current, next, previous, or a specific page. This function is generally used in the `href` attribute of pagination anchor tags and must be used on your blog listing template.

The examples below show this function in use as an anchor `href`. The first example outputs the current page. The second example takes the number 7 parameter to specify the seventh page. The third example uses the `next_page_num` variable to generate a link that is relative to the current page number (you can also use the `last_page_num` variable for the previous page). The final example uses the `current_page_num` variable and a `+` operator to create a link that is 4 greater than the current page.

#### Example
```jinja2
<a href="{{ blog_page_link(current_page_num) }}">Current page</a>
<a href="{{ blog_page_link(7) }}">Page 7</a>
<a href="{{ blog_page_link(next_page_num) }}">Next</a>
<a href="{{ blog_page_link(current_page_num + 4) }}">Page Plus 4</a>
```

#### Output
```jinja2
<a href="http://designers.hubspot.com/blog/page/1">Page 1</a>
<a href="http://designers.hubspot.com/blog/page/7">Page 7</a>
<a href="http://designers.hubspot.com/blog/page/2">Next</a>
<a href="http://designers.hubspot.com/blog/page/5">Page Plus 4</a>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| page | Number or HubL Var | Page Number used to generate URL or HubL variable for page number. | 


## blog_popular_posts
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


## blog_post_archive_url
The `blog_post_archive_url` function returns a full URL to the archive listing page for the given date values on the specified blog. This function has two required parameters and two optional parameters. The first parameter is a blog ID or simply the keyword `'default'`. The second is the year of archived posts you'd like to display.

The optional parameters include the month and day of archived posts you'd like to display, respectively.

The example below shows how this function can be used as an anchor's `href`.

#### Example
```jinja2
<a href="{{ blog_post_archive_url('default', 2017, 7, 5) }}">Posts from July 5th, 2017</a>
```

#### Output
```jinja2
<a href="http://blog.hubspot.com/marketing/archive/2017/07/05">Posts from July 5th, 2017</a>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| selected_blog | Blog id or 'default' | Specifies which blog to use. | 
| year | Integer | The year. | 
| month | Integer | The optional month. | 
| day | Integer | The optional day. | 


## blog_recent_author_posts
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


## blog_recent_posts
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


## blog_recent_tag_posts
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


## blog_tag_url
The `blog_tag_url` function returns a full URL to the specified blog tag's listing page.

This function accepts two parameters. The first parameter specifies which blog the tag's listing page exists in. The second parameter specifies which tag to link. This parameter can use the **`topic.slug`** for a particular tag from `content.topic_list` or accepts a lowercase hyphenated name such as `'marketing-tips'`.

The example below shows how this function can be used as an anchor's href. This can be combined with `blog_topics` as shown in that function's examples.

#### Example
```jinja2
<a href="{{ blog_tag_url('default', 'inbound-marketing') }}">Inbound Marketing</a>
```

#### Output
```jinja2
<a href="http://blog.hubspot.com/marketing/tag/inbound-marketing">Inbound Marketing</a>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| selected_blog | Blog id or 'default'	 | Specifies which blog to use. | 
| tag_slug | String | Specifies which tag to link to. | 


## blog_tags
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


## blog_total_post_count
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


## clear
Removes all items from a list. Unlike `pop()`, it does not return anything.

#### Example
```jinja2
{% set words = ["phone","home"] %}
{% do words.clear() %}
{{words}}
```

#### Output
```jinja2
[]
```


## color_variant
This function lightens or darkens a HEX value or color variable by a set amount. The first parameter is the hex color (for example ("#FFDDFF") or a variable storing a HEX value. The second parameter is the amount to adjust it by, from 0 to 255. This function can be used in CSS files to create a color variation. Another good use case is to use it with a color parameter of a color module, to allow users to specify a primary color that automatically generates a color variation.

In the example below, the HEX color #3A539B is stored in a variable called `base_color`. The color is modified by -80 resulting in a darker blue (#00034B).

#### Example
```jinja2
{% set base_color ="#3A539B" %} 
{{ color_variant(base_color, -80) }}
```

#### Output
```jinja2
#00034b
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| base_color | HEX color string | The starting color to be altered (Example: #F7F7F7). | 
| brightness_offset | Integer | A positive or negative number used to lighten or darken the base color. | 


## content_by_id
The **`content_by_id`** function returns a landing page, website page or blog post by ID. The only parameter accepted by this function is a numeric content ID.

The below example code shows this function in use to generate a hyperlinked list item.

#### Example
```jinja2
{% set my_content = content_by_id(4715624297) %}
<ul>
    <li>
        <a href="{{ my_content.absolute_url }}">{{my_content.title}}</a>
    </li>
</ul>
```

#### Output
```jinja2
<ul>
    <li>
        <a href="http://www.hubspot.com/blog/articles/kcs_article/email/how-do-i-create-default-values-for-my-email-personalization-tokens">How do I create default values for my email or smart content personalization tokens?</a>
    </li>
</ul>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| id | Id | The id of the content to look up. | 


## content_by_ids
Given a list of content IDs, returns a dict of landing page, website page or blog posts matching those IDs.

This function takes one parameter, a list of page or blog post IDs to look up, placed within an array. Up to 100 content objects can be passed. The below example code shows this function in use to generate a list of hyperlinked list items.

#### Example
```jinja2
{% set contents = content_by_ids([4715624297, 4712623297, 5215624284]) %}
<ul>
{% for content in contents %}
    <li>
        <a href="{{ content.absolute_url }}">{{content.title}}</a>
    </li>
    {% endfor %}
</ul>
```

#### Output
```jinja2
<ul>
    <li>
        <a href="http://www.hubspot.com/blog/articles/kcs_article/email/how-do-i-create-default-values-for-my-email-personalization-tokens">How do I create default values for my email or smart content personalization tokens?</a>
    </li>
    <li>
        <a href="https://blog.hubspot.com/marketing/content-marketing-strategy-guide">Content Marketing Strategy: A Comprehensive Guide for Modern Marketers</a>
    </li>
</ul>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| ids | List | A list of page or blog post ids to look up. Up to 100 content objects can be passed. | 


## copy
Return a shallow copy of the list. Equivalent to `a[:]`.

A *shallow copy* constructs a new compound object and then (to the extent possible) inserts *references* into it to the objects found in the original.

#### Example
```jinja2
{% set a = ["ham"] %}
{% set b = a.copy() %}
a: {{a}}

b: {{b}}

  After Append
{% do a.append("swiss") %}
a: {{a}}

b: {{b}}
```

#### Output
```jinja2
a: [ham]

b: [ham]

  After Append

a: [ham, swiss]

b: [ham]
```


## count
Returns the number of times a variable exists in a list.

#### Example
```jinja2
{% set attendees = ["Jack","Jon","Jerry","Jessica"] %}
{% set jon_count = attendees.count("Jon") %}
There are {{jon_count}} Jon's in the list.
<p>After append:</p>
{% do attendees.append("Jon") %}
{% set jon_count_after_append = attendees.count("Jon") %}
There are now {{jon_count_after_append}} Jon's in the list.
```

#### Output
```jinja2
There are 1 Jon's in the list.
<p>After append:</p>

There are now 2 Jon's in the list.
```


## crm_associations
Gets a list of CRM objects associated to an object from the HubSpot CRM. This function returns an object with the following attributes: `has_more`, `total`, `offset` and `results`.

- `has_more` indicates there are more results available beyond this batch (total &gt; offset).
- `total` is the total number of results available.
- `offset` is the offset to use for the next batch of results.
- *`results`* returns an array of the specified associated objects matching the function's parameters

For security purposes, only Product objects can be retrieved on a publicly accessible page. Any other object type must be hosted on a page which is either [password protected](https://knowledge.hubspot.com/cos-pages-editor/how-can-i-password-protect-my-pages) or requires a [CMS Membership login](https://knowledge.hubspot.com/cms-pages-editor/control-audience-access-to-pages). Objects in the *results* array are returned as a dict of properties and values.

#### Example
```jinja2
{% set associated_contacts = crm_associations(847943847, 2, 'limit=3&years_at_company__gt=2&orderBy=email', 'firstname,email', false) %} 
{{ associated contacts }}
```

#### Output
```jinja2
{has_more=true, offset=3, total=203, results=[{firstname=Aimee, id=905, email=abanks@company.com}, {firstname=Amy, id=1056, email=abroma@company.com}, {firstname=Abigael, id=957, email=adonahu@company.com}]}
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| id | Id | Id of object to find associations from. | 
| association type id | Integer | Id of the association type to use. | 
| query | String | Query string delimited by &. All expressions are ANDed together. Supported operators are eq (default), neq, lt, lte, gt, gte, is_null and not_null. | 
| properties | String | Optional. A comma-separated list of properties to return. By default, a small set of common properties are returned. The id property is always returned. | 
| formatting | Boolean | Optional. Format values such as dates and currency according to this portal's settings. Omit or pass false for raw strings. | 


## crm_object
Gets a single object from the HubSpot CRM.

For security purposes, only Product objects can be retrieved on a publicly accessible page. Any other object type must be hosted on a page which is either [password protected](https://knowledge.hubspot.com/cos-pages-editor/how-can-i-password-protect-my-pages) or requires a [CMS Membership login](https://knowledge.hubspot.com/articles/kcs_article/cms-pages-editor/control-audience-access-to-pages). Objects are returned as a dict of properties and values.

The first parameter (required) is a string specifying the CRM object type to get (contact, product, company, deal, ticket or quote).

The second parameter (required) specifies which CRM object to get. This parameter can either be a number, or a string. If you wish to get a specific CRM object by ID, pass a number of the ID of the object. If you wish to get a CRM object by querying `crm_objects`, pass a query string, delimited by `&`. All expressions are ANDed together. Supported operators are eq (default), `neq`, `lt`, `lte`, `gt`, `gte`, `is_null` and `not_null`.

The third parameter is a comma-separated list of properties to return. By default, a small set of common properties are returned.

The final parameter specifies if values such as dates and currency should be formatted according to the portal's settings. Pass 'false' for raw values.

#### Example
```jinja2
<!-- by query -->
{% set contact = crm_object("contact", "email=contact@company.com", "firstname,lastname", false) %}
<!-- by id -->
{% set contact = crm_object("contact", 123) %}
{{ contact.firstname }}
{{ contact.lastname }}
```

#### Output
```jinja2
Brian
Halligan
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| object_type | String | Contact, product, company, deal, ticket or quote. | 
| query | String | The id of the object OR a query string, delimited by &. All expressions are ANDed together. Supported operators are eq (default), neq, lt, lte, gt, gte, is_null and not_null. | 
| properties | String | Optional. A comma-separated list of properties to return. By default, a small set of common properties are returned. The id property is always returned. | 
| formatting | Boolean | Optional. Format values such as dates and currency according to this portal's settings. Omit or pass false for raw strings. | 


## crm_objects
Gets a list of objects from the HubSpot CRM.

This function returns an object with the following attributes: `has_more`, `total`, `offset` and `results`.

- `has_more` indicates there are more results available beyond this batch (total &gt; offset).
- `total` is the total number of results available.
- `offset` is the offset to use for the next batch of results.
- *`results`* returns an array of the specified objects matching the function's parameters.

Results can be sorted using at least one order parameter in the query. For example, `crm_objects("contact", "firstname=Bob&order=lastname&order=createdate")` will order contacts with the first name `"Bob"` by last name and then by `createdate`. To reverse a sort, prepend `-` to the property name like `order=-createdate`.  
For security purposes, only Product objects can be retrieved on a publicly accessible page. Any other object type must be hosted on a page which is either [password protected](https://knowledge.hubspot.com/cos-pages-editor/how-can-i-password-protect-my-pages) or requires a [CMS Membership login](https://knowledge.hubspot.com/articles/kcs_article/cms-pages-editor/control-audience-access-to-pages). Objects in the `results` array are returned as a dict of properties and values.

#### Example
```jinja2
{% set objects = crm_objects("contact", "firstname__not_null=&limit=3", "firstname,lastname") %} 
{{ objects }}
```

#### Output
```jinja2
{has_more=true, offset=3, total=331, results=[{firstname=Brian, id=44151, lastname=Halligan}, {firstname=Dharmesh, id=44051, lastname=Shah}, {firstname=George, id=88551, lastname=Washington}]}
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| object_type | String | Contact, product, company, deal, ticket or quote. | 
| query | String | A query string, delimited by &. All expressions are ANDed together. Supported operators are eq (default), neq, lt, lte, gt, gte, is_null and not_null. | 
| properties | String | A comma-separated list of properties to return. By default, a small set of common properties are returned. The id property is always returned. | 
| formatting | Boolean | Format values such as dates and currency according to this portal's settings. Omit or pass false for raw strings. | 


## cta
Because CTA modules have so many parameters that contain variations of their code, you can use the CTA function to easily generate a particular CTA in a template, page, or email. This function is what the rich text editor uses when you add a CTA via the editor.

#### Example
```jinja2
{{ cta('ccd39b7c-ae18-4c4e-98ee-547069bfbc5b')  }} 
{{ cta('ccd39b7c-ae18-4c4e-98ee-547069bfbc5b', 'justifycenter') }}
```

#### Output
```jinja2
<span class="hs-cta-wrapper" id="hs-cta-wrapper-ccd39b7c-ae18-4c4e-98ee-547069bfbc5b"> 
    <span class="hs-cta-node hs-cta-ccd39b7c-ae18-4c4e-98ee-547069bfbc5b" id="hs-cta-ccd39b7c-ae18-4c4e-98ee-547069bfbc5b" style="visibility: visible;">
        <a id="cta_button_158015_19a9097a-8dff-4181-b8f7-955a47f29826" class="cta_button " href="//cta-service-cms2.hubspot.com/ctas/v2/public/cs/c/?cta_guid=19a9097a-8dff-4181-b8f7-955a47f29826&placement_guid=ccd39b7c-ae18-4c4e-98ee-547069bfbc5b&portal_id=158015&redirect_url=APefjpH34lXcq1H4FhyHhE3DNeHPNigbBluiv6t07-N80GLkyj2Dn9PizhW8bo4ecrS47RmyslLg7QQKWLG7n2oNkvrumL9dWUjMMEjVYvStZ-IMyulMBvdU8AddI6nFXL0G_VPP_VXmnFi66RKPPjPvx6kbyPO6k566noP4CTZMyADHkGsGBf4S95YdTNtTTFabShT62cVAiV_oWlXbpfPWQc4G3IvkoDoAhmpQVW-ggUcKa4Ft_5A&hsutk=683eeb5b499fdfdf469646f0014603b4&utm_referrer=http%3A%2F%2Fwww.davidjosephhunt.com%2F%3Fhs_preview%3DNVkCLfFf-2857453560&canon=http%3A%2F%2Fwww.davidjosephhunt.com%2F-temporary-slug-63bb220d-eda6-44d0-9738-af928e787237" style="" cta_dest_link="http://www.hubspot.com/free-trial" title="Start a HubSpot trial"> Start a HubSpot trial </a>
    </span>
    <script charset="utf-8" src="//js.hscta.net/cta/current.js"></script>
    <script type="text/javascript">
        hbspt.cta.load(158015, 'ccd39b7c-ae18-4c4e-98ee-547069bfbc5b');
    </script>
</span>
<span class="hs-cta-wrapper" id="hs-cta-wrapper-ccd39b7c-ae18-4c4e-98ee-547069bfbc5b"> 
    <span class="hs-cta-node hs-cta-ccd39b7c-ae18-4c4e-98ee-547069bfbc5b" id="hs-cta-ccd39b7c-ae18-4c4e-98ee-547069bfbc5b" style="display: block; text-align: center; visibility: visible;">
        <a id="cta_button_158015_19a9097a-8dff-4181-b8f7-955a47f29826" class="cta_button " href="//cta-service-cms2.hubspot.com/ctas/v2/public/cs/c/?cta_guid=19a9097a-8dff-4181-b8f7-955a47f29826&placement_guid=ccd39b7c-ae18-4c4e-98ee-547069bfbc5b&portal_id=158015&redirect_url=APefjpH34lXcq1H4FhyHhE3DNeHPNigbBluiv6t07-N80GLkyj2Dn9PizhW8bo4ecrS47RmyslLg7QQKWLG7n2oNkvrumL9dWUjMMEjVYvStZ-IMyulMBvdU8AddI6nFXL0G_VPP_VXmnFi66RKPPjPvx6kbyPO6k566noP4CTZMyADHkGsGBf4S95YdTNtTTFabShT62cVAiV_oWlXbpfPWQc4G3IvkoDoAhmpQVW-ggUcKa4Ft_5A&hsutk=683eeb5b499fdfdf469646f0014603b4&utm_referrer=http%3A%2F%2Fwww.davidjosephhunt.com%2F%3Fhs_preview%3DNVkCLfFf-2857453560&canon=http%3A%2F%2Fwww.davidjosephhunt.com%2F-temporary-slug-63bb220d-eda6-44d0-9738-af928e787237" style="" cta_dest_link="http://www.hubspot.com/free-trial" title="Start a HubSpot trial"> Start a HubSpot trial </a>
    </span>
    <script charset="utf-8" src="//js.hscta.net/cta/current.js"></script>
    <script type="text/javascript">
        hbspt.cta.load(158015, 'ccd39b7c-ae18-4c4e-98ee-547069bfbc5b');
    </script>
</span>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| guid | String | The ID of the CTA to render. Can be found in the URL of the details screen of the CTA. | 
| align_opt | Enumeration | Adjusts alignment of CTA. Values include justifyleft, justifycenter, justifyright, justifyfull. | 


## datetimeformat
The `datetimeformat` function works just like the [datetimeformat filter](/docs/hubl/filters#datetimeformat), but uses function syntax instead of filter syntax. It uses the same parameters to format the date. [See the complete list of formatting parameters.](/docs/hubl/filters#widget_1582313600888)

#### Example
```jinja2
{{ datetimeformat(content.publish_date_local_time, '%B %e, %Y') }} 
```

#### Output
```jinja2
May 13, 2015
```


## extend
Extend a list by appending all items from an iterable. In other words, insert all list items from one list into another list.

#### Example
```jinja2
{% set vehicles = ["boat","car","bicycle"] %}
{% set more_vehicles = ["airplane","motorcycle"] %}
{% do vehicles.extend(more_vehicles) %}
{{vehicles}}
```

#### Output
```jinja2
[boat, car, bicycle, airplane, motorcycle]
```


## file_by_id
This function returns the metadata of a file by ID. It accepts a single parameter, the numeric ID of the file to look up.

#### Example
```jinja2
{% set file = file_by_id(123) %} 
{{ file.friendlyUrl }}
```

#### Output
```jinja2
https://www.hubspot.com/hubfs/HubSpot_Logos/HSLogo_color.svg
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| file_id | Id | The ID of the file to look up. | 


## geo_distance
This function contains 4 parameters and calculates the ellipsoidal 2D distance between two points on Earth.

#### Example
```jinja2
{% for row in hubdb_table_rows(1234567, "geo_distance(loc,1.233,-5.678,mi)__gt=500") %}
    {{row.name}} <br> 
{% endfor %}
```

#### Output
```jinja2
Cambridge, MA<br>
Salem, MA<br>
San Diego, CA<br>
Chicago, IL<br>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| point1 | Location | location from a HubDB column. | 
| point2_lat | Latitude | Latitude of point2. | 
| point2_long | Longitude | Longitude of point2. | 
| units | String | Units for the return value. Options are FT for feet, MI for miles, M for meters or KM for kilometers. | 


## get_asset_url
This function returns the public URL of a specified template or code file. The parameter of this function is the path in Design Manager. Coded file URLs update each time you publish them; therefore, by using this function your ensure you are always using the latest version of the file.

You can automatically generate this function in the app, by either right-clicking on a file name and choosing "Copy public URL" or by choosing **Actions &gt; Copy public URL**. The example below gets the URL of a Javascript file authored in Design Manager that can be included as the `src` of a ``.

#### Example
```jinja2
{{ get_asset_url("/custom/styles/style.css") }} 
```

#### Output
```jinja2
//cdn2.hubspot.net/hub/1234567/hub_generated/template_assets/1565970767575/custom/styles/style.min.css
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| path | String | The Design Manager file path to the template or file. | 


## get_public_template_url_by_id
This function works just like `get_public_template_url`, returning public URL of a specified template or code file. The only difference is the parameter of this function is the template ID (available in the URL of the template or coded file), instead of the Design Manager path.

#### Example
```jinja2
{{ get_public_template_url_by_id('2778457004')  }} 
```

#### Output
```jinja2
//cdn2.hubspot.net/hub/327485/hub_generated/style_manager/1431479563436/custom/page/Designers_2015/designer-doc-2105.min.js
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| template_id | Id | The ID number of the template of file. | 


## hubdb_table
For a comprehensive overview of HubDB, read our [HubDB page ](/docs/features/hubdb)in the CMS Developer tools section.

The `hubdb_table` function can be used to get information on a table including its name, columns, last updated, etc.

The following pieces of information can be pulled by calling the appropriate attributes:

- `id` - the ID of the table
- `name` - the name of the table
- `columns` - a list of column information
- `created_at` - timestamp of when this table was first created
- `published_at` - timestamp of when this table was published
- `updated_at` - timestamp of when this table was last updated
- `row_count` - the number of rows in the table

#### Example
```jinja2
{% set table_info = hubdb_table(1548215) %} 
{{ table_info.row_count }}
```

#### Output
```jinja2
25
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| table_id | String | Id or name of the table. | 


## hubdb_table_column
For a comprehensive overview of HubDB, read our [HubDB page ](/docs/features/hubdb)in the CMS Developer tools section.

The `hubdb_table_column` function can be used to get information on a column in table such as its label, type and options. This function accepts two parameters.

These pieces of information about the column can be pulled by calling the appropriate attributes:

- `id` - the ID of the column
- `name` - the name of the column
- `label` - the label to be used for the colum
- `type` - the type of the column
- `options` - for columns of type 'select', a map of optionId to option information
- `foreignIds` - for columns of type `'foreignId'`, a list of `foreignIds` (with `id` and `name` properties)

In addition to the above attributes, there is also a method which can be called: **`getOptionByName("")`** whereby for columns of type `'select'`, this will get option info by the option's name.

#### Example
```jinja2
{% set column_info = hubdb_table_column(123456, 6)  %} 
{{ column_info.label }}
```

#### Output
```jinja2
role
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| table_id | String | Id or name of the table. | 
| column | String | Id or name of the column. | 


## hubdb_table_row
For a comprehensive overview of HubDB, read our [HubDB page ](/docs/features/hubdb)in the CMS Developer tools section.   
  
The `hubdb_table_row` function can be used to pull a single row from a HubDB table. From this row, you can pull information from each table cell by calling on the corresponding attribute:   
  
(Built-in and custom column names are case insensitive. HS\_ID will work the same as hs\_id)

- `hs_id` - the globally unique id for this row
- `hs_created_at` - a timestamp representing when this row was created
- `hs_path` - when used with dynamic pages, this string is the last segment of the url's path for the page
- `hs_name` - when used with dynamic pages, this is the title of the page
- `` or `[""]` - Get the value of the column for this row by the `name` of the column

#### Example
```jinja2
{% set row = hubdb_table_row(1548264, 6726439331)  %} 
{{ row.role  }}
```

#### Output
```jinja2
CTO
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| table_id | String | Id or name of the table. | 
| row_id | Integer | Id of the row of the table. | 


## hubdb_table_rows
For a comprehensive overview of HubDB, read our [HubDB page ](/docs/features/hubdb)in the CMS Developer tools section.

The `hubdb_table_rows` function can be used to list rows of a HubDB table, to be iterated through.

#### Example
```jinja2
{% for row in hubdb_table_rows(1546258, "years_at_company__gt=3&orderBy=count") %}
  the value for row {{ row.hs_id }} is {{ row.name }}
{% endfor %}
```

#### Output
```jinja2
the value for row 6726439331 is Brian Halligan

the value for row 8438997836 is Dharmesh Shah
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| table_id | String | Id or name of the table to query. | 
| query | String | A query such in the same format as a URL query string. If not passed, returns all rows. Additionally, there are several optional filters that can be used. | 


## include_default_custom_css
This function generates a link tag that references the [Primary CSS file](https://knowledge.hubspot.com/cos-general/create-edit-and-attach-css-files-to-style-your-site) (`default_custom_style.min.css`). This file is designed to be a global CSS file that can be added to all templates. To render, the function requires a boolean parameter value of `True`.

#### Example
```jinja2
{{ include_default_custom_css(True) }} 
```

#### Output
```jinja2
<link href="//cdn2.hubspot.net/hub/327485/hub_generated/style_manager/1420345777097/custom/styles/default/hs_default_custom_style.min.css" rel="stylesheet">
```


## index
Returns the location of the first matching item in a 0 based `array`.

This function accepts 3 parameters, The first parameter is required. The first parameter is the item you are trying to find in the `array`. The second (`start`) and third (`end`) enable you to find that item in a slice of the `array`.

#### Example
```jinja2
{% set shapes = ["triangle","square","trapezoid","triangle"] %}
triangle index: {{shapes.index("triangle")}} <br>
trapezoid index: {{shapes.index("trapezoid")}}
<hr>
adjusted start and end <br>
triangle index: {{shapes.index("triangle",1,5)}}
```

#### Output
```jinja2
triangle index: 0<br>
trapezoid index: 2
<hr>
adjusted start and end<br>
triangle index: 3
```


## insert
Places an element into a list at the specific index provided.

This function accepts 2 parameters:

- `Index`: the position where an element is to be inserted
- `Element`: the item to be inserted

#### Example
```jinja2
{% set even_numbers = [2,4,8,10]  %}
{% do even_numbers.insert(2,6) %}
{{even_numbers}}
```

#### Output
```jinja2
[2, 4, 6, 8, 10]
```


## locale_name
Returns a human-readable string representation of a language code, optionally translated to a target language.

#### Example
```jinja2
{{ locale_name('es') }}
{{ locale_name('es', 'en') }}
```

#### Output
```jinja2
Español
Spanish
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| language_code | String | The language code. | 
| target_language_code | String | The language that the output will be translated to. | 


## menu
Returns the nested link structure of an advanced menu. Menu nodes have a variety of [properties](/docs/hubl/variables#menu-node-variables) that can be used on objects that are returned.

#### Example
```jinja2
{% set node = menu(987) %}
{% for child in node.children %}
	{{ child.label }}<br>
{% endfor %}
```

#### Output
```jinja2
page1<br>
page2<br>
page3<br>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| menu_id | Id | Required. The id of the menu passed as a number. | 
| root_type | Enumeration | Root type of the menu ("site_root", "top_parent", "parent", "page_name", "page_id", "breadcrumb").

"site_root" denotes static - Always show top-level pages in menu.
"top_parent" denotes dynamic by section - Show pages in menu that are related to section being viewed.
"parent" denotes dynamic by page - Show pages in menu that are related to page being viewed.
"breadcrumb" denotes breadcrumb style path menu (uses horizontal flow).
 | 
| root_key | String | Root key (id or name) when using "page_name" or "page_id". | 


## module_asset_url
Gets the URL for an asset attached to a custom module via **Linked Files &gt; Other Files**.

#### Example
```jinja2
{{ module_asset_url("smile.jpg") }} 
```

#### Output
```jinja2
https://cdn2.hubspot.net/hubfs/6178146/logo-black-color.png
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| name | String | The name of the asset. | 


## oembed
Returns OEmbed data dictionary for given request.

#### Example
```jinja2
{{ oembed({ url: "https://www.youtube.com/watch?v=KqpFNtbEOh8"}) }}
```

#### Output
```jinja2
OEmbedResponse{type=video, version=1.0, html=<iframe width="480" height="270" src="https://www.youtube.com/embed/KqpFNtbEOh8?feature=oembed" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>, title=Marketing Is a Marathon — Build a Complete Customer Experience, authorName=HubSpot, authorUrl=https://www.youtube.com/user/HubSpot, providerName=YouTube, providerUrl=https://www.youtube.com/, thumbnailUrl=https://i.ytimg.com/vi/KqpFNtbEOh8/hqdefault.jpg, thumbnailWidth=480, thumbnailHeight=360}
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| request | String | Request object, {url: string, max_width: long, max_height: long}. | 


## personalization_token
Returns the value of a contact or contact related property, or a default.

#### Example
```jinja2
Hi {{ personalization_token("contact.firstname", "there") }}!
```

#### Output
```jinja2
<!-- If the contact is known -->
Hi Dharmesh!

<!-- If the contact is unknown -->
Hi there!
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| expression | String | An expression for the object and property to render. | 
| default | String | (Optional) A default value to use if the expression has no value. | 


## pop
Removes the item at the index from the list. Also returns the removed item if printed.

#### Example
```jinja2
{% set even_numbers = [2,3,4,6,8,9,10]  %}
{% do even_numbers.pop(1) %}
{{even_numbers.pop(4)}}
{{even_numbers}}
```

#### Output
```jinja2
9
[2, 4, 6, 8, 10]
```


## postal_location
The `postal_location` function returns the latitude/longitude location pair for a given postal code and country code (limited to US, CA, and GB).

#### Example
```jinja2
{{ postal_location("02139") }}
{% set location = postal_location("02139", "US") %}
{{ location.latitude }}
{{ location.longitude }}
```

#### Output
```jinja2
LatLon{latitude=42.3647, longitude=-71.1042}
42.3647
-71.1042
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| postal_code | String | Postal code of the location. | 
| country_code | String | Country code for the postal code. If not provided, the country will try to be inferred from the postal code. | 


## range
Returns a list containing an arithmetic progression of integers. With one parameter, range will return a list from 0 up to (but not including) the `value`. With two parameters, the range will start at the first value and increment by 1 up to (but not including) the second `value`. The third parameter specifies the step increment. All values can be negative. Impossible ranges will return an empty list. Ranges can generate a maximum of 1000 values.

Range can be used within a [for loop](/docs/hubl/for-loops) to specify the number of iterations that should run.

#### Example
```jinja2
{{ range(11) }}
{{ range(5, 11) }}
{{ range(0, 11, 2) }}
       
       
{% for number in range(11) %}
{{ number }}
{% endfor %}
```

#### Output
```jinja2
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
[5, 6, 7, 8, 9, 10]
[0, 2, 4, 6, 8, 10]
       
       

0

1

2

3

4

5

6

7

8

9

10
```


## require_css
This function enqueues a CSS file to be rendered in the head element. All CSS link tags are grouped together and render before any JavaScript tags. The HubL is replaced with an empty line and then a link tag is added to `{{ standard_header_includes }}`. This method requires an absolute URL; CMS content with a known relative URL can be required by using the `get_asset_url()` function.

To enqueue an inline style to be rendered in the `head` via a style tag element, use the `{% require_css %} and {% end_require_css %}` tag instead with your style tags and CSS inside of that.

#### Example
```jinja2
{{ standard_header_includes }}
<!-- more html -->
{{ require_css("http://example.com/path/to/file.css") }}
{{ require_css(get_asset_url("/relative/path/to/file.css")) }}
```

#### Output
```jinja2
<!-- other standard header html -->
<link type="text/css" rel="stylesheet" href="http://example.com/path/to/file.css">
<link type="text/css" rel="stylesheet" href="http://example.com/relative/path/to/file.css">
<!-- more html -->
```


## require_js
This function enqueues a script to be rendered in either the head tag or footer. The HubL is replaced by an empty line and included in either `{{ standard_footer_includes }}` (the default) or `{{ standard_header_includes }}` if the call contains the `'head'` parameter.

To enqueue an inline script to be rendered in the head tag via a script element, use the `{% require_js %} and {% end_require_js %}` tag instead with you script tags and JS code inside.

#### Example
```jinja2
{{ standard_header_includes }}
<!-- more html -->
{{ require_js("http://example.com/path/to/footer-file.js", "footer") }}
{{ require_js("http://example.com/path/to/head-file.js", "head") }}

{{ standard_footer_includes }}
```

#### Output
```jinja2
<!-- other standard header html -->
<script src="http://example.com/path/to/head-file.js"></script>

<!-- more html -->

<script src="http://example.com/path/to/footer-file.js"></script>
<!-- other standard footer html -->
```


## resize_image_url
Rewrites the URL of image stored in File Manager to a URL that will resize the image on request. The function accepts one required parameter, and five optional parameters. At least one optional parameter must be passed.

Required

- `URL`: string, URL of a HubSpot-hosted image

Optional

- width: number, the new image width in pixels
- height: number, the new image height in pixels
- length: number, the new length of the largest side, in pixels
- upscale: boolean, use the resized image dimensions even if they would scale up the original image (images may appear blurry)
- upsize: boolean, return the resized image even if it is larger than the original in bytes

#### Example
```jinja2
{{ resize_image_url("http://your.hubspot.site/hubfs/img.jpg", 0, 0, 300) }}
```

#### Output
```jinja2
http://your.hubspot.site/hubfs/img.jpg?length=300&name=img.jpg
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| url | String | URL of a HubSpot-hosted image. | 
| width | Integer (px) | The new image width, in pixels. | 
| height | Integer (px) | The new image height, in pixels. | 
| length | Integer (px) | The new length of the largest side, in pixels. | 
| upscale | Boolean | Use the resized image dimensions even if they would scale up the original image (images may appear blurry). | 
| upsize | Boolean | Return the resized image even if it is larger than the original in bytes. | 


## reverse
Reverses the order of items in a list. Does not take any parameters. To reverse an object or return an iterator to iterate over the list in reverse, use [`|reverse`](/docs/hubl/filters#reverse)

#### Example
```jinja2
{% set numbers = [1,2,3,4] %}
{% do numbers.reverse() %}
{{numbers}}
```

#### Output
```jinja2
[4, 3, 2, 1]
```


## set_response_code
Set the respond code as the specified code. 404 is the only supported code for now. When using this, your page will return a 404 error.

#### Example
```jinja2
{{ set_response_code(404) }} 
```

#### Output
```jinja2
<!-- this will cause the page to result in a 404 error -->
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| code | Integer | The HTTP response code. Currently, 404 is the only supported code. | 


## super
Super prints content from the parent template into a child template, when you have created parent and children templates, using the extends tag. For example in the code below, a basic HTML template has been created with a HubL block named "sidebar" and saved as parent.html. A second template file is created that will extend that parent file. Normally the &lt;h3&gt; would be printed in the parent HTML's sidebar block. But by using super, content from the parent template sidebar block is combined with the content from the child template.

#### Example
```jinja2
{% extends "custom/page/web_page_basic/parent.html" %}

{% block sidebar %}
    <h3>Table Of Contents</h3>
    {{ super() }}
{% endblock %}
```

#### Output
```jinja2
<!doctype html>
<html>
    <head>
        <meta charset="utf-8">
        <title>This is the parent template </title>
    </head>
    <body>
             <h3>Table of contents</h3>
            Sidebar content from parent.
    </body>
</html>
```


## today
Returns the start of today (12:00am). Optionally you can add a parameter to change the timezone from the default UTC.

#### Example
```jinja2
{{ today() }}
{{ today("America/New_York") }}
{{ unixtimestamp(today("America/New_York").plusDays(1)) }}
```

#### Output
```jinja2
2018-10-23T00:00Z
2018-10-23T00:00-04:00[America/New_York]
1540353600000
```


## to_local_time
Converts a UNIX timestamp to the local time, based on your HubSpot Report Settings. You can then apply a datetimeformat filter to format the date.

#### Example
```jinja2
{{ to_local_time(eastern_dt) }} 
```

#### Output
```jinja2
2015-05-13 10:37:31
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| date | Datetime | UNIX timestamp to convert to local time. | 


## topic_cluster_by_content_id
Returns a HubL dict representing the topic cluster associated with a piece of content (determined by the passed content id), including metadata about the associated pillar page, core topic, and subtopics. Can be used to "auto-link" a piece of content with its associated pillar page \[if it exists\].

Available metadata can be found in: attachableContent (the current content's metadata), topic (the current content's associated topic metadata), coreTopic (the associated cluster's core topic metadata), and pillarPage (the associated pillar page's metadata).

Use `{{ topicCluster|pprint }}` to see a full a display of available properties/attributes.

#### Example
```jinja2
{{ topic_cluster_by_content_id(content.id) }}
{%- if content.id -%}
  {%- set topicCluster = topic_cluster_by_content_id(content.id) -%}
  {%- if topicCluster.pillarPage.url.value and topicCluster.pillarPage.publishState == 'PUBLISHED' -%}
    <div>Topic: <a href="{{ topicCluster.pillarPage.url.value }}">{{ topicCluster.coreTopic.phrase }}</a></div> 
  {%- endif -%}
{%- endif -%}
```

#### Output
```jinja2
{ attachedContent, topic, coreTopic, pillarPage }
(AttachedContentWithContext:  {attachedContent=AttachedContent{id=1234,    topicId=1234,    clusterId=1234,    portalId=0,    attachable=Attachable{contentId=124,    url=ValidatedUri{https://www.hubspot.com/},  attachableType=LANDING_PAGE,  title=title,  publishState=PUBLISHED,  deletedAt=null},  isLinkedToPillarPage=null,  isPillarPage=null,  createdAt=1547238986475,  updatedAt=1547238986475,  deletedAt=null},  coreTopic=Optional[Topic{id=1234,    portalId=0,    clusterId=1234,    phrase=TOPIC PHRASE,    attachedContent=null,    isCoreTopic=false,    createdAt=1547157062081,    updatedAt=1547232313421,    deletedAt=null}],  pillarPage=Optional[AttachedContent{id=1234,    topicId=1234,    clusterId=1234,    portalId=0,    attachable=Attachable{contentId=null,    url=ValidatedUri{https://www.hubspot.com.com/},  attachableType=EXTERNAL_URL,  title=null,  publishState=PUBLISHED,  deletedAt=null},  isLinkedToPillarPage=null,  isPillarPage=null,  createdAt=1547157062086,  updatedAt=1547157062086,  deletedAt=null}],  topic=Optional[Topic{id=1234,    portalId=0,    clusterId=8345,    phrase=topic phrase,    attachedContent=null,    isCoreTopic=false,    createdAt=1547238962703,    updatedAt=1547238962703,    deletedAt=null}]})



<div>
  Topic: <a href="#-link-to-pillar-page-url">
    core topic phrase
  </a>
</div>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| content_id | Id | The id of the page to look up. | 


## truncate
The truncate function works just like the [truncate filter](/docs/hubl/filters#truncate), but uses function syntax instead of filter syntax. The first parameter specifies the string. The second parameter specifies the length at which to truncate. The final parameter specifies the characters to add when the truncation occurs.

#### Example
```jinja2
{{ truncate('string to truncate at a certain length', 19, end='...') }} 
```

#### Output
```jinja2
string to truncate ...
```


## type
This function accepts one argument and returns the type of an object. The return value is one of "bool", "datetime", "dict", "float", "int", "list", "long", "null", "str" or "tuple".

#### Example
```jinja2
{{ type("Blog") }}
{% set my_type = type("Blog") %}
<p>{{my_type}}</p>
```

#### Output
```jinja2
<p>str</p>
```


## unixtimestamp
This function returns a unix timestamp. By default it will return the timestamp of now or you can optionally supply a datetime object to be converted to a unix timestamp.

#### Example
```jinja2
{{ unixtimestamp() }}
{{ unixtimestamp(d) }}

```

#### Output
```jinja2
1582822133978
1565983117868
```


## update
Updates the dict with the elements from another dict object or from an iterable of key/value pairs.

#### Example
```jinja2
{% set dict_var = {'authorName': 'Douglas Judy', 'authorTitle': 'Mastermind' } %}
{% set test = dict_var.update({'authorFriend': 'Jake'}) %}
{% set test = dict_var.update({'authorLocation': 'unknown'}) %}
{{ dict_var }}
```

#### Output
```jinja2
{authorName=Douglas Judy, authorTitle=Mastermind, authorFriend=Jake, authorLocation=unknown}
```


# Variables
## 
HubSpot templates can use a host of predefined variables that can be used to render useful website and email elements. This page is a reference listing of those variables. You can learn more about creating your own variables in a HubL template or module, [here](/docs/hubl/variables-macros-syntax).

While most of the variables listed on this page are optional, there are a few variables that are required, in order to create emails and pages from your templates.

## Required email template variables
To be [CAN-SPAM ](https://knowledge.hubspot.com/email/can-i-customize-my-can-spam-email-footer)compliant, all emails sent through HubSpot require certain company and opt-out information; therefore, HubSpot email templates require certain variables. There are additional email variables that are optional which are listed [further down this page](#email-variables).
| Variable | Type | Description | 
|  ------  |  ------  |  ------  | 
| site_settings.company_city | String | Prints the company city (set in Settings > Marketing > Email > Configuration > Footer). | 
| site_settings.company_name | String | Prints the company name (set in Settings > Marketing > Email > Configuration > Footer). | 
| site_settings.company_state | String | Prints the company state (set in Settings > Marketing > Email > Configuration > Footer). | 
| site_settings.company_street_address_1 | String | Prints the company address (set in Settings > Marketing > Email > Configuration > Footer). | 
| unsubscribe_link | String | Prints the URL of the page that allows recipients to manage subscription preferences or unsubscribe from email communications. This variable should be used in the href attribute of an <a>. | 


## Required page template variables
To publish a coded file as an editable page or blog template, the following variables must be included. If you want to publish an HTML file without these variables, to use within another template, you can do so by unchecking the option "Make this template available for new content".
| Variable | Type | Description | 
|  ------  |  ------  |  ------  | 
| standard_footer_includes | String | Renders the HubSpot tracking code and any other code included in your Footer HTML in Content Settings or the options of a particular page. This tag should be inserted directly before the closing body tag. | 
| standard_header_includes | String | Adds jQuery, public_common.css, layout.css, any attached stylesheets, a meta viewport tag, Google Analytics tracking code, other page meta information, and code added to the head tag at the domain/template/page level. This variable should be added to the <head> of HTML templates. | 


## Variables available in all templates
Many predefined HubSpot variables can be used in email, page, or blog templates. Below is a list of these variables.

*(Note: If you want to see additional information what these variables can output, [try using the pprint parameter](/docs/hubl/filters#pprint))*
The following variables will render on any type of content.
| Variable | Type | Description | 
|  ------  |  ------  |  ------  | 
| account | Dict	 | This variable is a dictionary that stores company personalization properties for a known contact. Properties can be accessed from this dict, by adding a period and the property name. For example, account.name would print the company name of a contact.Use of this variable will disable page caching.  | 
| company_domain | String | Prints the company domain from Website > Pages > Branding > Logo Link. | 
| contact | Dict | This variable is a dictionary that stores contact personalization properties for a known contact. Properties can be accessed from this dict, by adding a period and the property name. For example, contact.firstname would print the first name of a contact.Use of this variable will disable page caching.  | 
| content | Dict	 | This variable is a dictionary that stores various properties pertaining to a specific piece of content such as an email, a page, or a post. | 
| content.absolute_url | String | Prints the full URL of a page, post, or web page version of an email. | 
| content.archived | Boolean | This variable evaluates to True, if the page or email was marked as archived by the user. | 
| content.author_email | String | The email address of the content creator. | 
| content.author_name | String | The first and last name of the content creator. | 
| content.author_username | String | The HubSpot username of the content creator. | 
| content.campaign | String | The GUID for the marketing campaign that this page or email is associated with. This unique ID can be found in the URL of a particular campaign in the Campaign's tool. | 
| content.campaign_name | String | The name of the marketing campaign that this page, this post, or this email is associated with. | 
| content.created | Datetime | A datetime object for when the content was originally created, in UTC time. This variable can be formatted with the datetime filter. | 
| content.meta_description | String | When pulling the meta description of a page, it is better to use the variable page_meta.meta_description. | 
| content.name | String | The name of a post, email, or page. For pages and emails this will print the internal content name, while for posts this will print the post title. For blog posts, this is the post title that displays. For other types of content, this is generally an internal name. This variable includes a wrapper so that it is editable via the UI, when included in blog posts. If you want to print the content name without a wrapper, use page_meta.name. | 
| content.publish_date | Datetime | A datetime object representing when the content was published, in UTC time. This variable can be formatted with the datetime filter. | 
| content.publish_date_localized | String | A string representing the datetime when the content was published, in the local time as defined in the HubSpot Report settings. This variable is also subject to the language and  date format settings in Settings > Website > Blog > Date Formats. | 
| content.template_path | String | The Design Manager file path to your template (ie custom/page/web_page_basic/my_template.html). | 
| content.updated | Datetime | A datetime object for when the user last updated the content, in UTC time. This variable can be formatted with the datetime filter. | 
| content_id | String | Prints the unique ID for a page, post, or email. This ID can be found in the URL of the editor. You can use this variable as an alias for content.id. | 
| favicon_link | String | Prints the source URL of the favicon. This image is set in Settings > Website > Pages > Branding. | 
| hub_id | String | The portal ID of your HubSpot account. | 
| hubspot_analytics_tracking_code | String | Includes the analytics tracking code. This tag is not necessary, because standard_footer_includes, already renders the tracking code. | 
| local_dt | Datetime | A datetime object of the current time in the time zone defined in your Report Settings. | 
| local_time_zone | String | The time zone, as configured in your HubSpot Report Settings. | 
| page_meta.canonical_url | String | The official URL that this page should be accessed at. Usually does not include any query string parameters. Use this for the rel='canonical' tag. HubSpot automatically canonicalizes URLs. | 
| page_meta.html_title | String | The title of the page. This variable should be used in the <title> tag of HTML templates.   | 
| page_meta.meta_description | String | The meta description of a page. This variable should be used in the "description" <meta> tag of HTML templates. | 
| page_meta.name | String | An alias for content.name. | 
| portal_id | String | An alias for hub_id | 
| request_contact | Dict | A dictionary containing data about the requested contact.Use of this variable will disable page caching.  | 
| site_settings | Dict | The site_settings dict contains various settings from such as colors and fonts (see below). | 
| year | String | Prints the current year. | 


## Color and font settings
There are several basic color and font controls in **Settings &gt; Marketing &gt; Configuration &gt; Color** that can be printed to templates and files. Please note that if you use these variables in CSS files, you will need to republish/recompile your CSS file when you change one of the settings, for the new color to apply.
| Variable | Type | Description | 
|  ------  |  ------  |  ------  | 
| site_settings.background_color | Dict	 | Background color setting from Settings > Marketing > Email > Configuration > Color. Prints a HEX value. | 
| site_settings.body_border_color | String | Body border color setting from Settings > Marketing > Email > Configuration > Color. This option becomes available when you select "Manually set email border color" under the "Border Color Options" dropdown. Prints a HEX value. | 
| site_settings.body_border_color_choice | Enumeration | The variable is used in HubSpot's default email templates to determine whether or not a border should be added. The setting is controlled in Content Settings > Colors and Fonts. It prints values: BORDER_AUTOMATIC, BORDER_MANUAL, BORDER_NONE | 
| site_settings.body_color | String | Body color setting from Settings > Marketing > Email > Configuration > Color. Prints a HEX value. | 
| site_settings.color_picker_favorite_1 | String | Favorite color 1 setting from Settings > Marketing > Email > Configuration > Color. Prints a HEX value. Replace 1 with 2-6 to modify the tag for other favorite color settings. | 
| site_settings.primary_accent_color | String | Primary accent color setting from Settings > Marketing > Email > Configuration > Color. Prints a HEX value. | 
| site_settings.primary_font | Enumeration | Primary font setting from Settings > Marketing > Email > Configuration > Font. Prints value from dropdown. | 
| site_settings.primary_font_color | String | Primary font color setting from Settings > Marketing > Email > Configuration > Font. Prints a HEX value. | 
| site_settings.primary_font_size | String | Primary font size setting from Settings > Marketing > Email > Configuration > Font. Includes "px". | 
| site_settings.secondary_accent_color | String | Secondary font color setting from Settings > Marketing > Email > Configuration > Color Prints a HEX value. | 
| site_settings.secondary_font | Enumeration | Secondary font setting from Settings > Marketing > Email > Configuration > Font. Prints value from dropdown. | 
| site_settings.secondary_font_color | String | Secondary font color setting from Settings > Marketing > Email > Configuration > Font Prints a HEX value. | 
| site_settings.secondary_font_size | String | Primary font size setting from Settings > Marketing > Email > Configuration > Font. Includes "px". | 


## Email variables
The following variables are specifically for HTML email templates or HubL template modules in email layouts.
| Variable | Type | Description | 
|  ------  |  ------  |  ------  | 
| background_color | String | Email-template only alias for the color and font setting described above. | 
| body_border_color | String | Email-template only alias for the color and font setting described above. | 
| body_border_color_choice | String | Email-template only alias for the color and font setting described above. | 
| body_color | String | Email-template only alias for the color and font setting described above. | 
| content.create_page | Boolean | This variable is True, if there is a web page version of the email. | 
| content.email_body | Richtext | The main body of the email. This variable renders a rich text module. | 
| content.emailbody_plaintext | String | The optional override of the plain text email body | 
| content.from_name | String | The from name of the email sender | 
| content.reply_to | String | The reply to address for the email | 
| content.subject | String | The subject of the email | 
| email_body_border_css | String | Email-template only alias for the color and font setting described above. | 
| email_body_padding | string | The email body padding setting. This setting is located in Settings > Marketing > Email > Configuration > Size. | 
| email_body_width | String | The email body width setting. This setting is located in Settings > Marketing > Email > Configuration > Size. | 
| primary_accent_color | String | Email-template only alias for the color and font setting described above. | 
| primary_font | Enumeration | Email-template only alias for the color and font setting described above. | 
| primary_font_color | String | Email-template only alias for the color and font setting described above. | 
| primary_font_size | String | Email-template only alias for the color and font setting described above. | 
| primary_font_size_num | String | Prints the font size number from Settings > Marketing > Email > Configuration > Font. Excludes "px". | 
| secondary_accent_color | String | Email-template only alias for the color and font setting described above. | 
| secondary_font | Enumeration | Email-template only alias for the color and font setting described above. | 
| secondary_font_color | String | Email-template only alias for the color and font setting described above. | 
| secondary_font_size_num | String | Prints the font size number from Settings > Marketing > Email > Configuration > Font. Excludes "px". | 
| site_settings.company_street_address_2 | String | Prints the address line 2 from Settings > Marketing > Email > Configuration > Footer. | 
| site_settings.office_location_name | String | Prints the office location name from Settings > Marketing > Email > Configuration > Footer. | 
| subscription_confirmation_url | String | Prints the URL of the subscription preferences confirmation page. This URL is dynamically generated on send. | 
| subscription_name | String | Prints the name of the Email Type specified for that email. | 
| unsubscribe_anchor | String | Generates an anchor tag with the work "unsubscribe" linked to your unsubscribe page. | 
| unsubscribe_link_all | String | Renders a link to unsubscribe from all email communications, as opposed to a link to manage subscription preferences. | 
| unsubscribe_section | String | Renders an unsubscribe section that includes an unsubscribe link, as well as help text. | 
| view_as_page_section | String | Generates a link with help text that leads to a webpage version of an email. | 
| view_as_page_url | String | Generates a link that leads to a webpage version of an email. | 


## Website pages variables
The following variables are available for site pages, landing pages, system pages, and blogs.
| Variable | Type | Description | 
|  ------  |  ------  |  ------  | 
| builtin_body_classes | String | This variable dynamicaly prints helpful classes that help differentiate the markup of content created with that template (ie type of content, content name, etc). This makes styling different types of content or particular pages easier. This variable should be used in the class attribute of the body tag on coded templates. | 
| request_contact.is_logged_in | String | This variable defines whether or not the requesting contact is logged in to a website's gated content (see control audience access documentation for further information). The value of this variable will return true if the requesting contact is logged in, and false if the requesting contact has logged out. A contact can be logged out by directing them to the URL https://www.yourdomain.com/_hcms/mem/logout.Use of this variable will disable page caching.  | 
| request_contact.list_memberships | String | This variable returns a dict of ids that represents the lists of which the contact is a member.Use of this variable will disable page caching.  | 
| content.language | Dict | This variable returns a dict of information about the language settings of a page. {{ content.language.languageTag }} returns the language identifier of a page (i.e. "en" or "es"). {{ content.language.textDirection }} returns the text direction of the language of the page (i.e. "rtl" or "ltr"). | 


## HTTP request variables
The following variables print information about the HTTP page request.
| Variable | Type | Description | 
|  ------  |  ------  |  ------  | 
| request.cookies | Dict | A dictionary of cookie names mapped to cookie values.Use of this variable will disable page caching.  | 
| request.domain | String | The domain used to access this page | 
| request.full_url | String | The URL used to access this page, with the query string | 
| request.path | String | The path component of the URL | 
| request.path_and_query | String | The path and query component of the URL | 
| request.query | String | The query string component of the URL | 
| request.query_dict | Dict | The query string coverted into a name->value dictionary | 
| request.referrer | String | The HTTP referrer, the url of the page that linked to the current page.Use of this variable will disable page caching.  | 
| request.remote_ip | String | The IP address of the visitor.Use of this variable will disable page caching. | 
| request.scheme | String | The protocol of the request (either http or https) | 
| request.search_engine | String | The search engine used to find this page, if applicable. Ex: google, aol, live, yahoo, images.google, etc | 
| request.search_keyword | String | The keyword phrase used to find this page, if applicable | 
| request.headers | String | A dictionary of available request headers | 


## Blog variables
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


## HubDB variables
The following variables are used to build dynamic pages with HubDB. These variables are only available for dynamic templates.
| Variable | Type | Description | 
|  ------  |  ------  |  ------  | 
| dynamic_page_hubdb_table_id | Long | The ID of the table selected in the 'Advanced Settings` tab of the page editor. | 
| dynamic_page_hubdb_row | Dict | The HubDB row of the dynamic page that matches with the page request path. If the request is to the listing page, this value will be null. | 
| row.hs_id | Long | The internal ID of a HubDB row. | 
| row.hs_name | String | The name of the HubDB row. | 
| row.hs_path | String | The path of the HubDB row. Used to resolve a request to one row in the table specified by dynamic_page_hubdb_table_id. | 
| row.hs_child_table_id | Long | The child table ID of the HubDB row. Can be used to build nested templates. | 
| row.hs_parent_row | Dict | The parent row of the HubDB row. Can only be used when using child tables for nested templates. | 
| dynamic_page_route_level | Integer | Current depth of a page in a multi-level dynamic template. The value starts at 0 and increments with each additional table layer. | 


## Menu node variables
The following variables are available to use on the object returned by the [HubL menu function](/docs/hubl/functions#menu).
| Variable | Type | Description | 
|  ------  |  ------  |  ------  | 
| node.label | String | The menu label of the page. | 
| node.url | String | URL of the page. | 
| node.pageId | Number | ID of the page if within HubSpot. | 
| node.contentGroupId | Number | Blog ID of the page if it is a HubSpot blog post. | 
| node.parentNode | Object | The parent node of the current node. The parent node will have the current node in its children property. | 
| node.children | List | The list of child nodes for the current node. | 
| node.activeBranch | Boolean | True if the node is in the top-level branch that the current page is in. | 
| node.activeNode | Boolean | True if the node is the current page. | 
| node.level | Number | The number of levels deep the current node is from the top-level nodes. | 
| node.pageTitle | String | Name of the content page if within HubSpot. | 
| node.slug | String | Path slug of the page. | 
| node.linkTarget | String | Link target of the page. | 


# Tags
## 
This page is a comprehensive reference guide of the syntax and the available parameters for all HubL modules. For an explanation of the module tag syntax and a list of globally supported parameters, [check out this article](/docs/hubl/hubl-module-syntax-and-parameters). Each module type below contains a sample of the basic syntax, as well as an example with parameters and code output.

## Blog comments
A blog comments module renders the comments embed code on a blog template. This Javascript embed code loads the comments form and comments, based upon your configuration in Content Settings.

#### Example
```jinja2
Blog Comment Form module:
{% blog_comments "blog_comments" overrideable=False, label='Blog Comments' %}

Blog Comment Count module:
{% blog_comments "blog_comments" %}

Blog Comment listing for specific blog:
{% blog_comments "default_blog_comments" select_blog='359485112' %}
```

#### Output
```jinja2
Blog Commment Form Output:
<span id="hs_cos_wrapper_blog_comments" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_blog_comments"
    style="" data-hs-cos-general-type="widget" data-hs-cos-type="blog_comments">
    <div class="section post-footer">
        <div id="comments-listing" class="new-comments no-comments"></div>
        <div id="hs-comment-embed" style="display:none;"></div>
        <div id="comment-form" class="new-comments">
            <form novalidate="" accept-charset="UTF-8"
                action="https://api.hubapi.com/comments/v3/comment?portalId=311600" enctype="multipart/form-data"
                id="hsForm_d30edada-82e4-4a69-aaf4-a9d0376f37e6" method="POST" class="hs-form stacked"
                data-form-id="d30edada-82e4-4a69-aaf4-a9d0376f37e6" data-portal-id="311600"
                data-reactid=".hbspt-forms-0">
                <div data-reactid=".hbspt-forms-0.0:$0">
                    <div class="hs_email field hs-form-field" data-reactid=".hbspt-forms-0.0:$0.$email">
                        <label class="" placeholder="Enter your Email" for="email-d30edada-82e4-4a69-aaf4-a9d0376f37e6"
                            data-reactid=".hbspt-forms-0.0:$0.$email.0">
                            <span data-reactid=".hbspt-forms-0.0:$0.$email.0.0">Email</span><span
                                class="hs-form-required" data-reactid=".hbspt-forms-0.0:$0.$email.0.1">*</span>
                        </label>
                        <legend class="hs-field-desc" style="display:none;" data-reactid=".hbspt-forms-0.0:$0.$email.1">
                        </legend>
                        <div class="input" data-reactid=".hbspt-forms-0.0:$0.$email.$email">
                            <input id="email-d30edada-82e4-4a69-aaf4-a9d0376f37e6" class="hs-input" type="email"
                                name="email" required="" placeholder="" value=""
                                data-reactid=".hbspt-forms-0.0:$0.$email.$email.0">
                        </div>
                    </div>
                </div>
                <div data-reactid=".hbspt-forms-0.0:$1">
                    <div class="hs_website field hs-form-field" data-reactid=".hbspt-forms-0.0:$1.$website">
                        <label class="" placeholder="Enter your Website"
                            for="website-d30edada-82e4-4a69-aaf4-a9d0376f37e6"
                            data-reactid=".hbspt-forms-0.0:$1.$website.0">
                            <span data-reactid=".hbspt-forms-0.0:$1.$website.0.0">Website</span>
                        </label>
                        <legend class="hs-field-desc" style="display:none;"
                            data-reactid=".hbspt-forms-0.0:$1.$website.1"></legend>
                        <div class="input" data-reactid=".hbspt-forms-0.0:$1.$website.$website">
                            <input id="website-d30edada-82e4-4a69-aaf4-a9d0376f37e6" class="hs-input" type="text"
                                name="website" value="" placeholder=""
                                data-reactid=".hbspt-forms-0.0:$1.$website.$website.0">
                        </div>
                    </div>
                </div>
                <div data-reactid=".hbspt-forms-0.0:$2">
                    <div class="hs_comment field hs-form-field" data-reactid=".hbspt-forms-0.0:$2.$comment">
                        <label class="" placeholder="Enter your Comment"
                            for="comment-d30edada-82e4-4a69-aaf4-a9d0376f37e6"
                            data-reactid=".hbspt-forms-0.0:$2.$comment.0">
                            <span data-reactid=".hbspt-forms-0.0:$2.$comment.0.0">Comment</span>
                            <span class="hs-form-required" data-reactid=".hbspt-forms-0.0:$2.$comment.0.1">*</span>
                        </label>
                        <legend class="hs-field-desc" style="display:none;"
                            data-reactid=".hbspt-forms-0.0:$2.$comment.1"></legend>
                        <div class="input" data-reactid=".hbspt-forms-0.0:$2.$comment.$comment">
                            <textarea id="comment-d30edada-82e4-4a69-aaf4-a9d0376f37e6" class="hs-input" name="comment"
                                required="" placeholder=""
                                data-reactid=".hbspt-forms-0.0:$2.$comment.$comment.0"></textarea>
                        </div>
                    </div>
                </div>
                <div data-reactid=".hbspt-forms-0.0:$3">
                    <div class="hs_subscribe field hs-form-field" data-reactid=".hbspt-forms-0.0:$3.$subscribe">
                        <label class="" placeholder="Enter your Subscribe to follow-up comments for this post"
                            for="subscribe-d30edada-82e4-4a69-aaf4-a9d0376f37e6"
                            data-reactid=".hbspt-forms-0.0:$3.$subscribe.0">
                            <span data-reactid=".hbspt-forms-0.0:$3.$subscribe.0.0"></span>
                        </label>
                        <legend class="hs-field-desc" style="display:none;"
                            data-reactid=".hbspt-forms-0.0:$3.$subscribe.1"></legend>
                        <div class="input" data-reactid=".hbspt-forms-0.0:$3.$subscribe.$subscribe">
                            <ul class="inputs-list" data-reactid=".hbspt-forms-0.0:$3.$subscribe.$subscribe.0">
                                <li class="hs-form-booleancheckbox"
                                    data-reactid=".hbspt-forms-0.0:$3.$subscribe.$subscribe.0.0">
                                    <label for="subscribe-d30edada-82e4-4a69-aaf4-a9d0376f37e6"
                                        class="hs-form-booleancheckbox-display"
                                        data-reactid=".hbspt-forms-0.0:$3.$subscribe.$subscribe.0.0.0">
                                        <input id="subscribe-d30edada-82e4-4a69-aaf4-a9d0376f37e6" class="hs-input"
                                            type="checkbox" name="subscribe" value="true"
                                            data-reactid=".hbspt-forms-0.0:$3.$subscribe.$subscribe.0.0.0.0">
                                        <span data-reactid=".hbspt-forms-0.0:$3.$subscribe.$subscribe.0.0.0.1">Subscribe
                                            to follow-up comments for this post</span>
                                    </label>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
                <div data-reactid=".hbspt-forms-0.0:$4">
                    <div class="hs_lifecyclestage field hs-form-field" style="display:none;"
                        data-reactid=".hbspt-forms-0.0:$4.$lifecyclestage">
                        <label class="" placeholder="Enter your Lifecycle Stage"
                            for="lifecyclestage-d30edada-82e4-4a69-aaf4-a9d0376f37e6"
                            data-reactid=".hbspt-forms-0.0:$4.$lifecyclestage.0">
                            <span data-reactid=".hbspt-forms-0.0:$4.$lifecyclestage.0.0">Lifecycle Stage</span>
                        </label>
                        <legend class="hs-field-desc" style="display:none;"
                            data-reactid=".hbspt-forms-0.0:$4.$lifecyclestage.1"></legend>
                        <div class="input" data-reactid=".hbspt-forms-0.0:$4.$lifecyclestage.$lifecyclestage">
                            <input name="lifecyclestage" class="hs-input" type="hidden" value="subscriber"
                                data-reactid=".hbspt-forms-0.0:$4.$lifecyclestage.$lifecyclestage.0">
                        </div>
                    </div>
                </div>
                <div class="hs_submit" data-reactid=".hbspt-forms-0.2">
                    <div class="hs-field-desc" style="display:none;" data-reactid=".hbspt-forms-0.2.0"></div>
                    <div class="actions" data-reactid=".hbspt-forms-0.2.1">
                        <input type="submit" value="Submit Comment" class="hs-button primary"
                            data-reactid=".hbspt-forms-0.2.1.0">
                    </div>
                </div>
                <input name="hs_context" type="hidden"
                    value="{&quot;rumScriptExecuteTime&quot;:1396.815,&quot;rumServiceResponseTime&quot;:7737.500000000001,&quot;rumFormRenderTime&quot;:187.17999999999938,&quot;rumTotalRenderTime&quot;:7738.14,&quot;rumTotalRequestTime&quot;:183.2549999999992,&quot;pageUrl&quot;:&quot;http://311600.hs-sites.com/-temporary-slug-5eccb1d9-1f1b-4bbd-8e19-00e198331b15?hs_preview=ALicr-ma-4312320350&quot;,&quot;pageTitle&quot;:&quot;HubSpot Sales Professional User Guide: HubSpot Sales Professional Overview&quot;,&quot;source&quot;:&quot;FormsNext-static-1.390&quot;,&quot;isHostedOnHubspot&quot;:true,&quot;timestamp&quot;:1479135449193,&quot;userAgent&quot;:&quot;Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/54.0.2840.71 Safari/537.36&quot;,&quot;referrer&quot;:&quot;&quot;,&quot;hutk&quot;:&quot;a525e671c25f6b108d25e08c892e359e&quot;,&quot;originalEmbedContext&quot;:{&quot;portalId&quot;:&quot;311600&quot;,&quot;formId&quot;:&quot;d30edada-82e4-4a69-aaf4-a9d0376f37e6&quot;,&quot;target&quot;:&quot;#comment-form&quot;,&quot;redirectUrl&quot;:&quot;http://www.hubspot.com/contact-sales/thanks/&quot;,&quot;pageId&quot;:&quot;23423&quot;,&quot;pageName&quot;:&quot;My great landing page&quot;,&quot;css&quot;:&quot;.your-custom-css {background-color: #fe7722}&quot;,&quot;requiredCss&quot;:&quot;.my-custom-error-msgs {border-radius: 3px;}&quot;,&quot;submitButtonClass&quot;:&quot;hs-button primary&quot;},&quot;recentFieldsCookie&quot;:{},&quot;pageId&quot;:&quot;23423&quot;,&quot;pageName&quot;:&quot;My great landing page&quot;,&quot;boolCheckBoxFields&quot;:&quot;subscribe&quot;,&quot;dateFields&quot;:&quot;&quot;,&quot;redirectUrl&quot;:&quot;http://www.hubspot.com/contact-sales/thanks/&quot;,&quot;smartFields&quot;:{},&quot;urlParams&quot;:{&quot;hs_preview&quot;:&quot;ALicr-ma-4312320350&quot;},&quot;formValidity&quot;:{},&quot;correlationId&quot;:&quot;55d71532-ab6b-4415-98f5-f3a16d7741c9&quot;,&quot;disableCookieSubmission&quot;:false}"
                    data-reactid=".hbspt-forms-0.3">
                <input type="hidden" id="id_portalId" name="portalId" value="311600"><input type="hidden"
                    id="id_contentId" name="contentId" value="4312320350">
                <input type="hidden" id="id_collectionId" name="collectionId" value="2224463151">
                <input type="hidden" id="id_contentAuthorEmail" name="contentAuthorEmail"
                    value="cstone@hubspot.com"><input type="hidden" id="id_contentAuthorName" name="contentAuthorName"
                    value="Christopher Stone">
                <input type="hidden" id="id_comment_verification_text" name="comment_verification_text"
                    value="Your comment has been received.">
                <input type="hidden" id="id_contentTitle" name="contentTitle"
                    value="HubSpot Sales Professional User Guide: HubSpot Sales Professional Overview">
                <input type="hidden" id="id_contentPermalink" name="contentPermalink"
                    value="http://311600.hs-sites.com/-temporary-slug-5eccb1d9-1f1b-4bbd-8e19-00e198331b15">
                <input type="hidden" id="id_contentCreatedAt" name="contentCreatedAt" value="1479135208000">
                <input type="hidden" id="id_formGuid" name="formGuid" value="d30edada-82e4-4a69-aaf4-a9d0376f37e6">
            </form>
        </div>
    </div>
</span>

Blog Comment Listing Module Output:

(function ($) {
    var commentsEmbedContext = {
        portalId: 327485,
        collectionId: 359485112,
        contentId: 2684120609,
        target: '#comments-listing.new-comments',
        showComments: true,
        showForm: true,
        commentVerificationText: "Your comment has been received.",
        embedScriptEnv: "prod",
        apiEnv: "prod",
        contentTitle: "Post title",
        contentCreatedAt: "1427849160000",
        contentPermalink: "http:\/\/designers.hubspot.com\/blog\/post-name,
        contentAuthorEmail: "dhunt@hubspot.com",
        contentAuthorName: "David Hunt",
        captchaRequired: true,
        captchaKey: "6Lc3uMsSAAAAAMjk4NIvPQK9_-ZLk2wBokFCo5Qt",
        maxThreadDepth: 3,
        formId: "8d42bb92-241b-4894-b853-1d5f6553daa0"
    };

    function loadComments() {
        if (window.hubspot && typeof window.hubspot.loadCommentsEmbed === 'function') {
            hubspot.loadCommentsEmbed(commentsEmbedContext.embedScriptEnv, function () {
                if (typeof window.hsEmbedComments === 'function') {
                    window.hsEmbedComments(commentsEmbedContext);
                }
            });
        } else {
            setTimeout(loadComments, 50);
        }
    }
    loadComments();
})(window.hsjQuery || jQuery);
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| limit | Integer | Sets maximum number of comments. | 5000 | 
| select_blog | 'default' or blog ID | Specifies which blog is connected to the comments embed. This parameter accepts arguments of either 'default' or a blog ID (available in the URL of the Blog dashboard). If want to use your default blog, this parameter is unnecessary. | default | 
| skip_css | Boolean | Setting this option to True will stop the blog comments CSS from loading.  | false | 


## Blog content
While drag and drop layouts include a blog content module, these modules are not created with a single tag. They instead use conditional logic to define how a blog post and a blog listing should render. [You can learn more about coding blog templates here.](/docs/building-blocks/templates/blog-template-markup)

## Blog related posts
Adds a listing of blog posts based off of a set of parameters shared by posts across blogs. Posts are selected based off of their relevancy to the set parameters. For an example usage of the optional post\_formatter parameter, see [Creating a related blog post listing with the blog related posts HubL tag.](/tutorials/creating-a-related-post-listing)

Please note this tag does not generate a page/post level editable module, it is entirely configured with HubL.

#### Example
```jinja2
{% related_blog_posts %}
{% related_blog_posts limit=2, blog_ids="1,2", tags="Sales enablement,Marketing", blog_authors="John Smith,Frank Smith", path_prefixes="/business-blog", start_date="2018-04-10", end_date="2018-04-10", blog_post_override="2783035366" %}
```

#### Output
```jinja2
<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_related_blog_posts" data-hs-cos-general-type="widget" data-hs-cos-type="related_blog_posts" id="hs_cos_wrapper_" style=""><!--related-blog-entries--></span>
<div class="hs-related-blog-module feedreader_box">
  <span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_related_blog_posts" data-hs-cos-general-type="widget" data-hs-cos-type="related_blog_posts" id="hs_cos_wrapper_" style=""></span>
  <div class="hs-related-blog-item">
    <span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_related_blog_posts" data-hs-cos-general-type="widget" data-hs-cos-type="related_blog_posts" id="hs_cos_wrapper_" style=""></span>
    <div class="hs-related-blog-item-text">
      <span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_related_blog_posts" data-hs-cos-general-type="widget" data-hs-cos-type="related_blog_posts" id="hs_cos_wrapper_" style=""><a class="hs-related-blog-title" href="//www.underseaband.com/business-blog/marketing-is-fun"><span>Marketing is fun</span></a></span>
      <div class="hs-related-blog-byline">by <span class="hs-related-blog-author">John Smith</span> <span class="hs-related-blog-posted-at">posted on</span> <span class="hs-related-blog-date">June 3, 2018</span>
      </div>
      <div class="hs-related-blog-byline">
        <p class="hs-related-blog-description">Learn how to make marketing fun!<a href="//www.underseaband.com/business-blog/marketing-is-fun">Read more</a></p>
      </div>
      <div class="hs-related-blog-byline">
        <span class="hs-related-blog-tags">Tags: Marketing</span>
      </div>
    </div>
  </div>
  <div class="hs-related-blog-item hs-with-featured-image">
    <div class="hs-related-blog-item-text">
      <a class="hs-related-blog-title" href="//www.underseaband.com/business-blog/sales-is-fun"><span>Sales is fun</span></a>
      <div class="hs-related-blog-byline">by <span class="hs-related-blog-author">Frank Smith</span> <span class="hs-related-blog-posted-at">posted on</span> <span class="hs-related-blog-date">June 7, 2018</span>
      </div>
      <div class="hs-related-blog-byline">
        <p class="hs-related-blog-description">Learn how to make sales fun!<a href="//www.underseaband.com/business-blog/sales-is-fun">Read more</a></p>
      </div>
      <div class="hs-related-blog-byline">
        <span class="hs-related-blog-tags">Tags: Sales enablement</span>
      </div>
    </div>
    <div class="hs-related-blog-item-image-wrapper"><img alt="" class="hs-related-blog-featured-image" src="//www.underseaband.com/hubfs/business-blog/sales-is-fun.jpg"></div>
  </div>
</div>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| blog_ids | Integer | The ID(s) of blog(s) to include posts from. Omit this parameter to use the default blog. | 
           
           | 
| blog_post_ids | String | The ID(s) of a blog posts to use when finding relevant blog posts to list (comma separated). This parameter should only be used when the widget is appearing on pages, as on blog posts, it will default to the post the widget is appearing on. | 
           
           | 
| blog_post_override | String | The ID(s) of a blog posts which should always show up in the returned listing, despite all other parameter values and filters (comma separated). | 
           
           | 
| limit | Integer |  The max number of blog posts to list. | 3 | 
| tags | String | The tag(s) that should be used to determine if a post is relevant (comma separated). If a blog post has one of these tags or a similar tag, the post’s relevancy is increased, improving its ranking in the listing. | 
           
           | 
| start_date | datetime | Earliest published date. | 
           
           | 
| end_date | datetime | Latest published date. | 
           
           | 
| blog_authors | String |  The name(s) of authors to include posts from (comma separated). | 
           
           | 
| path_prefixes | String | URL paths or subdirectories to include posts from (comma separated). If a blog post has a similar prefix in its path, the post’s relevancy is increased, improving its ranking in the listing. | 
           
           | 
| post_formatter | String | The name of a custom macro to render returned blog posts. The macro is passed three parameters which are the blogs blog post object to format, the count in the iteration of blog posts, and the total count of blog posts in the results. If not specified or set to “default”, the built-in formatter will be used to format each post. | default | 


## Blog social sharing
Blog social sharing renders share counters on your blog posts (if enabled in Content Settings).

#### Example
```jinja2
{% blog_social_sharing "blog_social_sharing" %}
{% blog_social_sharing "blog_social_sharing" select_blog='359485112' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_blog_social_sharing" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_blog_social_sharing" style="" data-hs-cos-general-type="widget" data-hs-cos-type="blog_social_sharing">
     <div class="hs-blog-social-share">
          <ul class="hs-blog-social-share-list">
               <li class="hs-blog-social-share-item hs-blog-social-share-item-twitter">
                     <a href="https://twitter.com/share" class="twitter-share-button" data-lang="en" data-url="http://designers.hubspot.com/blog" data-size="medium" data-text="">Tweet</a>
               </li>
               <li class="hs-blog-social-share-item hs-blog-social-share-item-linkedin">
                    <script type="IN/Share" data-url="http://designers.hubspot.com/blog" data-showzero="true" data-counter="right"></script>
                </li>
                <li class="hs-blog-social-share-item hs-blog-social-share-item-facebook">
                     <div class="fb-like" data-href="http://designers.hubspot.com/blog" data-layout="button_count" data-action="like" data-show-faces="false" data-share="true" data-width="120"></div>
                </li>
                <li class="hs-blog-social-share-item hs-blog-social-share-item-google-plus">
                      <div class="g-plusone" data-size="medium" data-href="http://designers.hubspot.com/blog"></div>
                </li>
          </ul>
      </div>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| select_blog | 'default' or blog ID | Species which blog is connected to the share counters. This parameter accepts arguments of either 'default' or a blog ID (available in the URL of the Blog dashboard). If you want to use your default blog, this parameter is unnecessary. | default | 
| downgrade_shared_url | Boolean | Use HTTP in the url sent to the social media networks. Used to preserve counts when upgrading domains to HTTPS only. | false | 


## Blog subscription
A blog subscription module renders the blog subscriber form for a particular blog. This form is automatically created whenever a blog is created in Content Settings, and there is always one subscription form per blog. Please note that the subscribe form's fields are configured within the Forms editor UI.

#### Example
```jinja2
{% blog_subscribe "blog_subscribe" %}
{% blog_subscribe "subscribe_designers_blog" select_blog='default', title='Subscribe to the Designers Blog', response_message='Thanks for Subscribing!', label='Blog Email Subscription', overrideable=False %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_blog_subscription" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_blog_subscribe" style="" data-hs-cos-general-type="widget" data-hs-cos-type="blog_subscribe">
<h3 id="hs_cos_wrapper_blog_subscription_title" class="hs_cos_wrapper form-title" data-hs-cos-general-type="widget_field" data-hs-cos-type="text">Subscribe to Designers Blog</h3>
<div id="hs_form_target_blog_subscription"></div>
<script charset="utf-8" src="//js.hsforms.net/forms/current.js"></script>
<script>
hbspt.forms.create({ portalId: '327485', formId: 'a8d73dc6-0d3a-486d-8938-b19f28b69c3c', formInstanceId: '60', pageId: 2749976739, pageName: 'Apple, Google & Starbucks: Inside the Web Design Style Guides of 10 Famous Companies', redirectUrl: 'http://designers.hubspot.com/blog/web-design-style-guides-examples?hsFormKey=a56a754bc4c3465015935953363b8ff3#blog_subscription', css: '', target: '#hs_form_target_blog_subscription', formData: { cssClass: 'hs-form stacked' } });
</script>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| select_blog | 'default' or blog ID | Selects which blog subscription form to render. This parameter accepts arguments of either 'default' or a blog ID (available in the URL of the Blog dashboard). If want to use your default blog, this parameter is unnecessary. | default | 
| title | String | Defines text in an h3 tag title above the subscribe form. | "Subscribe Here!" | 
| no_title | Boolean | If True, the h3 tag above the title is removed. | false | 
| response_message | String | Defines the inline thank-you message that is rendered when a user submits a form. Supports HTML. | "Thanks for Subscribing!" | 
| edit_form_link | String | This parameter generates a link that allows users to click through to the corresponding Form editor screen. This option will only show in the editor UI if the modules has the parameter overrideable=True. Here is an example where HubID and form ID would be replaced with the information from the URL of your default blog subscriber form: edit_form_link=' <ul>\n <li><a href="/forms/HubID/FormID/edit/" target="_blank">Default Blog</a></li> \n</ul> '. \n drops the code onto a new line. | 
           
           | 


## Boolean
A boolean module creates a checkbox in the UI that prints "true" or "false." In addition to printing the value, this module is useful for defining conditional template logic, when combined with the parameter **export\_to\_template\_context**. Learn more about [**export\_to\_template\_context here**](/docs/building-blocks/modules/export-to-template-context).

#### Example
```jinja2
{% boolean "boolean" %}
{% boolean "nav_toggle" label='Hide navigation', value=False, no_wrapper=True %}
```

#### Output
```jinja2
false
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| value | Boolean | Determines whether the checkbox is checked or unchecked. | False | 


## Choice
A choice module creates a dropdown in the content editor UI that prints the value selected by the user. Choice modules are great for giving your users a preset set of options, such as printing the type of page as a page header.   
  
In addition to printing the choice value, this module is useful for defining conditional template logic, when combined with the parameter **export\_to\_template\_context**. Learn more about [**export\_to\_template\_context, here**](/docs/building-blocks/modules/export-to-template-context).

#### Example
```jinja2
{% choice "choice" %}
{% choice "type_of_page" label='Choose the type of page', value='About', choices='About, Careers, Contact, Store' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_type_of_page" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_choice" style="" data-hs-cos-general-type="widget" data-hs-cos-type="choice">
About
</span>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| value | Boolean | The default field value for the dropdown | 
| choices | Sequence | A comma-separated list of values, or list of value-label pairs. The syntax for value label pairs is as follows: choices='[[\"value1\", \"Label 1\"], [\"value2\", \"Label 2\"]]'. The editor will display the label, while it will print the value to the page. | 


## Color
The color module generates a color picker in the page editor UI that prints a HEX color value to a template. Please note that this module can only be used in templates, not CSS files. If using this tag in a &lt;style&gt; or inline CSS, you will want to use the no\_wrapper=True parameter to remove the wrapper &lt;span&gt; wrapper.

#### Example
```jinja2
{% color "color" %}
{% color "my_color_picker" label='Choose a color', color='#000000', no_wrapper=True %}
```

#### Output
```jinja2
#000000
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| color | String | A default HEX color value for the color picker | 


## CTA
A Call to Action or CTA module allows users to add a HubSpot Call to Action button to a predefined area of a page.

#### Example
```jinja2
{% cta "cta" %}
{% cta "my_cta" label='Select a CTA', guid='ccd39b7c-ae18-4c4e-98ee-547069bfbc5b', image_src='https://no-cache.hubspot.com/cta/default/53/c7335b66-a0d4-4d19-82eb-75e1626d02d0.png' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_cta" style="" data-hs-cos-general-type="widget" data-hs-cos-type="cta">
	<!--HubSpot Call-to-Action Code --> 
	<span class="hs-cta-wrapper" id="hs-cta-wrapper-ccd39b7c-ae18-4c4e-98ee-547069bfbc5b">
		<span class="hs-cta-node hs-cta-ccd39b7c-ae18-4c4e-98ee-547069bfbc5b" id="hs-cta-ccd39b7c-ae18-4c4e-98ee-547069bfbc5b" style="visibility: visible;">
			<a id="cta_button_158015_19a9097a-8dff-4181-b8f7-955a47f29826" class="cta_button " href="//cta-service-cms2.hubspot.com/ctas/v2/public/cs/c/?cta_guid=19a9097a-8dff-4181-b8f7-955a47f29826&placement_guid=ccd39b7c-ae18-4c4e-98ee-547069bfbc5b&portal_id=158015&redirect_url=APefjpFSOqhysLBE-Yye5WFoP82Swxb2PVWpfI3VxlUjuOCHfiVMcxKic3yM28vuwu9UB8_Jyhk6DGRCEN63hKqQOMtMTGmQZ1UNMK3LtNx0sRrAfQQYna2BfZ9RmgQOs8sKO_PcKOP6G26L5wQ5vdcXXOiMCxFPJxzPzUCcl474iiHKbEo5H8LVtZf6e140VOSGJ37NTpxCcPHLDvH9iFaT6mR0BnKzFReaX0FXBj7Lx2rFLVCZcIC0bdaFEGI1uKOJBMNT9RDtEzeJzUHzFYN0b34uv-ZR4w&hsutk=683eeb5b499fdfdf469646f0014603b4&utm_referrer=http%3A%2F%2Fwww.davidjosephhunt.com%2Fvariables%3Fhs_preview%3D159bC1Cj-2863569740&canon=http%3A%2F%2Fwww.davidjosephhunt.com%2Fvariables" style="" cta_dest_link="http://www.hubspot.com/free-trial" title="Start a HubSpot trial"> Start a HubSpot trial </a>
		</span>
		<script charset="utf-8" src="//js.hscta.net/cta/current.js"></script>
		<script type="text/javascript">
			hbspt.cta.load(158015, 'ccd39b7c-ae18-4c4e-98ee-547069bfbc5b');    
		</script>
	</span>  
	<!-- end HubSpot Call-to-Action Code -->
</span>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| embed_code | String | The embed code for the CTA. \n differentiates line breaks. | 
| full_html | String | The embed code for the CTA (Same as embed_code). \n differentiates line breaks. | 
| image_src | String | Image src url that defines the preview image in the content editor. | 
| image_editor | String | Markup for the image editor preview | 
| guid | String | The unique ID number of the CTA. This ID number is available in the URL of the Details screen of a particular CTA. This parameter is used to choose which CTA to display by default. | 
| image_html | String | CTA image HTML without the CTA script.* | 
| image_email | String | Email-friendly version of the CTA code.* | 


## Custom HTML
A custom HTML module allows users to enter raw HTML into the content editor. If you need to add extensive default HTML to the module, you may want to use [block syntax](/docs/hubl/hubl-module-syntax-and-parameters#block-syntax).

#### Example
```jinja2
{% raw_html "raw_html" %}
{% raw_html "my_custom_html_module" label="Enter HTML here" value='<div>My HTML Block</div>' %}


Block Syntax Example:

{% widget_block raw_html "my_custom_html_module" overrideable=True, label='My custom HTML module'  %}
        {% widget_attribute "value" %}
            <div>Default HTML block</div>
        {% end_widget_attribute %}
{% end_widget_block %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_my_custom_html_module" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_raw_html" style="" data-hs-cos-general-type="widget" data-hs-cos-type="raw_html">
    <div>My HTML block</div>
</span>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| value | String | Sets the default content HTML of the module. | 


## Custom modules
Custom Modules allow HubSpot designers to create a custom group of editable content objects to be used across templates and pages on HubSpot’s CMS, while still allowing marketers to control the specific content appearing within those modules on a page-by-page basis. You can learn more about [custom modules and their simplified HubL syntax, here](/docs/building-blocks/modules).   
  
Custom modules must be built in the Custom Module editor, but they can be included into coded templates and HubL modules. You will see a 'Usage Snippet' in the right sidebar of the Custom Module editor under 'Template Usage'.  
  
Custom modules require the ID of the module as a string as well as a path parameter in order to specify which module to load. The usage snippet will also include a label parameter. See the syntax below:

#### Example
```jinja2
{% module "module_15677217712485" path="/Custom/Test custom module"  %}
{% module "module_25642219712432" path="/Assets/Custom calendar module" label="Custom calendar module" %}
```

#### Output
```jinja2
<div id="hs_cos_wrapper_module_15677217712485" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_module" style="" data-hs-cos-general-type="widget" data-hs-cos-type="module">content!</div>
<style>
    @import "//cdn2.hubspotqa.com/qa/hub/126/file-613025667-css/custom_widget_example.css"
</style>
<div>
    <img class="persons-photo" src="//cdn2.hubspotqa.com/qa/hub/124/file-1360297556-jpeg/dharmesh.jpeg"
        alt="dharmesh.jpeg">
    <div>
        <img class="company-logo with-background"
            src="//cdn2.hubspotqa.com/qa/hub/124/file-221882251-png/HubSpot_Logo_2x.png" width="60px" height="inherit"
            alt="HubSpot_Logo_2x.png">
    </div>
</div>
<div>
    <p class="quote">
        <span class="quotation-mark"><b>" </b></span>The Content Optimization System matches content with context to
        create a highly personalized, relevant and meaningful customer experience.
        <span class="quotation-mark"><b>" </b></span>
    </p>
</div>
<div class="name-and-company">
    <span><b>Dharmesh Shah,</b></span>
    <span>HubSpot</span>
</div>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| module_id | String | The id of the module to render. | 
| path | String | The path of the module to render. Include leading slash for absolute path, otherwise path is relative to template. Reference HubSpot default modules with paths corresponding to their HubL tags such as @hubspot/rich_text, @hubspot/linked_image, etc. | 


## Email backup unsubscribe
The backup unsubscribe module renders for email recipients, if HubSpot is unable to determine their email address, when that recipient tries to unsubscribe. This module renders a form for the contact to enter his or her email address to unsubscribe from email communications. It should be used on an [Unsubscribe Backup system template.](https://knowledge.hubspot.com/cos-general/use-system-templates-to-customize-error-subscription-and-password-prompt-pages)

#### Example
```jinja2
{% email_simple_subscription "email_simple_subscription" %}
{% email_simple_subscription "email_simple_subscription" header='Email Unsubscribe', input_help_text='Your email address:', input_placeholder='email@example.com', button_text='Unsubscribe', label='Backup Unsubscribe' %}
```

#### Output
```jinja2
<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style=""></span>
<div class="page-header">
	<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style=""></span>
	<h1><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style="">Email Unsubscribe</span></h1><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style=""></span>
</div>
<form id="email-prefs-form" method="post" name="email-prefs-form" style="position: relative">
	<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style=""></span>
	<div id="content">
		<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style=""></span>
		<h3 style="font-weight: normal"><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style="">Your email address:</span></h3>
		<div style="padding-bottom: 10px">
			<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style=""><input class="email-edit hs-input" name="email" placeholder="email@example.com" style="padding: 6px; font-size: 15px; width: 507px; margin-left: 0px" type="email" value=""></span>
		</div><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style=""><input class="hs-button primary" id="submitbutton" type="submit" value="Unsubscribe"></span>
	</div><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style=""></span>
</form>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| header | String | Renders text in an h1 tag above the unsubscribe form. | "Email Unsubscribe" | 
| input_help_text | String | Renders help text in an h3 tag above your email unsubscribe form field. | "Your email address:" | 
| input_placeholder | String | Adds placeholder text within the email address form field. | "email@example.com" | 
| button_text | String | Changes the text of the unsubscribe form submit button. | "Unsubscribe" | 


## Email subscriptions
This module renders when an email recipient goes to edit his or her subscription preferences. It should be used on a [Subscription Preference system template.](https://knowledge.hubspot.com/cos-general/use-system-templates-to-customize-error-subscription-and-password-prompt-pages)

#### Example
```jinja2
{% email_subscriptions "email_subscriptions" %}
{% email_subscriptions "email_subscriptions" resubscribe_button_text='Yes, resubscribe me!', unsubscribe_single_text='Uncheck the types of emails you do not want to receive:', subheader_text='\n    If this is not your email address, please ignore this page since the email associated with this page was most likely forwarded to you.\n', unsubscribe_all_unsubbed_text='You are presently unsubscribed from all of our emails. Would you like to receive our emails again?', button_text='Update email preferences', label='Subscription Preferences', header='Communication Preferences', unsubscribe_all_option='Unsubscribe me from all mailing lists.', unsubscribe_all_text='Or check here to never receive any emails:' %}
```

#### Output
```jinja2
<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style=""></span>
<form id="email-prefs-form" method="post" name="email-prefs-form">
	<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style=""></span>
	<div class="page-header">
		<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style=""></span>
		<h1><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style="">Communication Preferences</span></h1>
		<h2><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style="">example@email.com</span></h2><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style=""><br></span>
		<p><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style="">If this is not your email address, please ignore this page since the email associated with this page was most likely forwarded to you.</span></p>
	</div>
	<div class="email-prefs" id="content">
		<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style=""></span>
		<p class="header"><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style="">Uncheck the types of emails you do not want to receive:</span></p><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style=""><input name="email" type="hidden" value="example@email.com"> <input name="unsub_url" type="hidden" value=""> <input name="unsubed_all" type="hidden" value="false"> <input name="subscription_ids" type="hidden" value=""></span>
		<div class="item">
			<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style=""></span>
			<div class="item-inner">
				<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style=""></span>
				<div class="checkbox-row">
					<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style=""><span class="fakelabel"><input id="id_0" name="id_0" type="checkbox"> <span>Example Subscription #1</span></span></span>
				</div>
				<p>Your email type description</p>
			</div>
		</div>
		<div class="item">
			<div class="item-inner">
				<div class="checkbox-row">
					<span class="fakelabel"><input id="id_0" name="id_0" type="checkbox"> <span>Example Subscription #2</span></span>
				</div>
				<p>Your email type description</p>
			</div>
		</div>
		<div class="subscribe-options" style="margin-right: 0">
			<p class="header">Or check here to never receive any emails:</p>
			<p><label for="globalunsub"><input id="globalunsub" name="globalunsub" type="checkbox"> <span>Unsubscribe me from all mailing lists.</span></label></p>
		</div><input class="hs-button primary" id="submitbutton" type="submit" value="Update email preferences">
		<div class="clearer"></div>
	</div>
</form>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| header | String | Renders text in an h1 tag above the subscription preferences form. | "Communication Preferences" | 
| subheader_text | String | Populates text below the heading above the unsubscribe preferences. | "<p>\n    If this is not your email address, please ignore this page since the email associated with this page was most likely forwarded to you.\n</p>" | 
| unsubscribe_single_text | String | Renders text in a <p class="header"> above the subscription options. | "Uncheck the types of emails you do not want to receive:" | 
| unsubscribe_all_text | String | Renders text in a <p class="header"> above the unsubscribe from all emails checkbox input. | "Or check here to never receive any emails:" | 
| unsubscribe_all_unsubbed_text | String | Populates text within a <p> that renders, if a contact is currently unsubscribed from all emails. | "You are presently unsubscribed from all of our emails. Would you like to receive our emails again?" | 
| unsubscribe_all_option | String | Sets the text next to the unsubscribe from all emails checkbox input. | "Unsubscribe me from all mailing lists." | 
| button_text | String | Sets the text of the submit button that updates subscription preferences. | "Update email preferences"  | 
| resubscribe_button_text | String | Sets the text of the submit button for when contacts are resubscribing. | "Yes, resubscribe me!" | 


## Email subscriptions confirmation
The email subscriptions update confirmation is a module that can be added to the thank you template for when a recipient updates his or her subscription preferences or unsubscribes. It should be used on a [Subscription Preference system template.](https://knowledge.hubspot.com/cos-general/use-system-templates-to-customize-error-subscription-and-password-prompt-pages)

#### Example
```jinja2
{% email_subscriptions_confirmation "email_subscriptions_confirmation" %}
{% email_subscriptions_confirmation "email_subscriptions_confirmation" label='Subscriptions Update Confirmation', unsubscribe_all_success='You have successfully unsubscribed from all email communications.', subscription_update_success='You have successfully updated your email preferences.', subheader_text='\n    If this is not your email address, please ignore this page since the email associated with this page was most likely forwarded to you.\n' %}
```

#### Output
```jinja2
<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions_confirmation" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions_confirmation" id="hs_cos_wrapper_email_subscriptions_confirmation" style=""></span>
<div class="page-header">
	<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions_confirmation" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions_confirmation" id="hs_cos_wrapper_email_subscriptions_confirmation" style=""></span>
	<h2><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions_confirmation" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions_confirmation" id="hs_cos_wrapper_email_subscriptions_confirmation" style="">example@email.com</span></h2><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions_confirmation" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions_confirmation" id="hs_cos_wrapper_email_subscriptions_confirmation" style=""><br></span>
	<p><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions_confirmation" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions_confirmation" id="hs_cos_wrapper_email_subscriptions_confirmation" style="">If this is not your email address, please ignore this page since the email associated with this page was most likely forwarded to you.</span></p>
</div>
<div class="success" id="content">
	<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions_confirmation" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions_confirmation" id="hs_cos_wrapper_email_subscriptions_confirmation" style="">You have successfully updated your email preferences.</span>
</div>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| header | String | Renders text in an h1 tag above the unsubscribe form. | "Communication Preferences" | 
| subheader_text | String | Populates text above the confirmation message. | "<p>\n    If this is not your email address, please ignore this page since the email associated with this page was most likely forwarded to you.\n</p>" | 
| unsubscribe_all_success | String | Sets the text that will display when someone unsubscribes from all email communications. | "You have successfully unsubscribed from all email communications." | 
| subscription_update_success | String | Sets the text when a recipient updates his or her subscription preferences. | "You have successfully updated your email preferences." | 


## Flexible column
Flexible columns are vertical columns in a template that allow the end user to insert and remove a variety of modules of their choosing into the template, while [editing in the content editor](https://knowledge.hubspot.com/cos-pages-editor/how-to-use-flexible-columns-in-your-pages). When coding a flexible column with HubL, you can choose to wrap other HubL modules to make them appear in the flexible column by default. The sample code below shows the basic syntax and a sample flexible column with a rich-text and form module contained as default content. Please note that flexible columns can only be added to page templates, not blog or email templates.

#### Example
```jinja2
{% widget_container "my_flexible_column" %}
    {% rich_text "my_rich_text" %}
    {% rich_text "second_rich_text" %}
{% end_widget_container %}
```

#### Output
```jinja2
<span class="hs_cos_wrapper hs_cos_wrapper_widget_container hs_cos_wrapper_type_widget_container" data-hs-cos-general-type="widget_container" data-hs-cos-type="widget_container" id="hs_cos_wrapper_my_flexible_column" style=""></span>
<div class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_rich_text" data-hs-cos-general-type="widget" data-hs-cos-type="rich_text" id="hs_cos_wrapper_widget_2822416670" style="">
	<span class="hs_cos_wrapper hs_cos_wrapper_widget_container hs_cos_wrapper_type_widget_container" data-hs-cos-general-type="widget_container" data-hs-cos-type="widget_container" id="hs_cos_wrapper_my_flexible_column" style=""></span>
</div>
<div class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_rich_text" data-hs-cos-general-type="widget" data-hs-cos-type="rich_text" id="hs_cos_wrapper_widget_2822416675" style="">
	<span class="hs_cos_wrapper hs_cos_wrapper_widget_container hs_cos_wrapper_type_widget_container" data-hs-cos-general-type="widget_container" data-hs-cos-type="widget_container" id="hs_cos_wrapper_my_flexible_column" style=""></span>
</div>
```


## Form
Allows users to select a HubSpot form to add to their page.

#### Example
```jinja2
{% form "form" %}
{% form "my_form" form_to_use='08bd9f0d-3be9-41c2-93b6-231a3a71b143', title='Free Trial' %}


Block Syntax Example:
{% widget_block form "my_form" form_follow_ups_follow_up_type='', response_redirect_id=306590405, form_to_use='08bd9f0d-3be9-41c2-93b6-231a3a71b143', title='Free Trial', notifications_are_overridden=True, sfdc_campaign='', response_message='Thanks for submitting the form.', response_response_type='redirect', response_redirect_url='', overrideable=True, gotowebinar_webinar_key='', response_redirect_name='Homepage (http://www.hubspot.com/)', label='Form', response={message='Thank you for submitting the form.', redirect_url=''}  %}
        {% widget_attribute "notifications_override_email_addresses" is_json=True %}["noreply@hubspot.com"]{% end_widget_attribute %}
{% end_widget_block %}
```

#### Output
```jinja2
<div id="hs_cos_wrapper_my_form" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_form" style="" data-hs-cos-general-type="widget" data-hs-cos-type="form">
    <h3 id="hs_cos_wrapper_module_13885064832664947_title" class="hs_cos_wrapper form-title" data-hs-cos-general-type="widget_field" data-hs-cos-type="text">Free Trial</h3>
    <div id="hs_form_target_module_13885064832664947">
        <form accept-charset="UTF-8" enctype="multipart/form-data" id="hsForm_08bd9f0d-3be9-41c2-93b6-231a3a71b143_6756" class="hs-form stacked hs-custom-form" action="https://forms.hubspot.com/uploads/form/v2/158015/08bd9f0d-3be9-41c2-93b6-231a3a71b143" method="POST" novalidate="novalidate">
            <div class="hs_lastname field hs-form-field">
                <label placeholder="Enter your Last Name" for="lastname-08bd9f0d-3be9-41c2-93b6-231a3a71b143_6756">Last Name</label>
                <div class="hs-field-desc" style="display: none;"></div>
                <div class="input">
                    <input class="hs-input" type="text" id="lastname-08bd9f0d-3be9-41c2-93b6-231a3a71b143_6756" name="lastname" value="" placeholder="">
                </div>
            </div>
            <div class="hs_firstname field hs-form-field">
                <label placeholder="Enter your First Name" for="firstname-08bd9f0d-3be9-41c2-93b6-231a3a71b143_6756">First Name</label>
                <div class="hs-field-desc" style="display: none;"></div>
                <div class="input">
                    <input class="hs-input" type="text" id="firstname-08bd9f0d-3be9-41c2-93b6-231a3a71b143_6756" name="firstname" value="" placeholder="">
                </div>
            </div>
            <div class="hs_email field hs-form-field">
                <label placeholder="Enter your Email" for="email-08bd9f0d-3be9-41c2-93b6-231a3a71b143_6756">Email<span class="hs-form-required"> * </span></label>
                <div class="hs-field-desc" style="display: none;"></div>
                <div class="input">
                    <input class="hs-input" type="email" required="required" id="email-08bd9f0d-3be9-41c2-93b6-231a3a71b143_6756" name="email" value="" placeholder="">
                </div>
            </div>
            <div class="hs_submit">
                <div class="hs-field-desc" style="display: none;"></div>
                <div class="actions">
                    <input class="hs-button primary large" type="submit" value="Submit">
                </div>
            </div>
        </form>
    </div>
    <script charset="utf-8" src="//js.hsforms.net/forms/current.js"></script>
    <script>
        hbspt.forms.create({
            portalId: '158015',
            formId: '08bd9f0d-3be9-41c2-93b6-231a3a71b143',
            formInstanceId: '6756',
            pageId: 1,
            redirectUrl: "http:\/\/www.davidjosephhunt.com\/404",
            deactivateSmartForm: true,
            css: '',
            target: '#hs_form_target_module_13885064832664947',
            contentType: "landing-page",
            formData: {
            cssClass: 'hs-form stacked hs-custom-form'
            }
        });
    </script>
</div>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| form_key | String | Specifies a unique id for the form at the page level. | 
           
           | 
| form_to_use | String | Specifies which form to load by default, based on the Form ID. This ID is available in the form editor URL of a each form. | 
           
           | 
| title | String | Populates an h3 header tag above the form. | 
           
           | 
| no_title | Boolean |  If True, the h3 tag above the title is removed. | False | 
| form_follow_ups_follow_up_type | Enumeration | Specifies follow up actions such as enrolling a contact into a workflow or sending a simple follow up email. Possible values include: no_action, simple, and automation. | 
           
           | 
| simple_email_for_live_id | Number | Specifies the ID of the simple follow-up email for the live page. | 
           
           | 
| simple_email_for_buffer_id | Number | Specifies the ID of the simple follow-up email for the auto-save version of a page. | 
           
           | 
| follow_up_type_simple | Boolean | If true, enables a simple follow-up email. Alternative to form_follow_ups_follow_up_type. | 
           
           | 
| follow_up_type_automation | Boolean | If true, enrolls submissions in a workflow. Alternative to form_follow_ups_follow_up_type. | 
           
           | 
| simple_email_campaign_id | Number | Specifies the ID of the simple follow-up email. Alternative to simple_email_for_live_id. | 
           
           | 
| form_follow_ups_workflow_id | Number | Specifies the ID of the workflow in which to enroll submissions. | 
           
           | 
| response_redirect_url | String | If redirecting to an external page, this parameter specifies the URL to redirect to. | 
           
           | 
| response_redirect_id | Number | If redirecting to HubSpot hosted page, this parameter specifies the page ID of that page. The page ID is available in the page editor URL of each page. | 
           
           | 
| response_response_type | Enumeration | Determines whether to redirect to another page or to display an inline thank you message on submission. The value of this parameter should either be 'redirect' or 'inline'. | inline | 
| response_message | String | Sets an inline thank you message. This parameter supports HTML. | 
           
           | 
| notifications_are_overridden | Boolean | If True, the form will send form notifications to specified email addresses selected in the notifications_override_email_addresses parameter, instead of the form defaults | False | 
| notifications_override_guid_buffer | String | ID of override settings in auto-save version of page. | 
           
           | 
| notifications_override_guid | String | ID of override settings in live version of page. | 
           
           | 
| notifications_override_email_addresses | JSON | Block syntax supports a JSON list of email recipients that will be notified upon form submission. These email addresses will override the email notification settings set in the form. | 
           
           | 
| gotowebinar_webinar_key | String | Specifies the GoToWebinar webinar to enroll contacts who submit the form into. Only available for portals using the GoToWebinar integration. | 
           
           | 
| sfdc_campaign | String | Specifies the Salesforce campaign to enroll contacts who submit the form into. This parameter's value should be the SFDC campaign ID and is only available for portals that are integrated with Salesforce. | 
           
           | 


## Footer
Renders copyright information with the year and company name specified in Content Settings (Email &gt; Footer Information).

#### Example
```jinja2
{% page_footer "page_footer" %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_page_footer" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_page_footer" style="" data-hs-cos-general-type="widget" data-hs-cos-type="page_footer">
    <footer>
        <span class="hs-footer-company-copyright">© 2020 HubSpot</span>
    </footer>
</span>
```


## Gallery
Generates a HubSpot gallery module. This gallery module is based on [Slick](http://kenwheeler.github.io/slick/). While you can create a gallery module with standard module HubL syntax, If you want to predefine default slides using HubL, you must use block syntax. Both methods are shown below.

#### Example
```jinja2
{% gallery "crm_gallery" %}

<-- Block syntax -->
{% widget_block gallery "Gallery" display_mode='standard' sizing='static', transition='slide', caption_position='below', auto_advance=True, overrideable=True, description_text='', show_pagination=True, label='Gallery', loop_slides=True, num_seconds=5  %}
    {% widget_attribute "slides" is_json=True %}
        [{
            "caption": "CRM Contacts App", 
            "show_caption": true, 
            "link_url": "http://www.hubspot.com/crm", 
            "alt_text": "Screenshot of CRM Contacts", 
            "img_src": "http://go.hubspot.com/hubfs/Contacts-View-1.png?t=1430860504240", 
            "open_in_new_tab": true
        }, 
        {
            "caption": "HubSpot CRM Contact Profile", 
            "show_caption": true, 
            "link_url": "http://www.hubspot.com/", 
            "alt_text": "HubSpot CRM Contact Profile", 
            "img_src": "http://cdn2.hubspot.net/hubfs/53/Contact-Profile.png?t=1430860504240", 
            "open_in_new_tab": true
        }]
    {% end_widget_attribute %}
{% end_widget_block %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_crm_gallery" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_gallery" style=""
    data-hs-cos-general-type="widget" data-hs-cos-type="gallery">
    <div id="hs_cos_flex_gallery_crm_gallery" class="hs_cos_flex-gallery flex-gallery-main gallery-mode-gallery">
        <div class="hs_cos_flex-viewport" style="overflow: hidden; position: relative;">
            <ul class="hs_cos_flex-slides hs_cos_flex-slides-main "
                style="width: 800%; -webkit-transition-duration: 0s; transition-duration: 0s; -webkit-transform: translate3d(-1090px, 0px, 0px);">
                <li class="hs_cos_flex-slide-main clone" aria-hidden="true"
                    style="width: 1090px; float: left; display: block;">
                    <a href="//www.hubspot.com/" target="_blank"><img
                            src="//cdn2.hubspot.net/hubfs/53/Contact-Profile.png?t=1430860504240&t=1430335520686"
                            alt="HubSpot CRM Contact Profile" draggable="false"></a>
                    <div class="caption">
                        HubSpot CRM Contact Profile
                    </div>
                </li>
                <li class="hs_cos_flex-slide-main hs_cos_flex-active-slide"
                    style="width: 1090px; float: left; display: block;">
                    <a href="//www.hubspot.com/crm" target="_blank"><img
                            src="http://go.hubspot.com/hubfs/Contacts-View-1.png?t=1430860504240&t=1430335520686"
                            alt="Screenshot of CRM Contacts" draggable="false"></a>
                    <div class="caption">
                        CRM Contacts App
                    </div>
                </li>
                <li class="hs_cos_flex-slide-main" style="width: 1090px; float: left; display: block;">
                    <a href="//www.hubspot.com/" target="_blank"><img
                            src="//cdn2.hubspot.net/hubfs/53/Contact-Profile.png?t=1430860504240&t=1430335520686"
                            alt="HubSpot CRM Contact Profile" draggable="false"></a>
                    <div class="caption">
                        HubSpot CRM Contact Profile
                    </div>
                </li>
                <li class="hs_cos_flex-slide-main clone" aria-hidden="true"
                    style="width: 1090px; float: left; display: block;">
                    <a href="//www.hubspot.com/crm" target="_blank"><img
                            src="http://go.hubspot.com/hubfs/Contacts-View-1.png?t=1430860504240&t=1430335520686"
                            alt="Screenshot of CRM Contacts" draggable="false"></a>
                    <div class="caption">
                        CRM Contacts App
                    </div>
                </li>
            </ul>
        </div>
        <ol class="hs_cos_flex-control-nav hs_cos_flex-control-paging">
            <li><a class="hs_cos_flex-active">1</a></li>
            <li><a class="">2</a></li>
        </ol>
        <ul class="hs_cos_flex-direction-nav">
            <li><a class="hs_cos_flex-prev" href="#">Previous</a></li>
            <li><a class="hs_cos_flex-next" href="#">Next</a></li>
        </ul>
    </div>
    <script>
        window.hsSliderConfig = window.hsSliderConfig || {};
        window.hsSliderConfig['crm_gallery'] = {
            mode: 'gallery',
            mainConfig: {
                "animationLoop": true,
                "direction": "horizontal",
                "slideshowSpeed": 5000.0,
                "controlNav": true,
                "smoothHeight": false,
                "namespace": "hs_cos_flex-",
                "slideshow": true,
                "selector": ".hs_cos_flex-slides > li",
                "animation": "slide"
            }
        };
    </script>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| slides | JSON | A JSON list of the default caption, the link url, the alt text, the image src, and whether to open in a new tab. See block syntax above. | 
           
           | 
| loop_slides | Boolean | When True, continuously loop through slides. | True | 
| num_seconds | Number | Time in seconds to pause between slides. | 5 | 
| show_pagination | Boolean | Provide buttons below slider to navigate among slides. | True | 
| sizing | Enumeration | Determines whether the slider changes sizes, based on the height of the slides. Possible values include: "static" or "resize". | "static" | 
| auto_advance | Boolean | Automatically advance slides after the time set in num_seconds. | False | 
| transition | Enumeration | Sets the type of slide transition. Possible values include: "fade" or "slide". | "slide" | 
| caption_position | Enumeration | Affects positioning of caption on or below the slide. Possible values include "below" or "superimpose". | "below" | 
| display_mode | Enumeration | Determines how the image gallery will be displayed. Possible values include: "standard", "lightbox", "thumbnail". | "standard" | 
| lightboxRows | Number | If "display_mode" is set to "lightbox", this parameter will control the number of rows displayed within the lightbox. | 3 | 


## Header
Generates a header module that will render text as an h1-h6 tag.

#### Example
```jinja2
{% header "header"  %}
{% header "my_header" header_tag='h1', overrideable=True, value='A clear and bold header', label='Header' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_my_header" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_header" style="" data-hs-cos-general-type="widget" data-hs-cos-type="header">
    <h1>A clear and bold header</h1>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| header_tag | String | Select which heading tag to render. Possible values include: h1, h2, h3, h4, h5, h6. | h1 | 
| value | String | Renders default text within the heading module. | "A clear bold header" | 


## Image
Creates a image module that allows users to select an image from the content editor. If you want the image to be linked to a destination URL, you should use linked\_image below.

#### Example
```jinja2
{% image "image" %}
{% image "executive_image" label='Executive photo', alt='Photo of Brian Halligan', src='//cdn2.hubspot.net/hub/53/file-733888619-jpg/assets/hubspot.com/about/management/brian-home.jpg', width='300' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_executive_image" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_image" style="" data-hs-cos-general-type="widget" data-hs-cos-type="image">
    <img src="//cdn2.hubspot.net/hub/53/file-733888619-jpg/assets/hubspot.com/about/management/brian-home.jpg?width=300" class="hs-image-widget " width="300" alt="Photo of Brian Halligan" title="Photo of Brian Halligan">
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| alt | String | Sets the default alt text for the image. | 
           
           | 
| src | String | Populates the src attribute of the img tag. | 
           
           | 
| width | Number | Sets the width attribute of the img tag. | The width of the image | 
| height | Number | Sets a min-height in a style attribute of the img tag for email templates only. | The height of the image | 
| hspace | Number | Sets the hspace attribute of the img tag. | 
           
           | 
| align | String | Sets the align attribute of the img tag. Possible values include: left, right, & center. | 
           
           | 
| style | String | Adds inline CSS declarations to the img tag. For example style="border:1px solid blue; margin:10px" | 
           
           | 


## Image src
An image src module creates a image selector in the content editor, but rather than printing a img tag, it renders the URL of the image. This tag is generally used with no\_wrapper=True parameter, so that the image src can be added to inline CSS or other markup. An alternative to using this tag is to use the export\_to\_template\_context parameter.

#### Example
```jinja2
{% image_src "image_src" %}
{% image_src "executve_image_src" src='//cdn2.hubspot.net/hub/53/file-733888614-jpg/assets/hubspot.com/about/management/dharmesh-home.jpg', no_wrapper=True %}
```

#### Output
```jinja2
//cdn2.hubspot.net/hub/53/file-733888614-jpg/assets/hubspot.com/about/management/dharmesh-home.jpg
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| src | String |  Specifies the default URL image src. | 
           
           | 


## Language switcher
Adds a Globe Icon with links to the translated versions of a given CMS page. Learn more about [multi-language content here](https://knowledge.hubspot.com/cos-general/how-to-manage-multi-language-content-with-hubspots-cos).

#### Example
```jinja2
{% language_switcher "language_switcher" overrideable=false, display_mode='localized', label='Language Switcher' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_module_1487954976079503" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_language_switcher" style="" data-hs-cos-general-type="widget" data-hs-cos-type="language_switcher">
  <div class="lang_switcher_class">
     <div class="globe_class">
         <ul class="lang_list_class">
             <li>
                 <a class="lang_switcher_link" href="http://www.hubspot.com">English</a>
             </li>
             <li>
                 <a class="lang_switcher_link" href="http://www.hubspot.com/es">Spanish</a>
             </li>
         </ul>
     </div>
  </div>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| display_mode | Enumeration | The language of the text in the language switcher. Values are:

Pagelang means the names of languages will display in the language of the page the switcher is on.
Localized means the name of each language will display in that language.
Hybrid is a combination of the two.
 | Localized | 


## Linked image
Creates a user-selectable image that is wrapped in a link. This module has all of the parameters of an image module with two additional parameters that specify the link destination URL and whether the link opens in a new window.

#### Example
```jinja2
{% linked_image "linked_image" %}
{% linked_image "executive_image" label='Executive photo', link="https://twitter.com/bhalligan", open_in_new_tab=True, alt='Photo of Brian Halligan', src='//cdn2.hubspot.net/hub/53/file-733888619-jpg/assets/hubspot.com/about/management/brian-home.jpg', width='300' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_executive_image" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_linked_image" style="" data-hs-cos-general-type="widget" data-hs-cos-type="linked_image">
    <a href="https://twitter.com/bhalligan" target="_blank" id="hs-link-executive_image" style="border-width:0px;border:0px;">
        <img src="//cdn2.hubspot.net/hub/53/file-733888619-jpg/assets/hubspot.com/about/management/brian-home.jpg?width=300" class="hs-image-widget " style="width:300px;border-width:0px;border:0px;" width="300" alt="Photo of Brian Halligan" title="Photo of Brian Halligan">
    </a>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| alt | String | Sets the default alt text for the image. | 
           
           | 
| src | String | Populates the src attribute of the img tag. | 
           
           | 
| width | Number | Sets the width attribute of the img tag. | The width of the image | 
| height | Number | Sets a min-height in a style attribute of the img tag for email templates only. | The height of the image | 
| hspace | Number | Sets the hspace attribute of the img tag. | 
           
           | 
| align | String | Sets the align attribute of the img tag. Possible values include: left, right, & center. | 
           
           | 
| style | String | Adds inline CSS declarations to the img tag. For example style="border:1px solid blue; margin:10px" | 
           
           | 
| open_in_new_tab | Boolean | Selects whether or not to open the destination URL in another tab. | False | 
| link | String | Sets the destination URL of the link that wraps the img tag. | 
           
           | 
| target | String | Sets the target attribute of the link tag. | 
           
           | 


## Logo
A logo module renders your company's logo image from Content Settings.

#### Example
```jinja2
{% logo "logo" %}
{% logo "my_logo" width='200' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_my_logo" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_logo" style="" data-hs-cos-general-type="widget" data-hs-cos-type="logo">
    <a href="//www.hubspot.com" id="hs-link-my_logo">
        <img src="//cdn2.hubspot.net/hub/53/file-1237149549-png/assets/hubspot.com/V2-Global/hubspot-logo-dark.png?t=1430948896766&amp;width=200" class="hs-image-widget " width="200" alt="HubSpot logo" title="HubSpo logot">
    </a>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| suppress_company_name | Boolean | Hides company name if an image logo isn't set. | False | 
| alt | String | Sets the default alt text for the image. | Value in Content Settings | 
| src | String | Populates the src attribute of the img tag. | Value in Content Settings | 
| width | Number | Sets the width attribute of the img tag. | The width of the image | 
| height | Number | Sets a min-height in a style attribute of the img tag for email templates only. | The height of the image | 
| hspace | Number | Sets the hspace attribute of the img tag. | 
           
           | 
| align | String | Sets the align attribute of the img tag. Possible values include: left, right, & center. | 
           
           | 
| style | String | Adds inline CSS declarations to the img tag. For example style="border:1px solid blue; margin:10px" | 
           
           | 
| open_in_new_tab | Boolean | Selects whether or not to open the destination URL in another tab. | False | 
| link | String | Sets the destination URL of the link that wraps the img tag. | 
           
           | 
| override_inherited_src | Boolean | If true, use src from logo widget rather than src inherited from settings or template. | True | 


## Menu
Generates an advanced menu based on a menu tree in **Content Settings &gt; Advanced Menus.**

#### Example
```jinja2
{% menu "menu" %}
{% menu "my_menu" id=456, site_map_name='Default', overrideable=False, root_type='site_root', flyouts='true', max_levels='2', flow='horizontal', label='Advanced Menu' %}
```

#### Output
```jinja2
<div id="hs_menu_wrapper_my_menu" class="hs-menu-wrapper active-branch flyouts hs-menu-flow-horizontal" data-sitemap-name="Default">
    <ul>
        <li class="hs-menu-item hs-menu-depth-1"><a href="http://www.underseaband.com/music">Music</a></li>
        <li class="hs-menu-item hs-menu-depth-1"><a href="http://www.underseaband.com/shows">Shows</a></li>
        <li class="hs-menu-item hs-menu-depth-1"><a href="http://www.underseaband.com/blog">Blog</a></li>
        <li class="hs-menu-item hs-menu-depth-1"><a href="http://www.underseaband.com/contact">Contact</a></li>
    </ul>
</div>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| id | Integer | ID of Menu Tree from Advanced Menus in Content Settings. | 
           
           | 
| site_map_name | String | Name of Menu Tree from Advanced Menus in Content Settings. |  'default' | 
| root_type | Enumeration | Specifies the type of advanced menus. Options include: "site_root", "top_parent", "parent", "page_name", "page_id", and "breadcrumb". These values correspond to static, dynamic by section, dynamic by page, and breadcrumb. |  'site_root' | 
| flyouts | String | When true, a class is added to the menu tree that can be styled to allow child menu items will appear when you hover over the parent. When false, child menu items will always appear. |  'true' | 
| max_levels | Integer | Determines how many levels of nested menus render in the markup. This parameter dictates number of menu tree children that can be expanded in the menu. | 2 | 
| flow | Enumeration | Sets orientation of menu items. This adds classes to menu tree, so that they can be styled accordingly. Possible values include "horizontal", "vertical" or "vertical_flyouts". Horizontal menus display items side-by-side, and vertical menus are top-to-bottom. |  'horizontal' | 
| root_key | String | Used to find the menu root. When root_type is set to page_id or page_name, this param should be the page ID or the label of the page, respectively. | 'horizontal' | 


## Password prompt
Adds a password prompt to password-protected pages.

#### Example
```jinja2
{% password_prompt "password_prompt" %}
{% password_prompt "my_password_prompt" submit_button_text='Submit', bad_password_message='Sorry, please try again.\n', label='Password Prompt' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_password_prompt" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_password_prompt" style="" data-hs-cos-general-type="widget" data-hs-cos-type="password_prompt">
    <form method="post" action="/_hcms/protected/auth">
        <input name="content_id" type="hidden" value="1">
        <input name="redirect_url" type="hidden" value="https://preview.hs-sites.com/content-rendering/v1/public/_hcms/preview/template/multi">
        <input name="password" type="password" id="hs-pwd-widget-password" style="height: 22px; margin-top: -5px">
        <input type="submit" class="hs-button primary large" value="Submit">
    </form>
    <script type="text/javascript">
        document.getElementById("hs-pwd-widget-password").focus();
    </script>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| submit_button_text | String |  Label for button below password entry field. | 'Submit' | 
| bad_password_message | String |  Message displayed if incorrect password entered. |  '<p>Sorry, please try again.</p>' | 
| password_placeholder | String |  Defines placeholder text within the password field. | 'Password' | 


## Post filter
Creates a linked listing of posts by topic, posts by month, or posts by author.

#### Example
```jinja2
{% post_filter "post_filter" %}
{% post_filter "posts_by_topic" select_blog='default', expand_link_text='see all', overrideable=False, list_title='Posts by Topic', max_links=5, filter_type='topic', label='Posts by Topic' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_posts_by_topic" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_post_filter" style="" data-hs-cos-general-type="widget" data-hs-cos-type="post_filter">
    <div class="block">
        <h3>Posts by Topic</h3>
        <div class="widget-module">
            <ul>
                <li><a href="http://www.underseaband.com/blog/topic/pedals">pedals (15)</a></li>
                <li><a href="http://www.underseaband.com/blog/topic/music-recommendations">music recommendations (7</a></li>
                <li><a href="http://www.underseaband.com/blog/topic/undersea">Undersea (6)</a> </li>
                <li> <a href="http://www.underseaband.com/blog/topic/band">band (2)</a> </li>
                <li> <a href="http://www.underseaband.com/blog/topic/diy-tips">DIY tips (2)</a> </li>
                <li> <a href="http://www.underseaband.com/blog/topic/visual-artists">Visual artists (1)</a> </li>
            </ul>
        </div>
    </div>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| select_blog | 'default' or blog ID | Selects the HubSpot blog to use. This parameter uses either an blog ID or 'default' value. | 'default' | 
| expand_link_text | String |  Text link to display if more posts than max_links number available. Exclude parameter to omit link. | 'see all' | 
| list_title | String | List title to display. | '' | 
| list_tag | String | Sets the tag used for the list. Value should generally be 'ul' or 'ol'. | 'ul' | 
| title_tag | String | Sets the tag used for the list title. | 'h3' | 
| max_links | Number | Maximum number of filter values to display. Excude parameter to show all. | 5 | 
| filter_type | Enumeration | Selects the type of filter. Possible values include 'topic', 'month', and 'author'. | 'topic' | 


## Post Listing
Adds a listing of most popular or top posts.

#### Example
```jinja2
{% post_listing "post_listing" %}
{% post_listing "top_posts" select_blog='default', label='Recent Posts', overrideable=False, list_title='Recent Posts', listing_type='recent', max_links=5 %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_top_posts" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_post_listing" style="" data-hs-cos-general-type="widget" data-hs-cos-type="post_listing">
    <div class="block">
        <h3>Most popular posts</h3>
        <div class="widget-module">
            <ul>
                <li><a href="http://www.underseaband.com/blog/5-emerging-bands-that-you-need-to-hear">5 emerging bands that you need to hear</a></li>
                <li><a href="http://www.underseaband.com/blog/pedal-board-power-supplies">Pedal Board Power Supplies</a></li>
                <li><a href="http://www.underseaband.com/blog/pedal-board-wiring">Pedal Board Wiring</a></li>
                <li><a href="http://www.underseaband.com/blog/pedal-board-layouts">Pedal Board Layouts</a></li>
                <li><a href="http://www.underseaband.com/blog/your-teeth-shake">Your Teeth Shake</a></li>
            </ul>
        </div>
    </div>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| select_blog | 'default' or blog ID |  Selects the HubSpot blog to use for the listing. This parameter uses either an blog ID or 'default' value. | 'default' | 
| list_title | String | List title to display. | '' | 
| list_tag | String | Sets the tag used for the list. Value should generally be 'ul' or 'ol'. | 'ul' | 
| title_tag | String | Sets the tag used for the list title. | 'h3' | 
| listing_type | String | List the blog posts by most recent or most popular in a time range. Possible values include recent, popular_all_time, popular_past_year, popular_past_six_months, and popular_past_month. | 'recent' | 
| max_links | Number |  Maximum number of blog posts to list. | 5 | 
| include_featured_image | Boolean |  Display featured image along with post link. | False | 


## Require_css
A HubL tag that enqueues a style element to be rendered in the &lt;head&gt;. To enqueue a stylesheet from a different file to render in the &lt;head /&gt; via a &lt;link /&gt; tag (as opposed to inline as shown here), use the HubL function require\_css(absolute\_url) instead.

#### Example
```jinja2
{{ standard_header_includes }}
<!-- more html -->

{% require_css %}
    <style>
        body {
            color: red;
        }
    </style>
{% end_require_css %}

{{ standard_footer_includes }}
```

#### Output
```jinja2
<!-- other standard header html -->
    <style>
        body {
            color: red;
        }
    </style>
<!-- more html -->
<!-- other standard footer html -->
```


## Require_js
A HubL tag that enqueues a script element to be rendered. To enqueue a script to render in the &lt;head /&gt;from a different file via a &lt;script /&gt; element (as opposed to inline as shown here), use the HubL function require\_js(absolute\_url) instead.

#### Example
```jinja2
{{ standard_header_includes }}
<!-- more html -->

{% require_js position="footer" %}
    <script>
        console.log("The CMS is awesome!");
    </script>
{% end_require_js %}

{{ standard_footer_includes }}
```

#### Output
```jinja2
<!-- other standard header html -->
<!-- more html -->
<script>
    console.log("The CMS is awesome!");
</script>
<!-- other standard footer html -->
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| position | String | Set the position where the inline script will be rendered. Options include: "head" and "footer". | 'footer' | 


## Rich text
Creates a WYSIWYG content editor.

#### Example
```jinja2
{% rich_text "rich_text" %}
{% rich_text "left_column" label="Enter HTML here" html='<div>My rich text default content</div>' %}


Block Syntax Example:


{% widget_block rich_text "right_column" overrideable=True, label='Right Column'  %}
    {% widget_attribute "html" %}
            <h2>Something Powerful</h2>
            <h3>Tell The Reader More</h3>
            <p>The headline and subheader tells us what you're offering, and the form header closes the deal. Over here you can explain why your offer is so great it's worth filling out a form for.</p>
            <p>Remember:</p>
            <ul>
                <li>Bullets are great</li>
                <li>For spelling out <a href="#">benefits</a> and</li>
                <li>Turning visitors into leads.</li>
            </ul>
    {% end_widget_attribute %}
{% end_widget_block %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_right_column" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_rich_text" style="" data-hs-cos-general-type="widget" data-hs-cos-type="rich_text">
    <h2>Something Powerful</h2>
    <h3>Tell The Reader More</h3>
    <p>The headline and subheader tells us what you're offering, and the form header closes the deal. Over here you can explain why your offer is so great it's worth filling out a form for.</p>
    <p>Remember:</p>
    <ul>
        <li>Bullets are great</li>
        <li>For spelling out benefits and</li>
        <li>Turning visitors into leads.</li>
    </ul>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| html | String | Default rich text content for module. | <h2>Something Powerful</h2> <h3>Tell The Reader More</h3> <p>The headline and subheader tells us what you're offering, and the form header closes the deal. Over here you can explain why your offer is so great it's worth filling out a form for.</p> <p>Remember:</p> <ul> <li>Bullets are great</li> <li>For spelling out <a href="#">benefits</a> and</li> <li>Turning visitors into leads.</li> </ul> | 


## RSS listing
Loads a list of content from an internal or external RSS feed.

#### Example
```jinja2
{% rss_listing "rss_listing" %}
{% rss_listing "my_rss_listing" rss_url='', publish_date_text='posted at', feed_source={rss_url='', is_external=False, content_group_id='24732847'}, click_through_text='Read more', show_date=True, include_featured_image=True, overrideable=False, publish_date_format='short', show_detail=True, show_author=True, number_of_items='5', is_external=False, title='', content_group_id='24732847', label='RSS Listing', limit_to_chars='200', attribution_text='by' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_my_rss_listing" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_rss_listing" style="" data-hs-cos-general-type="widget" data-hs-cos-type="rss_listing">
    <h3></h3>
    <div class="hs-rss-module feedreader_box">
        <div class="hs-rss-item hs-with-featured-image">
            <div class="hs-rss-item-text">
                <a class="hs-rss-title" href="http://www.underseaband.com/blog/city-where-stars-are-not"><span>City
                        Where Stars Are Not</span></a>
                <div class="hs-rss-byline">by <span class="hs-rss-author">Matthew Vincenty</span>
                    <span class="hs-rss-posted-at">posted at</span> <span class="hs-rss-date">5/1/15 11:02 AM</span>
                </div>
                <div class="hs-rss-description">
                    <p> We are pleased to announce the release of our next single "City Where Stars Are Not"! It will be
                        available Tuesday May 5th and features lead vocals by bassist David Hunt. Thanks to Peter...<a
                            href="http://www.underseaband.com/blog/city-where-stars-are-not">Read more</a> </p>
                </div>
            </div>
            <div class="hs-rss-item-image-wrapper">
                <img class="hs-rss-featured-image" src="http://www.underseaband.com/hubfs/Blog_Images/citywherestarsarenot.png?t=1430835551915"> 
            </div>
        </div>
        <div class="hs-rss-item hs-with-featured-image">
            <div class="hs-rss-item-text">
                <a class="hs-rss-title" href="http://www.underseaband.com/blog/loud-louder"><span>New Pedal! ChadderBox
                        Effects Loud Louder</span></a>
                <div class="hs-rss-byline">by <span class="hs-rss-author">Corey Wade</span>
                    <span class="hs-rss-posted-at">posted at</span> <span class="hs-rss-date">4/27/15 10:30 AM</span>
                </div>
                <div class="hs-rss-description">
                    <p>
                        I have the good fortune to have recently met Chad from ChadderBox Effects. It turns out he works
                        part-time on the same floor in the same building where I also work part-time. When I found out
                        Chad...<a href="http://www.underseaband.com/blog/loud-louder">Read more</a> </p>
                </div>
            </div>
            <div class="hs-rss-item-image-wrapper"> <img class="hs-rss-featured-image"
                    src="http://www.underseaband.com/hubfs/Blog_Images/10724991_612551458879970_1563949619_n.jpg?t=1430835551915">
            </div>
        </div>
        <div class="hs-rss-item hs-with-featured-image">
            <div class="hs-rss-item-text"> <a class="hs-rss-title"
                    href="http://www.underseaband.com/blog/introducing-ariél-torres"><span>Introducing: Ariél
                        Torres</span></a>
                <div class="hs-rss-byline">by <span class="hs-rss-author">Corey Wade</span> <span
                        class="hs-rss-posted-at">posted at</span> <span class="hs-rss-date">4/24/15 10:30 AM</span>
                </div>
                <div class="hs-rss-description">
                    <p> Everyone needs to check out Boston-based visual artist Ariél Torres’ work. He was very nice to
                        let us use one of his pieces for “Your Teeth Shake”, and we couldn’t be more stoked about it.
                        Check out...<a href="http://www.underseaband.com/blog/introducing-ariél-torres">Read more</a>
                    </p>
                </div>
            </div>
            <div class="hs-rss-item-image-wrapper"> <img class="hs-rss-featured-image"
                    src="http://www.underseaband.com/hubfs/tangledupinblue-449270-edited.jpg?t=1430835551915"> </div>
        </div>
        <div class="hs-rss-item hs-with-featured-image">
            <div class="hs-rss-item-text"> 
                <a class="hs-rss-title" href="http://www.underseaband.com/blog/new-pedal-fuzzrocious-rat-tail"><span>New Pedal! Fuzzrocious Rat Tail</span></a>
                <div class="hs-rss-byline">by <span class="hs-rss-author">Matthew Vincenty</span> <span
                        class="hs-rss-posted-at">posted at</span> <span class="hs-rss-date">4/21/15 4:34 PM</span>
                </div>
                <div class="hs-rss-description">
                    <p> I found myself in the position of needing to put together a new board to fill in on guitar with
                        our friends Glacier.&nbsp;First I needed a distortion pedal that could pull of their heavier
                        bits so I...<a href="http://www.underseaband.com/blog/new-pedal-fuzzrocious-rat-tail">Read
                            more</a> </p>
                </div>
            </div>
            <div class="hs-rss-item-image-wrapper"> <img class="hs-rss-featured-image"
                    src="http://www.underseaband.com/hubfs/Blog_Images/11023171_476701342477661_420938091_n.jpg?t=1430835551915">
            </div>
        </div>
        <div class="hs-rss-item hs-with-featured-image">
            <div class="hs-rss-item-text"> <a class="hs-rss-title"
                    href="http://www.underseaband.com/blog/using-two-amps"><span>Using two amps</span></a>
                <div class="hs-rss-byline">by <span class="hs-rss-author">Matthew Vincenty</span> <span
                        class="hs-rss-posted-at">posted at</span> <span class="hs-rss-date">4/17/15 3:58 PM</span>
                </div>
                <div class="hs-rss-description">
                    <p> Sometimes just one amp isn't enough. Using multiple amps together can yield a sound that is more
                        than the sum of it's parts. Both Corey and myself have split our singal to multiple amps.
                        Currently...<a href="http://www.underseaband.com/blog/using-two-amps">Read more</a> </p>
                </div>
            </div>
            <div class="hs-rss-item-image-wrapper"> <img class="hs-rss-featured-image"
                    src="http://www.underseaband.com/hubfs/Blog_Images/E719C0A7-6C2A-41FB-9A59-FA8236DED4A5.jpg?t=1430835551915">
            </div>
        </div>
    </div>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| show_title | Boolean |  Shows or hides RSS feed title. | True | 
| show_date | Boolean | Displays post date. | True | 
| show_author | Boolean | Displays author name. | True | 
| show_detail | Boolean | Display post summary up to number of characters set by limit_to_chars parameter. | True | 
| title | String | Populates a heading above the RSS feed listing. | 
           
           | 
| limit_to_chars | Number | Maximum number of characters to display in summary. | 200 | 
| publish_date_format | String | Format for the publish date. Possible values include 'short', 'medium' and 'long'. Also accepts custom formats including "MMMM d, yyyy 'at' h:mm a". | 'short' | 
| attribution_text | String | The text which attributes an author to a post. | 'by' | 
| click_through_text | String | The text which will be displayed for the click through link at the end of a post summary. | 'Read more' | 
| publish_date_text | String |  The text which indicates when a post was published. | 'posted at' | 
| include_featured_image | Boolean | Displays featured image with post link for HubSpot generated RSS feeds. | False | 
| item_title_tag | String | Specifies HTML tag of each post title. | span | 
| is_external | Boolean | RSS feed is from an external blog. | False | 
| number_of_items | Number | Maximum number of posts to display. | 5 | 
| publish_date_language | String | Specifies the language of the publish date. | en_US | 
| rss_url | String |  The URL where the RSS feed is located. | 
           
           | 
| content_group_id | String | ID for blog when feed source is internal blog. | 
           
           | 
| select_blog | String | Can be used to select an internal HubSpot blog feed. | default | 
| feed_source | String | Set source for RSS feed. When internal, general format is {rss_url='', is_external=False, content_group_id='2502431580'}. When external, general format is {rss_url='http://blog.hubspot.com/marketing/rss.xml', is_external=True}. | 
           
           | 
| tag_id | Number | ID for tag when feed source is internal blog. | 
           
           | 


## Section header
Generates an h1 header and &lt;p&gt; subheader.

#### Example
```jinja2
{% section_header "section_header" %}
{% section_header "my_section_header" subheader='A more subdued subheader', header='A clear and bold header', label='Section Header'  %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_my_section_header" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_section_header" style="" data-hs-cos-general-type="widget" data-hs-cos-type="section_header">
    <div class="page-header section-header">
        <h1>A clear and bold header</h1>
        <p class="secondary-header"><span id="hs_cos_wrapper_subheader" class="section-subheader">A more subdued subheader</span></p>
    </div>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| header | String | Text to display in header. | 'A clear and bold header' | 
| subheader | String | Text to display in subheader. | 'A more subdued subheader' | 


## Simple menu
Simple menus allow you to create basic navigation menus that can be modified at the page level. Unlike regular menu modules, simple menus are not managed from the Advanced Menus screen in Content Settings, but rather from the template and page editors. You can use [block syntax](/docs/building-blocks/modules/syntax-and-parameters) to set up a default menu tree.

#### Example
```jinja2
{% simple_menu "simple_menu" %}
{% simple_menu "my_simple_menu" orientation='horizontal', label='Simple Menu' %}


Block Syntax Example:


{% widget_block simple_menu "block_simple_menu" overrideable=True, orientation='horizontal', label='Simple Menu'  %}
        {% widget_attribute "menu_tree" is_json=True %}[{"contentType": null, "subCategory": null, "pageLinkName": null, "pageLinkId": null, "isPublished": false, "categoryId": null, "linkParams": null, "linkLabel": "Home", "linkTarget": null, "linkUrl": "http://www.hubspot.com", "children": [], "isDeleted": false}, {"contentType": null, "subCategory": null, "pageLinkName": null, "pageLinkId": null, "isPublished": false, "categoryId": null, "linkParams": null, "linkLabel": "About", "linkTarget": null, "linkUrl": "http://www.hubspot.com/internet-marketing-company", "children": [{"contentType": null, "subCategory": null, "pageLinkName": null, "linkUrl": "http://www.hubspot.com/company/management", "isPublished": false, "children": [], "linkParams": null, "linkLabel": "Our Team", "linkTarget": null, "pageLinkId": null, "categoryId": null, "isDeleted": false}], "isDeleted": false}, {"contentType": null, "subCategory": null, "pageLinkName": null, "pageLinkId": null, "isPublished": false, "categoryId": null, "linkParams": null, "linkLabel": "Pricing", "linkTarget": null, "linkUrl": "http://www.hubspot.com/pricing", "children": [], "isDeleted": false}]{% end_widget_attribute %}
{% end_widget_block %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_my_simple_menu" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_simple_menu" style="" data-hs-cos-general-type="widget" data-hs-cos-type="simple_menu">
    <ul></ul>
</span>


<span id="hs_cos_wrapper_block_simple_menu" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_simple_menu"
    style="" data-hs-cos-general-type="widget" data-hs-cos-type="simple_menu">
    <div id="hs_menu_wrapper_module_143093417497114626" class="hs-menu-wrapper active-branch flyouts hs-menu-flow-horizontal" data-sitemap-name="">
        <ul>
            <li class="hs-menu-item hs-menu-depth-1"><a href="//www.hubspot.com" target="_self">Home</a></li>
            <li class="hs-menu-item hs-menu-depth-1 hs-item-has-children"><a href="//www.hubspot.com/internet-marketing-company" target="_self">About</a>
                <ul class="hs-menu-children-wrapper">
                    <li class="hs-menu-item hs-menu-depth-2"><a href="//www.hubspot.com/company/management" target="_self">Our Team</a></li>
                </ul>
            </li>
            <li class="hs-menu-item hs-menu-depth-1"><a href="//www.hubspot.com/pricing" target="_self">Pricing</a></li>
        </ul>
    </div>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| orientation | Enumeration | Defines classes of menu markup to allow to style the orientation of menu items on the page. Possible values include 'horizontal' and 'vertical'. | 'horizontal' | 
| menu_tree | JSON | Menu structure including page link names and target URLs. | [] | 


## Social sharing
Social sharing modules generate social media icons that can be used to share a particular page. This module can be used with [block syntax](/docs/building-blocks/modules/syntax-and-parameters) to customize the icon images and more.

#### Example
```jinja2
{% social_sharing "social_sharing" %}
{% social_sharing "my_social_sharing" use_page_url=True %}

Block Syntax Example:


{% widget_block social_sharing "my_social_sharing" label='Social Sharing', use_page_url=True, overrideable=True  %}
        {% widget_attribute "pinterest" is_json=True %}{"custom_link_format": "", "pinterest_media": "http://cdn1.hubspot.com/hub/158015/305390_10100548508246879_837195_59275782_6882128_n.jpg", "enabled": true, "network": "pinterest", "img_src": "https://static.hubspot.com/final/img/common/icons/social/pinterest-24x24.png"}{% end_widget_attribute %}
        {% widget_attribute "twitter" is_json=True %}{"custom_link_format": "", "enabled": true, "network": "twitter", "img_src": "https://static.hubspot.com/final/img/common/icons/social/twitter-24x24.png"}{% end_widget_attribute %}
        {% widget_attribute "linkedin" is_json=True %}{"custom_link_format": "", "enabled": true, "network": "linkedin", "img_src": "https://static.hubspot.com/final/img/common/icons/social/linkedin-24x24.png"}{% end_widget_attribute %}
        {% widget_attribute "facebook" is_json=True %}{"custom_link_format": "", "enabled": true, "network": "facebook", "img_src": "https://static.hubspot.com/final/img/common/icons/social/facebook-24x24.png"}{% end_widget_attribute %}
        {% widget_attribute "email" is_json=True %}{"custom_link_format": "", "enabled": true, "network": "email", "img_src": "https://static.hubspot.com/final/img/common/icons/social/email-24x24.png"}{% end_widget_attribute %}
{% end_widget_block %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_social_sharing" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_social_sharing" style="" data-hs-cos-general-type="widget" data-hs-cos-type="social_sharing">
    <a href="http://www.facebook.com/share.php?u=http%3A%2F%2Fexample.com%2Fmy-page%3Futm_medium%3Dsocial%26utm_source%3Dfacebook" target="_blank" style="width:24px;border-width:0px;border:0px;">
        <img src="//static.hubspot.com/final/img/common/icons/social/facebook-24x24.png?width=24" class="hs-image-widget hs-image-social-sharing-24" style="max-height:24px;max-width:24px;border-width:0px;border:0px;" width="24" hspace="0" alt="Share on Facebook">
    </a>
    <a href="http://www.linkedin.com/shareArticle?mini=true&url=http%3A%2F%2Fexample.com%2Fmy-page%3Futm_medium%3Dsocial%26utm_source%3Dlinkedin" target="_blank" style="width:24px;border-width:0px;border:0px;">
        <img src="//static.hubspot.com/final/img/common/icons/social/linkedin-24x24.png?width=24" class="hs-image-widget hs-image-social-sharing-24" style="max-height:24px;max-width:24px;border-width:0px;border:0px;" width="24" hspace="0" alt="Share on LinkedIn">
    </a>
    <a href="https://twitter.com/intent/tweet?original_referer=http%3A%2F%2Fexample.com%2Fmy-page%3Futm_medium%3Dsocial%26utm_source%3Dtwitter&url=http%3A%2F%2Fexample.com%2Fmy-page%3Futm_medium%3Dsocial%26utm_source%3Dtwitter&source=tweetbutton&text=" target="_blank" style="width:24px;border-width:0px;border:0px;">
        <img src="//static.hubspot.com/final/img/common/icons/social/twitter-24x24.png?width=24" class="hs-image-widget hs-image-social-sharing-24" style="max-height:24px;max-width:24px;border-width:0px;border:0px;" width="24" hspace="0" alt="Share on Twitter">
    </a>
    <a href="http://pinterest.com/pin/create/button/?url=http%3A%2F%2Fexample.com%2Fmy-page%3Futm_medium%3Dsocial%26utm_source%3Dpinterest&media=http%3A%2F%2Fcdn1.hubspot.com%2Fhub%2F158015%2F305390_10100548508246879_837195_59275782_6882128_n.jpg" target="_blank" style="width:24px;border-width:0px;border:0px;">
        <img src="//static.hubspot.com/final/img/common/icons/social/pinterest-24x24.png?width=24" class="hs-image-widget hs-image-social-sharing-24" style="max-height:24px;max-width:24px;border-width:0px;border:0px;" width="24" hspace="0" alt="Share on Pinterest"></a>
    <a href="mailto:?subject=Check out http%3A%2F%2Fexample.com%2Fmy-page%3Futm_medium%3Dsocial%26utm_source%3Demail &body=Check out http%3A%2F%2Fexample.com%2Fmy-page%3Futm_medium%3Dsocial%26utm_source%3Demail" target="_blank" style="width:24px;border-width:0px;border:0px;">
        <img src="//static.hubspot.com/final/img/common/icons/social/email-24x24.png?width=24" class="hs-image-widget hs-image-social-sharing-24" style="max-height:24px;max-width:24px;border-width:0px;border:0px;" width="24" hspace="0" alt="Share on Email">
    </a>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| use_page_url | Boolean | If true, the module shares the URL of the page by default. | True | 
| link | String | Specifies a different URL to share, if use_page_url is false. | 
           
           | 
| pinterest | JSON | Parameters for Pinterest link format and icon image source. | See block syntax example, above | 
| twitter | JSON | Parameters for Twitter link format and icon image source. | See block syntax example, above | 
| linked_in | JSON | Parameters for LinkedIn link format and icon image source. | See block syntax example, above | 
| facebook | JSON | Parameters for Facebook link format and icon image source. | See block syntax example, above | 
| email | JSON | Parameters for email sharing link format and icon image source. | See block syntax example, above | 


## Spacer
A spacer module generates an empty span tag. This tag can be styled to act as a spacer. In drag and drop layouts, the spacer module is wrapped in a container with a class of span1-span12 to determine how much space the module should take up in the twelve column responsive grid.

#### Example
```jinja2
{% space "space" %}
{% space "spacer" label='Horizontal Spacer' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_module_spacer" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_space" style="" data-hs-cos-general-type="widget" data-hs-cos-type="space"></span>
```


## Text
Creates a single line of text. This module can be useful to be mixed into your markup, when used in conjunction with the no\_wrapper=True parameter. For example, if you wanted your end users to be able to define a destination of a predefined anchor, you could populate the href with a text module with **no\_wrapper=True**.

#### Example
```jinja2
{% text "text" %}
{% text "simple_text_field" label="Enter text here", value="This is the default value for this text field" %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_simple_text_field" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_text" style="" data-hs-cos-general-type="widget" data-hs-cos-type="text">This is the default value for this text field</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| value | String | Sets the default text of the single line text field. | 
           
           | 


## Textarea
A textarea is similar to a text module in that it allows users to enter plain text, but it gives them a larger area to work in the content editor. This module does not support HTML. If you want to use directly within a predefined wrapping tag, add the **no\_wrapper=true** parameter.

#### Example
```jinja2
{% textarea "my_textarea" %}
{% textarea "my_textarea" label='Enter plain text block', value='Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean a urna quis lacus vehicula rutrum.', no_wrapper=True %}
```

#### Output
```jinja2
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean a urna quis lacus vehicula rutrum.
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| value | String | Sets the default text of the textarea. | 
           
           | 


## Video Player
Render a Vidyard video player for a File Manager video which is selected "Allow embedding, sharing, and tracking".

#### Example
```jinja2
{% video_player "embed_player" %}
{% video_player "embed_player" overrideable=False, type='scriptV4', hide_playlist=True, viral_sharing=False, embed_button=False, width='600', height='375', player_id='6178121750', style='', conversion_asset='{"type":"FORM","id":"9a77c63f-bee6-4ff8-9202-b0af020ea4b2","position":"POST"}' %}
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| hide_playlist | Boolean | Hide the video playlist. | True | 
| playlist_color | String | A HEX color value for the playlist. | 
           
           | 
| play_button_color | String | A HEX color value for the play and pause buttons. | #2A2A2A | 
| embed_button | Boolean | Display embed button on the player | False | 
| viral_sharing | Boolean | Display the social networks sharing button on the player. | False | 
| width | Number | Width of the embedded video player. | Auto | 
| height | Number | Height of the embedded video player. | Auto | 
| player_id | Number | The player_id of the video to embed. Returned at GET /filemanager/api/v2/files/:file_id in the meta.video_data.hosting_infos dict. | 
           
           | 
| style | String | Additional style for player. | 
           
           | 
| conversion_asset | JSON | Event setting for player. Can render CTA or Form before or after video plays. This parameter takes a JSON object with three parameters: type (FORM or CTA), id (The guid of the type object), position (POST or PRE). | See above example | 


# Filters
## 
Filters affect the ultimate output of your HubL. They can be applied to various HubL statements and expressions to alter the template markup outputted by the server.

The basic syntax of a filter is **|filtername**. The filter is added directly following the statement or the expression, within its delimeters. Some filters have additional parmeters that can be added in parentheses. The basic syntax of a filter with a string, a number, and a boolean parameters is: **|filtername('stringParameter', 10, true)**. Notice that string parameters shoud be written in quotes. Also note that HubL filters have an alias that can be used to serve the same purpose as the primary filter.

The following article contains all of the supported HubL filters.

## abs
Gets the absolute value of a number. You can use this filter to ensure that a number is positive.

#### Example
```jinja2
{% set my_number = -53 %} 
{{ my_number|abs }}
```

#### Output
```jinja2
53
```


## add
Adds a numeric value to another numeric value. This filter functions the same as the [+ operator](/docs/hubl/operators-and-expression-tests#math). The parameter in parentheses is the addend that you are combining with your initial numeric value.

#### Example
```jinja2
{% set my_num = 40 %} 
{{ my_num|add(13) }}
```

#### Output
```jinja2
53
```


## attr
Renders the attribute of a dictionary. This filter is the equivalent of printing a variable that exists within a dictionary, such as content.absolute\_url.
| Parameter | Description | 
|  ------  |  ------  | 
| attribute_name `REQUIRED` | Specifies which attribute to print | 


#### Example
```jinja2
{{ content|attr('absolute_url') }} 
```

#### Output
```jinja2
http://designers.hubspot.com/docs/hubl/hubl-filters
```


## batch
A batch filter groups up items within a sequence.
| Parameter | Description | 
|  ------  |  ------  | 
| linecount `Required` | The number of items to include in the batch | 
| fill_with `Optional` | Specifies what to include in order to fill up any missing items | 

In the example below, there is variable containing a sequence of types of fruits. The batch filter is applied to a loop that iterates through the sequence. The nested loop runs three times to print 3 types of fruit per row, before the outer loop runs again. Notice in the final output that since there are only 5 types of fruit, the final item is replaced by a &amp;nbsp (the second parameter).

#### Example
```jinja2
{% set rows = ['apples', 'oranges', 'pears', 'grapes', 'blueberries'] %}

<table>
{% for row in rows|batch(3, '&nbsp;') %}
   <tr>
    {% for column in row %}
        <td>{{ column }}</td>
    {% endfor %}
    </tr> 
{% endfor %}
</table>
```

#### Output
```jinja2
<table>
<tbody>
    <tr>
        <td>apples</td>
        <td>oranges</td>
        <td>pears</td>
   </tr> 
   <tr>
        <td>grapes</td>
        <td>blueberries</td>
        <td>&nbsp;</td>
    </tr> 
</tbody>
</table>
```


## between_times
Calculates the time between two datetime objects in a specified time unit.
| Parameter | Description | 
|  ------  |  ------  | 
| end `Required` | The ending datetime object | 
| timeunit `Required` | Valid time units are nanos , micros , millis , seconds , minutes , hours , half_days , days , weeks , months , years , decades , centuries , millennia , and eras . | 


#### Example
```jinja2
{% set begin = "2018-07-14T14:31:30+0530"|strtotime("yyyy-MM-dd'T'HH:mm:ssZ") %}
{% set end = "2018-07-20T14:31:30+0530"|strtotime("yyyy-MM-dd'T'HH:mm:ssZ") %}
{{ begin|between_times(end, 'days') }}
```

#### Output
```jinja2
6
```


## bool
Converts a text string value to a boolean.

#### Example
```jinja2
{% if "true"|bool == true %}hello world{% endif %}
```

#### Output
```jinja2
hello world
```


## capitalize
Capitalize the first letter of a variable value. The first character will be uppercase, all others letters will retain their original case.

#### Example
```jinja2
{% set sentence = "the first letter of a sentence should always be capitalized." %} 
{{ sentence|capitalize }}
```

#### Output
```jinja2
The first letter of a sentence should always be capitalized.
```


## center
The center filter uses whitespace to center text within a given field length. This filter is not recommended or particularly useful since HubSpot's HTML compiler will automatically strip out the white space; however, it is included here for the sake of comprehensiveness.
| Parameter | Description | 
|  ------  |  ------  | 
| width `Required` | Specifies the length of whitespace to center the text in. | 

The example below shows a center filter being applied to a variable in a pre tag, so the whitespace isn't stripped out.

#### Example
```jinja2
<pre>
{% set var = "string to center" %}
before{{ var|center(80) }}after
</pre>
```

#### Output
```jinja2
<pre>
before                                string to center                                after
</pre>
```


## convert_rgb
Converts a HEX value to an RGB string. This is useful if you need to convert color variables to RGB to be used with a RGBA CSS declaration. In the example below, the value set by a color module is converted to an RGB value and used in an RGBA CSS declaration.

#### Example
```jinja2
{% set my_color = "#FFFFFF" %}
{{ my_color|convert_rgb }}

{% color "my_color" color="#000000", export_to_template_context=True %}
<div style="background: rgba({{ widget_data.my_color.color|convert_rgb }}, .5)"></div>
```

#### Output
```jinja2
255, 255, 255

<div style="background: rgba(0, 0, 0, .5)"></div>
```


## cut
Removes a string from a value. This filter can be used to match and cut out a specific part of a string. The parameter specifies the part of the string that should be removed. The example below removes the space and the word world from the original variable value.
| Parameter | Description | 
|  ------  |  ------  | 
| characters_to_cut `Required` | The part of the string that should be removed. | 


#### Example
```jinja2
{% set my_string = "Hello world." %} 
{{ my_string|cut(' world') }}
```

#### Output
```jinja2
Hello.
```


## datetimeformat
Formats a date object. By default, HubSpot date variables print as timestamps. The datetimeformat filter is used to convert that timestamp into a legible date and/or time. The filter's parameters, listed in the table below, dictate how the time variable ultimately renders.

A null date input to the filter assumes the current date and time.

An optional second parameter can be used to specify a timezone. The timezone must be in a [supported Java 8 format.](https://docs.oracle.com/javase/8/docs/api/java/util/TimeZone.html)
| Parameter | Description | 
|  ------  |  ------  | 
| format `Required` | Directive format for the datetime object. See the directive table under the example for values.  | 
| timezone `Optional` | Specifies a timezone. Must be in a supported Java 8 format. | 


#### Example
```jinja2
{{ content.updated|datetimeformat('%B %e, %Y') }}
{{ content.publish_date|datetimeformat('%B %e, %Y %l %p') }} 
{{ content.publish_date|datetimeformat('%B %e, %Y %l %p', 'America/Los_Angeles') }}
```

#### Output
```jinja2
October 17, 2020
October 1, 2020 4 PM
October 1, 2020 9 AM
```

| Directive | Example | Description | 
|  ------  |  ------  |  ------  | 
| %a | Sun, Mon, ..., Sat (en_US);So, Mo, ..., Sa (de_DE) | Weekday as locale’s abbreviated name. | 
| %A | Sunday, Monday, ..., Saturday (en_US);Sonntag, Montag, ..., Samstag (de_DE) | Weekday as locale’s full name.  | 
| %w | 1, 2, ..., 7 | Weekday as a decimal number, where 1 is Sunday and 7 is Saturday.NOTE: This differs from python day numbers which start at 0. | 
| %d | 01, 02, ..., 31 | Day of the month as a zero-padded decimal number. | 
| %e | 1, 2, ..., 31 | Day of the month as a decimal number, without padding. | 
| %b | Jan, Feb, ..., Dec (en_US);Jan, Feb, ..., Dez (de_DE) | Month as locale’s abbreviated name.  | 
| %B | January, February, ..., December (en_US);Januar, Februar, ..., Dezember (de_DE) | Month as locale’s full name.  | 
| %OB | 1月, 2月, ..., 12月 (ja) | Get the nominative version of the months name. | 
| %m | 01, 02, ..., 12 | Month as a zero-padded decimal number. | 
| %y | 00, 01, ..., 99 | Year without century as a zero-padded decimal number. | 
| %Y | 1970, 1988, 2001, 2013 | Year with century as a decimal number. | 
| %H | 00, 01, ..., 23 | Hour (24-hour clock) as a zero-padded decimal number. | 
| %I | 01, 02, ..., 12 | Hour (12-hour clock) as a zero-padded decimal number. | 
| %k | 0,  1, ..., 24 | The hour (24-hour clock) as a decimal number (range 0 to 23); single digits are preceded by a blank. | 
| %l | 1,  2, ..., 12 | (note this is a lower case L) The hour (12-hour clock) as a decimal number (range 1 to 12); single digits are preceded by a blank. | 
| %p | AM, PM (en_US);am, pm (de_DE) | Locale’s equivalent of either AM or PM.  | 
| %M | 00, 01, ..., 59 | Minute as a zero-padded decimal number. | 
| %S | 00, 01, ..., 59 | Second as a zero-padded decimal number. | 
| %f | 000000, 000001, ..., 999999 | Microsecond as a decimal number, zero-padded on the left. | 
| %z | (empty), +0000, -0400, +1030 | UTC offset in the form +HHMM or -HHMM (empty string if the the object is naive). | 
| %Z | (empty), UTC, EST, CST | Time zone name (empty string if the object is naive). | 
| %j | 001, 002, ..., 366 | Day of the year as a zero-padded decimal number. | 
| %U | 00, 01, ..., 53 | Week number of the year (Sunday as the first day of the week) as a zero padded decimal number. All days in a new year preceding the first Sunday are considered to be in week 0. | 
| %W | 00, 01, ..., 53 | Week number of the year (Monday as the first day of the week) as a decimal number. All days in a new year preceding the first Monday are considered to be in week 0. | 
| %c | Tue Aug 16 21:30:00 1988 (en_US);Di 16 Aug 21:30:00 1988 (de_DE) | Locale’s appropriate date and time representation.  | 
| %x | 08/16/88 (None);08/16/1988 (en_US);16.08.1988 (de_DE) | Locale’s appropriate date representation.  | 
| %X | 21:30:00 (en_US);21:30:00 (de_DE) | Locale’s appropriate time representation.  | 
| %% | % | A literal '%' character. | 


## default
If the value is undefined it will return the first parameter, otherwise the value of the variable will be printed. If you want to use default with variables that evaluate to false, you have to set the second parameter to **true**. The first example below would print the message if the variable is not defined. The second example applied the filter to an empty string, which is not undefined, but it prints a message due to the second parameter.
| Parameter | Description | 
|  ------  |  ------  | 
| default_variable `Required` | Value to return if the variable is undefined. If the variable is defined, the value of the variable will be returned instead. | 
| boolean `Optional` | Returns the default_value if the variable is an empty string | 


#### Example
```jinja2
{{ my_variable|default('my_variable is not defined') }} 
{{ ''|default('the string was empty', true) }}
```

#### Output
```jinja2
my_variable is not defined
the string was empty
```


## dictsort
Sort a dict and yield (key, value) pairs. Dictionaries are unsorted by default, but you can print a dictionary, sorted by key or value. The first parameter is a boolean to determine, whether or not the sorting is case sensitive. The second parameter determines whether to sort the dict by key or value. The example below prints a sorted contact dictionary, with all the known details about the contact.
| Parameter | Description | 
|  ------  |  ------  | 
| case_sensitive `Required` | Determines if sorting is case sensitive | 
| sort_by `Required` | Determines whether to sort by key or value | 


#### Example
```jinja2
{% for item in contact|dictsort(false, 'value') %}
    {{item}}
{% endfor %}
```

#### Output
```jinja2
A sorted contact dictionary
```


## difference
This filter returns the difference of two sets or lists. The list returned from the filter contains all unique elements that are in the first list but not the second.
| Parameter | Description | 
|  ------  |  ------  | 
| list `Required` | The second list to compare to for use in finding differences from the original list. | 


#### Example
```jinja2
{{ [1, 2, 3]|difference([2, 3, 4, 5]) }}
```

#### Output
```jinja2
[1]
```


## divide
Divide the current value by a divisor. The parameter passed is the divisor. This filter is an alternative to the / operator.
| Parameter | Description | 
|  ------  |  ------  | 
| divisor `Required` | The number to divide the variable by. | 


#### Example
```jinja2
{% set numerator = 106 %}
{{ numerator|divide(2) }}
```

#### Output
```jinja2
53
```


## divisible
An alternative to the divisibleby expression test, the filter divisible will evaluate to true if the value is divisible by the given number.
| Parameter | Description | 
|  ------  |  ------  | 
| divisor `Required` | The number to use when evaluating if the value is divisible. | 


#### Example
```jinja2
{% set num = 10 %}
{% if num|divisible(2) %}
The number is divisble by 2
{% endif %}
```

#### Output
```jinja2
The number is divisible by 2
```


## escape
Convert the characters &amp;, &lt;, &gt;, ‘, and ” in string to HTML-safe sequences. Use this if you need to display text that might contain such characters in HTML. Marks return value as markup string.

#### Example
```jinja2
{% set escape_string = "<div>This markup is printed as text</div>" %} 
{{ escape_string|escape }}
```

#### Output
```jinja2
<div>This markup is printed as text</div>
```


## escape_jinjava
Converts the characters { and } in string s to Jinjava-safe sequences. Use this filter if you need to display text that might contain such characters in Jinjava. Marks return value as markup string.

#### Example
```jinja2
{% set escape_string = "{{This markup is printed as text}}" %}
{{ escape_string|escape_jinjava }}
```

#### Output
```jinja2
{{This markup is printed as text}}
```


## escapejs
Escapes strings so that they can be safely inserted into a JavaScript variable declaration.

#### Example
```jinja2
{% set escape_string = "\tThey said 'This string can safely be inserted into JavaScript.'" %}
{{ escape_string|escapejs }}
```

#### Output
```jinja2
They said \'\\tThis string can safely be inserted into JavaScript.\'
```


## escapejson
Escapes strings so that they can be used as JSON values.

#### Example
```jinja2
{% set your_string = '\tTesting a \"quote for the week\"'
{{ your_string|escapejson }}
```

#### Output
```jinja2
\\tTesting a \\\"quote for the week\\\"
```


## filesizeformat
Format the value like a ‘human-readable’ file size (i.e. 13 kB, 4.1 MB, 102 Bytes, etc). Per default decimal prefixes are used (Mega, Giga, etc.), if the parameter is set to True the binary prefixes are used (Mebi, Gibi).
| Parameter | Description | 
|  ------  |  ------  | 
| boolean `Optional` | If set to true, binary prefixes are used such as Mebi & Gibi. | 


#### Example
```jinja2
{% set bytes = 100000 %} 
{{ bytes|filesizeformat }}
```

#### Output
```jinja2
100.0 KB
```


## first
Returns the first item in a sequence.

#### Example
```jinja2
{% set my_sequence = ['Item 1', 'Item 2', 'Item 3'] %} 
{{ my_sequence|first }}
```

#### Output
```jinja2
Item 1
```


## float
Convert the value into a floating point number. If the conversion doesn’t work it will return 0.0. You can override this default using the first parameter.
| Parameter | Description | 
|  ------  |  ------  | 
| default `Optional` | Integer to return if the conversion doesn't work.  | 


#### Example
```jinja2
{% text "my_text" value='25', export_to_template_context=True %} 
{{ widget_data.my_text.value|float + 28 }}
```

#### Output
```jinja2
53.0
```


## forceescape
Strictly enforce HTML escaping. In HubSpot's environment there isn't really a use case for double escaping, so this is generally behaves the same as the escape filter.

#### Example
```jinja2
{% set escape_string = "<div>This markup is printed as text</div>" %} 
{{ escape_string|forceescape }}
```

#### Output
```jinja2
<div>This markup is printed as text</div>
```


## format
Apply Python string formatting to an object. %s can be replaced with another variable.

#### Example
```jinja2
{{ "Hi %s %s"|format(contact.firstname, contact.lastname) }} 
```

#### Output
```jinja2
Hi Brian Halligan
```


## format_currency
Formats a given number as a currency based on portal's default currency and locale passed in as a parameter.
| Parameter | Description | 
|  ------  |  ------  | 
| locale `Optional` | The Java local Language tag. The default is the page's locale.Format : ISO639LanguageCodeInLowercase-ISO3166CountryCodeInUppercase | 


#### Example
```jinja2
{% set price = 100 %}
{{ price|format_currency("en-US") }}
{{ price|format_currency("fr-FR") }}
```

#### Output
```jinja2
$100
100 $
```


## fromjson
Converts a JSON string to an object.

#### Example
```jinja2
{% set obj ='{ "name":"Brian","role":"Owner" }' %}
{{ obj|fromjson }}
```

#### Output
```jinja2
{role=Owner, name=Brian}
```


## geo_distance
Calculates the ellipsoidal 2D distance between two points on Earth.

#### Example
```jinja2
<!-- in the example below the HubDB Location = 42.3667, -71.1060 (Cambridge, MA) | Chicago, IL = 37.3435, -122.0344 -->
{{ row.location | geo_distance(37.3435, -122.0344, "mi") }} MI
```

#### Output
```jinja2
861.1655563461395 MI
```


## groupby
The groupby filter groups a sequence of objects by a common attribute.The parameter sets the common attribute to group by.
| Parameter | Description | 
|  ------  |  ------  | 
| attribute `Required` | The attribute to group by. | 


#### Example
```jinja2
<ul>
{% for group in contents|groupby('blog_post_author') %}
    <li>{{ group.grouper }}
      <ul>
        {% for content in group.list %}
          <li>{{ content.name }}</li>
        {% endfor %}
      </ul>
    </li>
{% endfor %}
</ul>
```

#### Output
```jinja2
<ul>
    <li>Blog author 1
        <ul>
          <li>Post by Blog author 1<li>
          <li>Post by Blog author 1<li>
          <li>Post by Blog author 1<li>
        </ul>
    </li>  
    <li>Blog author 2
        <ul>
          <li>Post by Blog author 2<li>
          <li>Post by Blog author 2<li>
          <li>Post by Blog author 2<li>
        </ul>
    </li>
    <li>Blog author 3
        <ul>
          <li>Post by Blog author 3<li>
          <li>Post by Blog author 3<li>
          <li>Post by Blog author 3<li>
        </ul>
    </li>
</ul>
```


## indent
The indent filter uses whitespace to indent text within a given field length. This filter is not recommended or particularly useful since HubSpot's HTML compiler will automatically strip out the white space; however, it is included here for the sake of comprehensiveness. The example below shows a center filter being applied to a variable in a pre tag, so the whitespace isn't stripped out. The first parameter controls the amount of whitespace and the second boolean toggles whether to indent the first line.
| Parameter | Description | 
|  ------  |  ------  | 
| width `Required` | The amount of whitespace to be applied. | 
| boolean `Required` | A boolean value on whether to indent the first line. | 


#### Example
```jinja2
<pre>
{% set var = "string to indent" %}
{{ var|indent(2, true) }}
</pre>
```

#### Output
```jinja2
  string to indent
```


## int
Convert the value into an integer. If the conversion doesn’t work it will return 0. You can override this default using the first parameter.
| Parameter | Description | 
|  ------  |  ------  | 
| default `Required` | Integer to return if the conversion doesn't work. | 


#### Example
```jinja2
{% text "my_text" value='25', export_to_template_context=True %} 
{{ widget_data.my_text.value|int + 28 }}
```

#### Output
```jinja2
53
```


## intersect
This filter returns the intersection of two sets or lists. The list returned from the filter contains all unique elements that are contained in both lists.
| Parameter | Description | 
|  ------  |  ------  | 
| list `Required` | The second list to compare to for use in finding where the list intersects with the original list. | 


#### Example
```jinja2
{{ [1, 2, 3]|intersect([2, 3, 4, 5]) }}
```

#### Output
```jinja2
[2, 3]
```


## ipaddr
Evaluates to true if the value is a valid IPv4 or IPv6 address.

#### Example
```jinja2
{% set ip = '1.0.0.1' %}
{% if ip|ipaddr %}
    The string is a valid IP address
{% endif %}
```

#### Output
```jinja2
    The string is a valid IP address
```


## join
Return a string which is the concatenation of the strings in the sequence. The separator between elements is an empty string per default, you can define it with the optional parameter. The second parameter can be used to specify an attribute to join.
| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| delimiter `Optional` | String | The delimiter to use when concatenating strings. | 
| attribute `Optional` | HubL Variable | An attribute to use as a delimiter. | 


#### Example
```jinja2
{% set my_list = [1, 2, 3] %}
{% set sep = "---" %}
{{ my_list|join }}
{{ my_list|join('|') }}
{{ my_list|join(sep) }}
```

#### Output
```jinja2
123
1|2|3
1---2---3
```


## last
Returns the last item of a sequence.

#### Example
```jinja2
{% set my_sequence = ['Item 1', 'Item 2', 'Item 3'] %}
{% my_sequence|last %}
```

#### Output
```jinja2
Item 3
```


## length
Return the number of items of a sequence or mapping.

#### Example
```jinja2
{% set services = ['Web design', 'SEO', 'Inbound Marketing', 'PPC'] %} 
{{ services|length }}
```

#### Output
```jinja2
4
```


## list
Convert the number values into a list. If it was a string the returned list will be a list of characters. To add strings to a sequence, simply add them to the string variables to the sequence delimiters \[ \].

#### Example
```jinja2
{% set one = 1 %}
{% set two = 2 %}
{% set three = 3 %}
{% set four = ["four"] %}
{% set list_num = one|list + two|list + three|list + four|list %}
{{ list_num }}
```

#### Output
```jinja2
[1,2,3]
```


## log
Calculates the natural logarithm of a number.
| Parameter | Description | 
|  ------  |  ------  | 
| base `Optional` | Calculate the logarithm at the nth base. | 


#### Example
```jinja2
{{ 10|log }}
{{ 65536|log(2) }}
```

#### Output
```jinja2
2.302585092994046
16.0
```


## lower
Convert a value to all lowercase letters.

#### Example
```jinja2
{{ text "text" value='Text to MAKE Lowercase', export_to_template_context=True }} 
{{ widget_data.text.value|lower }}
```

#### Output
```jinja2
text to make lowercase
```


## map
Applies a filter on a sequence of objects or looks up an attribute. This is useful when dealing with lists of objects but you are really only interested in a certain value of it.

The basic usage is mapping on an attribute. For example, if you want to use conditional logic to check if a value is present in a particular attribute of a dict. Alternatively, you can let it invoke a filter by passing the name of the filter and the arguments afterwards.
| Parameter | Description | 
|  ------  |  ------  | 
| attribute | Attribute to return in the sequence of objects. | 
| filter | Filter to apply to the sequence of objects. | 


#### Example
```jinja2
{% set seq = ['item1', 'item2', 'item3'] %}
{{ seq|map('upper') }}
{{ content|map('currentState')}}
```

#### Output
```jinja2
[ITEM1, ITEM2, ITEM3]
DRAFT
```


## md5
Calculates the [md5 hash](https://en.wikipedia.org/wiki/MD5) of the given object

#### Example
```jinja2
{{ content.absolute_url|md5 }} 
```

#### Output
```jinja2
923adb4ce05a4c6342c04c80be88d15e
```


## minus_time
Subtracts an amount of time to a datetime object.
| Parameter | Description | 
|  ------  |  ------  | 
| diff `Required` | Amount to subtract. | 
| timeunit `Required` | Valid time units are nanos , micros , millis , seconds , minutes , hours , half_days , days , weeks , months , years , decades , centuries , millennia , and eras . | 


#### Example
```jinja2
{% set date = "2018-07-14T14:31:30+0530"|strtotime("yyyy-MM-dd'T'HH:mm:ssZ") %}
{{ date }}
{{ date|minus_time(2, 'months') }}
```

#### Output
```jinja2
2018-07-14 14:31:30
2018-05-14 14:31:30
```


## mulitply
Multiplies a value with a number. Functions the same as the [\* operator](/docs/hubl/operators-and-expression-tests?hsLang=en).

#### Example
```jinja2
{% set n = 20 %} 
{{ n|multiply(3) }}
```

#### Output
```jinja2
60
```


## plus_time
Adds an amount of time to a datetime object.
| Parameter | Description | 
|  ------  |  ------  | 
| diff `Required` | Amount to add. | 
| timeunit `Required` | Valid time units are nanos , micros , millis , seconds , minutes , hours , half_days , days , weeks , months , years , decades , centuries , millennia , and eras . | 


#### Example
```jinja2
{% set date = "2018-07-14T14:31:30+0530"|strtotime("yyyy-MM-dd'T'HH:mm:ssZ") %}
{{ date }}
{{ date|plus_time(5, 'days') }}
```

#### Output
```jinja2
2018-07-14 14:31:30
2018-07-19 14:31:30
```


## pprint
Pretty print a variable. This prints the type of variable and other info that is useful for debugging.

#### Example
```jinja2
{% set this_var ="Variable that I want to debug" %} 
{{ this_var|pprint }}
```

#### Output
```jinja2
(String: Variable that I want to debug)
```


## random
Return a random item from the sequence. The random function does NOT break caching. It is best used for scenarios where you are okay with the random item is selected when the server-side cache refreshes, not on page load. If you do need to return a random item every page load you should use javascript.

#### Example
```jinja2
{% for content in contents|random %}
<div class="post-item">Post item markup</div>
{% endfor %}
```

#### Output
```jinja2
<div class="post-item">Random post</div>
```


## regex_replace
Searches for a regex pattern and replaces with a sequence of characters. The first argument is a RE2-style regex pattern, the second is the replacement string.

Information on the RE2 regex syntax can be found [here](https://github.com/google/re2/wiki/Syntax).

#### Example
```jinja2
{{ "contact-us-2"|regex_replace("[^a-zA-Z]", "") }} 
```

#### Output
```jinja2
contactus
```


## reject
Filters a sequence of objects by applying an [expression test](/docs/hubl/operators-and-expression-tests?hsLang=en) to the object and rejecting the ones with the test succeeding.
| Parameter | Description | 
|  ------  |  ------  | 
| exp_text | The expression test to apply to the object. | 


#### Example
```jinja2
{% set some_numbers = [10, 12, 13, 3, 5, 17, 22] %} 
{{ some_numbers|reject('even') }}
```

#### Output
```jinja2
[13, 3, 5, 17]
```


## rejectattr
Filters a sequence of objects by applying a test to an attribute of an object and rejecting the ones with the test succeeding.
| Parameter | Description | 
|  ------  |  ------  | 
| attribute_name `Required` | Specifies the attribute to select. You can access nested attributes using dot notation. | 
| exp_test `Optional` | The expression to test | 
| val `Optional` | Value to test against. | 


#### Example
```jinja2
{% for content in contents|rejectattr('post_list_summary_featured_image') %}
<div class="post-item">
{% if content.post_list_summary_featured_image %}
    <div class="hs-featured-image-wrapper">
            <a href="{{content.absolute_url}}" title="" class="hs-featured-image-link">
            <img src="{{ content.post_list_summary_featured_image }}" class="hs-featured-image">
            </a>
    </div>
{% endif %}
{{ content.post_list_content|safe }}
</div>
{% endfor %}
```

#### Output
```jinja2
<div class="post-item">Post with no featured image</div>
<div class="post-item">Post with no featured image</div>
<div class="post-item">Post with no featured image</div>
```


## replace
Replace all instances of a substring with a new one.
| Parameter | Description | 
|  ------  |  ------  | 
| old `Required` | The substring that should be replaced. | 
| new `Required` | Replacement string. | 
| count `Optional` | If provided, only the firstcount occurrences are replaced. | 


#### Example
```jinja2
{% if topic %}
<h3>Posts about {{ page_meta.html_title|replace('Blog | ', '') }}</h3>
{% endif %}

```

#### Output
```jinja2
<h3>Posts about topic name</h3>
```


## reverse
Reverse the object or return an iterator the iterates over it the other way round. To reverse a list use [.reverse()](/docs/hubl/functions#reverse)

#### Example
```jinja2
{% set nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10] %}
{% for num in nums|reverse %}
{{ num }}
{% endfor %}
```

#### Output
```jinja2
10 9 8 7 6 5 4 3 2 1
```


## root
Calculates the square root of a value.
| Parameter | Description | 
|  ------  |  ------  | 
| nth_root `Optional` | Calculate the nth root of a number. | 


#### Example
```jinja2
{{ 16|root }}
{{ 625|root(4) }}
```

#### Output
```jinja2
4
5
```


## round
Round the number to a given precision.
| Parameter | Description | 
|  ------  |  ------  | 
| precision `Optional` | Specifies the precision of the rounding. | 
| rounding_method `Optional` | Options include common round either up or down (default); ceil always rounds up; floor always rounds down.
If you don’t specify a method common is used. | 


#### Example
```jinja2
{{ 52.5|round }} 
{{ 52.5|round(0, 'floor') }}
```

#### Output
```jinja2
53
52
```


## safe
Mark the value as safe which means that in an environment with automatic escaping enabled this variable will not be escaped.

#### Example
```jinja2
{{ content.post_list_content|safe }} 
```

#### Output
```jinja2
<p>HTML post content that is not escaped. </p>
```


## select
Filters a sequence of objects by applying a test to the object and only selecting the ones with the test succeeding.
| Parameter | Description | 
|  ------  |  ------  | 
| exp_text | The expression test to apply to the object. | 


#### Example
```jinja2
{% set some_numbers = [10, 12, 13, 3, 5, 17, 22] %} 
{{ some_numbers|select('even') }}
```

#### Output
```jinja2
[10, 12, 22] 
```


## selectattr
Filters a sequence of objects by applying a test to an attribute of an object and only selecting the ones with the test succeeding.
| Parameter | Description | 
|  ------  |  ------  | 
| attribute_name `Required` | Specifies the attribute to select. You can access nested attributes using dot notation. | 
| exp_test `Optional` | The expression to test | 
| val `Optional` | Value to test against. | 


#### Example
```jinja2
{% for content in contents|selectattr('post_list_summary_featured_image') %}
<div class="post-item">
  {% if content.post_list_summary_featured_image %}
    <div class="hs-featured-image-wrapper">
       <a href="{{content.absolute_url}}" title="" class="hs-featured-image-link">
         <img src="{{ content.post_list_summary_featured_image }}" class="hs-featured-image">
       </a>
    </div>
  {% endif %}
{{ content.post_list_content|safe }}
</div>
{% endfor %}
```

#### Output
```jinja2
<div class="post-item">
  <div class="hs-featured-image-wrapper">
     <a href="http://blog.hubspot.com/marketing/how-to-get-a-job" title="" class="hs-featured-image-link">
       <img src="//cdn2.hubspot.net/hub/53/hubfs/00-Blog-Related_Images/landing-a-job-featured-image.png?t=1431452322770&width=761" class="hs-featured-image">
     </a>
   </div>
Post with featured image
</div>
```


## shuffle
Randomizes the order of iteration through a sequence. The example below shuffles a standard blog loop.

#### Example
```jinja2
{% for content in contents|shuffle %}
<div class="post-item">Markup of each post</div>
{% endfor %}
```

#### Output
```jinja2
<div class="post-item">Markup of each post 5</div>
<div class="post-item">Markup of each post 3</div>
<div class="post-item">Markup of each post 1</div>
<div class="post-item">Markup of each post 2</div>
<div class="post-item">Markup of each post 4</div>
```


## slice
Slice an iterator and return a list of lists containing those items. The first parameter specifies how many items will be sliced, and the second parameter specifies characters to fill in empty slices.
| Parameter | Description | 
|  ------  |  ------  | 
| slices `Required` | How many items will be sliced. | 
| filler `Required` | Specifies characters to fill in empty slices.  | 


#### Example
```jinja2
{% set items = ['laptops', 'tablets', 'smartphones', 'smart watches', 'TVs'] %}
<div class="columwrapper">
  {% for column in items|slice(3,' ') %}
    <ul class="column-{{ loop.index }}">
    {% for item in column %}
      <li>{{ item }}</li>
    {% endfor %}
    </ul>
  {% endfor %}
</div>
```

#### Output
```jinja2
<div class="columwrapper">
    <ul class="column-1">
      <li>laptops</li>
      <li>tablets</li>
      <li>smartphones</li>
    </ul>
  
    <ul class="column-2">
      <li>smart watches</li>  
      <li>TVs</li>
      <li>&nbsp;</li>
    </ul>
</div>
```


## sort
Sorts an iterable. This filter requires all parameters to sort by an attribute in HubSpot. The first parameter is a boolean to reverse the sort order. The second parameter determines whether or not the sorting is case sensitive. And the final parameter specifies an attribute to sort by. In the example below, posts from a blog are rendered and alphabetized by name.
| Parameter | Description | 
|  ------  |  ------  | 
| reverse `Required` | Boolean value to reverse the sort order. | 
| case_sensitive `Required` | Boolean value that determines if the sorting is case sensitive.  | 
| attribute `Required` | Attribute to sort by. | 


#### Example
```jinja2
{% set my_posts = blog_recent_posts('default', limit=5) %}

{% for item in my_posts|sort(False, False, 'name') %}
{{ item.name }}<br>


{% endfor %}
```

#### Output
```jinja2
A post<br>
B post<br>
C post<br>
D post<br>
E post<br>
```


## split
Splits the input string into a list on the given separator. The first parameter specifies the separator to split the variable by. The second parameter determines how many times the variable should be split. Any remaining items would remained group. In the example below, a string of names is split at the ";" for the first 4 names.
| Parameter | Description | 
|  ------  |  ------  | 
| character_to_split_by `Required` | Specifies the separator to split the variable by. | 
| number_of_splits `Required` | Determines how many times the variable should be split. Any remaining items would remain grouped. | 


#### Example
```jinja2
{% set string_to_split = "Stephen; David; Cait; Nancy; Mike; Joe; Niall; Tim; Amanda" %}
{% set names = string_to_split|split(';', 4) %}
<ul>
{% for name in names %}
  <li>{{ name }}</li>
{% endfor %}
</ul>
```

#### Output
```jinja2
<ul>
  <li>Stephen</li>
  <li>David</li>
  <li>Cait</li>
  <li>Nancy; Mike; Joe; Niall; Tim; Amanda</li>
</ul>
```


## string
Converts a different variable type to a string. In the example below, a integer is converted into a string (pprint is used to confirm the change in variable type).

#### Example
```jinja2
{% set number_to_string = 45 %} 
{{ number_to_string|string|pprint }}
```

#### Output
```jinja2
(String: 45) 
```


## striptags
Strip SGML/XML tags and replace adjacent whitespace by one space. This filter can be used to remove any HTML tags from a variable.

#### Example
```jinja2
{% set some_html = "<div><strong>Some text</strong></div>" %} 
{{ some_html|striptags }}
```

#### Output
```jinja2
  some text  
```


## strtotime
Converts a datetime string and a datetime format into a datetime object.
| Parameter | Description | 
|  ------  |  ------  | 
| datetimeFormat `Required` | Date and time patterns. | 


#### Example
```jinja2
{{ "2018-07-14T14:31:30+0530"|strtotime("yyyy-MM-dd'T'HH:mm:ssZ")|unixtimestamp }}

```

#### Output
```jinja2
1531558890000
```


## sum
Adds numeric values in a sequence. The first parameter can specify an optional attribute and the second parameter sets a value to return if there is nothing in the variable to sum.
| Parameter | Description | 
|  ------  |  ------  | 
| attribute `Optional` | Attribute to sum. | 
| return_if_nothing `Optional` | Value to return if there is nothing in the variable to sum. | 


#### Example
```jinja2
{% set sum_this = [1, 2, 3, 4, 5] %}
{{ sum_this|sum }}
Total: {{ items|sum(attribute='price') }}
```

#### Output
```jinja2
15
Total: 20
```


## symmetric_difference
This filter returns the symmetric difference of two sets or lists. The list returned from the filter contains all unique elements that are in the first list but not the second, or are in the second list but not the first
| Parameter | Description | 
|  ------  |  ------  | 
| list `Required` | The second list to compare to for use in finding the symmetric difference with the original list. | 


#### Example
```jinja2
{{ [1, 2, 3]|symmetric_difference([2, 3, 4, 5]) }}
```

#### Output
```jinja2
[1, 4, 5]
```


## title
Return a titlecased version of the value. I.e. words will start with uppercase letters, all remaining characters are lowercase.

#### Example
```jinja2
{% text "my_title" label='Enter a title', value='My title should be titlecase', export_to_template_context=True %} 
{{ widget_data.my_title.value|title }}
```

#### Output
```jinja2
My Title Should Be Titlecase
```


## tojson
Writes an object as a JSON string.

#### Example
```jinja2
{% for content in contents %}
  {{ content.blog_post_author|tojson }}
{% endfor %}
```


## trim
Strips leading and trailing whitespace. HubSpot already trims whitespace from markup, but this filter is documented for the sake of comprehensiveness.

#### Example
```jinja2
{{ " remove whitespace " }} 
{{ " remove whitespace "|trim }}
```

#### Output
```jinja2
 remove whitespace 
remove whitespace
```


## truncate
Cuts off text after a certain number of characters. The default is 255. Please note that HTML characters are included in this count. The length is specified with the first parameter which defaults to 255. If the second parameter is true the filter will cut the text at length. Otherwise it will discard the last word. If the text was in fact truncated it will append an ellipsis sign ("..."). If you want a different ellipsis sign than "..." you can specify it using the third parameter.
| Parameter | Description | 
|  ------  |  ------  | 
| number_of_characters `Required` | Number of characters to truncate the text by. Default is 255. | 
| breakword `Optional` | Boolean value. If true, the filter will cut the text at length. If false, it will discard the last wrod.  | 
| end `Optional` | Override the default '...' trailing characters after the truncation. | 


#### Example
```jinja2
{{ "I only want to show the first sentence. Not the second."|truncate(40) }} 
{{ "I only want to show the first sentence. Not the second."|truncate(35, True, '..........') }}
```

#### Output
```jinja2
I only want to show the first sentence.
I only want to show the first sente.......... 
```


## truncatehtml
Truncates a given string, respecting html markup (i.e. will properly close all nested tags). This will prevent a tag from being remaining open after truncation. HTML characters do not count towards the character total. This filter has a length parameter and a truncation symbol parameter. There is a third boolean parameter that specifies whether words will be broken at length. This parameter is false by default in order to preserve the length of words.
| Parameter | Description | 
|  ------  |  ------  | 
| number_of_characters `Required` | Number of characters to truncate the text by. Default is 255. | 
| end `Optional` | Override the default '...' trailing characters after the truncation. | 
| breakword `Optional` | Boolean value. If true, the filter will cut the text at length. If false, it will discard the last wrod.  | 


#### Example
```jinja2
{% set html_text = "<p>I want to truncate this text without breaking my HTML<p>" %} 
{{ html_text|truncatehtml(28, '..' , false) }}
```

#### Output
```jinja2
<p>I want to truncate this..</p>
```


## union
This filter returns the union of two sets or lists. The list returned from the filter contains all unique elements that are in either list.
| Parameter | Description | 
|  ------  |  ------  | 
| list `Required` | The second list to union with the original list. | 


#### Example
```jinja2
{{ [1, 2, 3]|union([2, 3, 4, 5]) }}
```

#### Output
```jinja2
[1, 2, 3, 4, 5]
```


## unique
This filter extracts a unique set from a sequence or dict of objects. When filtering a dict, such as a list of posts returned by a function, you can specify the which attribute should be used to deduplicate items in the dict.
| Parameter | Description | 
|  ------  |  ------  | 
| attr `Optional` | Specifies the attribute that should be used when filtering a dict value | 


#### Example
```jinja2
{% set my_sequence = ['one', 'one', 'two', 'three' ] %} 
{{ my_sequence|unique }}
```

#### Output
```jinja2
[one, two, three]
```


## unixtimestamp
This filter converts a datetime object into a unix timestamp.

#### Example
```jinja2
{{ local_dt }} 
{{ local_dt|unixtimestamp }}
```

#### Output
```jinja2
2017-01-30 17:11:44
1485814304000
```


## upper
Convert a value to all uppercase letters.

#### Example
```jinja2
{% text "text" value='text to make uppercase', export_to_template_context=True %} 
{{ widget_data.text.value|upper }}
```

#### Output
```jinja2
TEXT TO MAKE UPPERCASE
```


## urlencode
Escapes a url encodes a string using UTF-8 formatting.

#### Example
```jinja2
{% text "encode" value="Escape & URL encode this string", label="Enter slug", export_to_template_context=True %} 
{{ widget_data.encode.value|urlencode }}
```

#### Output
```jinja2
Escape+%26+URL+encode+this+string 
```


## urlize
Converts URLs in plain text into clickable links. If you pass the filter an additional integer it will shorten the urls to that number. The second parameter is a boolean that dictates whether the link is rel="no follow". The final parameter lets you specify whether the link will open in a new tab.
| Parameter | Description | 
|  ------  |  ------  | 
| shorten_text `Optional` | Integer that will shorten the urls to desired number. | 
| no_follow `Optional` | Boolean value to indicate whether the link is rel="no follow". | 
| target='_blank' `Optional` | Specifies whether the link will open in a new tab. | 


#### Example
```jinja2
{{ "http://hubspot.com/"|urlize }}
{{ "http://hubspot.com/"|urlize(10,true) }}
{{ "http://hubspot.com/"|urlize('',true) }}
{{ "http://hubspot.com/"|urlize('',false,target='_blank') }}
```

#### Output
```jinja2
<a href="//hubspot.com/">http://hubspot.com/</a>
<a href="//hubspot.com/" rel="nofollow">http://...</a>
<a href="//hubspot.com/" rel="nofollow">http://hubspot.com/</a>
<a href="//hubspot.com/" target="_blank">http://hubspot.com/</a>
```


## wordcount
Count the number of words in a string.

#### Example
```jinja2
{%  set count_words = "Count the number of words in this variable"  %} 
{{ count_words|wordcount }}
```

#### Output
```jinja2
8
```


## wordwrap
Causes words to wrap at a given character count. This works best in a &lt;pre&gt; because HubSpot strips whitespace by default.
| Parameter | Description | 
|  ------  |  ------  | 
| character_count `Required` | Number of characters to wrap the content at. | 


#### Example
```jinja2
{% set wrap_text = "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam efficitur, ipsum non sagittis euismod, ex risus rhoncus lectus, vel maximus leo enim sit amet dui. Ut laoreet ultricies quam at fermentum." %} 
{{ wrap_text|wordwrap(10) }}
```

#### Output
```jinja2
Lorem
ipsum
dolor sit
amet,
consectetur
adipiscing
elit.
Etiam
efficitur,
ipsum non
sagittis
euismod,
ex risus
rhoncus
lectus,
vel
maximus
leo enim
sit amet
dui. Ut
laoreet
ultricies
quam at
fermentum.
```


## xmlattr
Create an HTML/XML attribute string, based on the items in a dict. All values that are neither none   
nor undefined are automatically escaped. It automatically prepends a space in front of the item if the filter returned something unless the first parameter is false.
| Parameter | Description | 
|  ------  |  ------  | 
| autospace `Required` | Boolean value that will automatically prepend a space in front of the item unless set to false. | 


#### Example
```jinja2
{% set html_attributes = {'class': 'bold', 'id': 'sidebar'} %}
<div {{ html_attributes|xmlattr }}></div>
```

#### Output
```jinja2
<div class="bold" id="sidebar"></div>
```


# Operators and Expression Tests
## 
In order to expand the logic and functionality of your templates, HubL supports several key operators and expression tests. The [operators](https://designers.hubspot.com/docs/hubl/operators-and-expression-tests#operators) allow you to execute math functions, make comparisons, complicate template logic, and alter what markup renders. In addition, this article contains a comprehensive list of [expression tests](https://designers.hubspot.com/docs/hubl/operators-and-expression-tests#expression-tests) that can be used in HubL.

## Operators
| Symbol | Description | 
|  ------  |  ------  | 
| + | Adds two objects together. You will generally use this for the addition of numbers. If you are trying to concatenate strings of lists, you should use ~ instead. | 
| - | Subtracts one number from another. | 
| / | Divides numbers | 
| % | Returns the remainder from dividing numbers | 
| // | Divide two numbers and return the truncated integer result. Example: {{ 20 // 7 }} is 2 | 
| * | Multiplies numbers | 
| ** | Raise the left operand to the power of the right operand | 


#### Example
```jinja2
{% set my_num = 11 %}
{% set my_number = 2 %}
    
{{ my_num + my_number }}<br/>  <!-- 11 + 2 = 13 -->
{{ my_num - my_number }}<br/>  <!-- 11 - 2 = 9 -->
{{ my_num / my_number }}<br/>  <!-- 11 / 2 = 5.5 -->
{{ my_num % my_number }}<br/>  <!-- 11 % 2 = 1 -->
{{ my_num // my_number }}<br/> <!-- 11 // 2 = 5 -->
{{ my_num * my_number }}<br/>  <!-- 11 * 2 = 22 -->
{{ my_num ** my_number }}<br/> <!-- 11 ** 2 = 121 -->
```

#### Output
```jinja2
13
9
5.5
1
5
22
121
```

| Symbol | Description | 
|  ------  |  ------  | 
| == | Equal to. Evaluates to true if two objects are equal.  | 
| != | Not equal to. Evaluates to true if two objects are not equal. | 
| > | Greater than. Evaluates to true if the left-hand side is greater than the right-hand side. | 
| >= | Greater than or equal to. Evaluates to true if the left-hand side is greater or equal to the right-hand side. | 
| < | Less than. Evaluates to true if the left-hand side is lower than the right-hand side. | 
| <= | Less than or equal to. Evaluates to true if the left-hand side is lower or equal to the right-hand side. | 


#### Example
```jinja2
{% set my_num = 11 %}
{% set my_number = 2 %}

{{ my_num == my_number }}<br/>  <!-- false -->
{{ my_num != my_number }}<br/>  <!-- true -->
{{ my_num > my_number }}<br/>   <!-- true -->
{{ my_num >= my_number }}<br/>  <!-- true -->
{{ my_num < my_number }}<br/>   <!-- false -->
{{ my_num <= my_number }}<br/>  <!-- false -->
```

#### Output
```jinja2
false
true
true
true
false
false
```

Logical operators allow you to combine multiple expressions into single statements.
| Symbol | Description | 
|  ------  |  ------  | 
| and | Return true if the left and the right operand are true. | 
| or | Return true if the left or the right operand is true. | 
| not | Negates a statement and is used in conjunction with is. See examples below. | 
| (expr) | Group an expression for the order of operations. For example, (10 - 2) * variable. | 
| ?: | The ternary operator accepts 3 arguments (expression, true condition, false condition). Evaluates an expression and returns the corresponding condition. | 

Below are other important HubL operators that can be used to perform various tasks.
| Symbol | Description | 
|  ------  |  ------  | 
| in | Checks to see if a value is in a sequence. | 
| is | Performs an expression test. | 
| | | Applies a filter. | 
| ~ | Concatenates values. | 


## Expression tests
Expression tests are various boolean conditions that can be evaluated by using logical operators.
The `containing` expression test checks to see whether a list variable has a value in it.

#### Example
```jinja2
{% set numbers = [1, 2, 3] %}

{% if numbers is containing 2 %}
	Set contains 2!
{% endif %}
```

#### Output
```jinja2
Set contains 2!
```

The `containingall` expression test checks if a list variable contains all of the values of another list.

#### Example
```jinja2
{% set numbers = [1, 2, 3] %}

{% if numbers is containingall [2, 3] %}
	Set contains 2 and 3!
{% endif %}

{% if numbers is containingall [2, 4] %}
	Set contains 2 and 4!
{% endif %}
```

#### Output
```jinja2
Set contains 2 and 3!
```

The **defined** expression test checks to see whether a variable is defined within the context of the template. While you can use this expression test, writing an if statement without any operators will default to checking whether or not the variable is defined.

In the example below, a color module's color parameter is tested. If the color parameter had no value, the template would render a default black background color. If it is defined, it renders the background color set by the user.

#### Example
```jinja2
{% color "my_color" color='#930101', export_to_template_context=True %}
<style>
{% if widget_data.my_color.color is defined %}
body{
    background: {{ widget_data.my_color.color }};
}
{% else %}
body{
    background: #000;
}
{% endif %}
</style>
```

#### Output
```jinja2
<style>
 
body{
    background: #930101;
}
 
</style> 
```

The expression test **divisibleby** can be used to test whether an object is divisible by another number.

For example, below a for loop is created that iterates through a list of types of animals. Each type of animal gets printed in a div, and every 5th div has different inline styling applied (width:100%). This concept could be applied to a blog where different markup is rendered for a certain pattern of posts. To learn more about for loops and loop.index, [check out this article](https://designers.hubspot.com/docs/hubl/for-loops?hsLang=en).

#### Example
```jinja2
{% set animals = ['lions', 'tigers', 'bears', 'dogs', 'sharks'] %} 
{% for animal in animals %} 
    {% if loop.index is divisibleby 5 %}
    <div style="width:100%">{{animal}}</div> 
    {% else %}
    <div style="width:25%">{{animal}}</div>
    {% endif %}
{% endfor %}
```

#### Output
```jinja2
<div style="width:25%">lions</div> 
<div style="width:25%">tigers</div> 
<div style="width:25%">bears</div> 
<div style="width:25%">dogs</div> 
<div style="width:100%">sharks</div> 
```

The **equalto** expression test checks to see if a variable's value is equal to a constant or another variable. You can also use the operator == to do the same test.

In the example below, the width of the blog posts is adjusted based on the total number of posts in the loop. The example output assumes there were 4 posts in the blog.

#### Example
```jinja2
{% for content in contents %}
    {% if loop.length is equalto 2 %}
        <div style="width:50%;">Post content</div>
    {% elif loop.length is equalto 3 %}  
        <div style="width:33.333332%;">Post content</div>
    {% elif loop.length is equalto 4 %}  
        <div style="width:25%;">Post content</div>    
    {% else %}
        <div style="width:100%;>Post content</div>
    {% endif %}
{% endfor %}
```

#### Output
```jinja2
<div style="width:25%;">Post content</div>
<div style="width:25%;">Post content</div>
<div style="width:25%;">Post content</div>
<div style="width:25%;">Post content</div>
```

The **even** expression test checks to see whether a numeric variable is an even number.

The example below shows a simplified blog listing loop, where if the current iteration of the loop is even, a class of even-post is assigned to the post item div. Otherwise, a class of odd-post is assigned.

#### Example
```jinja2
{% for content in contents %}
   {% if loop.index is even %}
        <div class="post-item even-post">Post content</div>
    {% else %}
        <div class="post-item odd-post">Post content</div>
    {% endif %}
{% endfor %} 
```

#### Output
```jinja2
<div class="post-item odd-post">Post content</div>
<div class="post-item even-post">Post content</div>
<div class="post-item odd-post">Post content</div>
<div class="post-item even-post">Post content</div>
```

Checks to see whether a variable is **iterable** and can be looped through.

This example checks a variable called "jobs" to see if it can be iterated through. Since the variable contains a list of jobs, the if statement would evaluate to true, and the loop would run. If the variable had contained a single value, the [if statement](http://developers-web1-hubspot.sites.hubspot.com/docs/hubl/if-statements?hsLang=en) would print that value with different markup instead. [You can learn more about for loops here](https://designers.hubspot.com/docs/hubl/for-loops?hsLang=en).

#### Example
```jinja2
{% set jobs = ['Accountant', 'Developer', 'Manager', 'Marketing', 'Support'] %} 

{% if jobs is iterable %}
<h3>Available positions</h3>
<ul>
{% for job in jobs %}
    <li>{{ job }}</li>
{% endfor %}
</ul>
{% else %}
<h3>Available position</h3>
<div class="single-position">{{ jobs }}</div>
{% endif %}
```

#### Output
```jinja2
<h3>Available positions</h3>
<ul>
    <li>Accountant</li>
    <li>Developer</li>
    <li>Manager</li>
    <li>Marketing</li>
    <li>Support</li>
</ul>
```

The **lower** expression test evaluates to true when a string is lowercase.

The example below uses an [unless statement](http://developers-web1-hubspot.sites.hubspot.com/docs/hubl/if-statements?hsLang=en#unless-statements) and a lower filter to ensure that a string of text entered into a text module is always lowercase.

#### Example
```jinja2
{% module "my_text" path="@hubspot/text" label='Enter text', value='Some TEXT that should be Lowercase', export_to_template_context=True %}

{% unless widget_data.my_text.value is lower %}
{{ widget_data.my_text.value|lower }}
{% endunless %}
```

#### Output
```jinja2
some text that should be lowercase
```

The **mapping** expression test checks to see whether or not an object is a dict (dictionary).

The example below is checking to see if the contact object is a dictionary, in which case it is.

#### Example
```jinja2
{% if contact is mapping %}
This object is a dictionary.
{% else %}
This object is not a dictionary.
{% endif %}
```

#### Output
```jinja2
This object is a dictionary.
```

The **none** expression test checks to see whether a variable has a null value.

#### Example
```jinja2
{% module "user_email" path="@hubspot/text" label='Enter user email', value='example@hubspot.com', export_to_template_context=True %}
{% unless widget_data.user_email.value is none %}
{{ widget_data.user_email.value }}
{% endunless %}
```

#### Output
```jinja2
example@hubspot.com
```

The **number** expression test checks to see whether or not the value of a variable is a number.

The example below checks a variable to see whether or not it is a variable, and if so it converts it into millions.

#### Example
```jinja2
{% set my_var = 40 %}
{% if my_var is number %}
{{ my_var * 1000000 }}
{% else %}
my_var is not a number.
{% endif %}
```

#### Output
```jinja2
40000000
```

The **odd** expression test checks to see whether a numeric variable is an odd number.

Below is the same example as the inverse even expression test previously described.

#### Example
```jinja2
{% for content in contents %}
   {% if loop.index is odd %}
        <div class="post-item odd-post">Post content</div>
    {% else %}
        <div class="post-item even-post">Post content</div>
    {% endif %}
{% endfor %} 
```

#### Output
```jinja2
<div class="post-item odd-post">Post content</div>
<div class="post-item even-post">Post content</div>
<div class="post-item odd-post">Post content</div>
<div class="post-item even-post">Post content</div>
```

The **sameas** expression test checks to see whether or not two variables have the same value.

The example below sets two variables and then checks to see whether or not they are the same.

#### Example
```jinja2
{% set var_one = True %}
{% set var_two = True %}
{% if var_one is sameas var_two  %}
The variables values are the same.
{% else %}
The variables values are different.
{% endif %}
```

#### Output
```jinja2
The variables values are the same.
```

The **sequence** expression test is similar to the **iterable** test, in that it checks to see whether or not a variable is a sequence.

The example below checks whether a variable is a sequence and then iterates through that sequence of musical genres.

#### Example
```jinja2
{% set genres = ['Pop', 'Rock', 'Disco', 'Funk', 'Folk', 'Metal', 'Jazz', 'Country', 'Hip-Hop', 'Classical', 'Soul', 'Electronica' ] %} 
{% if genres is sequence %}
<h3>Favorite genres</h3>
<ul>
{% for genre in genres %}
    <li>{{ genre }}</li>
{% endfor %}
</ul>
{% else %}
<h3>Favorite genre:</h3>
    <div class='single-genre'>{{ genres }}</div>
{% endif %}
```

#### Output
```jinja2
<ul>
    <li>Pop</li>
    <li>Rock</li>
    <li>Disco</li>
    <li>Funk</li>
    <li>Folk</li>
    <li>Metal</li>
    <li>Jazz</li>
    <li>Country</li>
    <li>Hip-Hop</li>
    <li>Classical</li>
    <li>Soul</li>
    <li>Electronica</li>
</ul>
```

The **string** expression test checks to see whether the value stored in a variable is text.

The example below checks whether or not a variable is a string, and if so it applies a title filter to change the capitalization.

#### Example
```jinja2
{% set my_var = "title of section" %}
{% if my_var is string %}
{{ my_var|title }}
{% else %}
my_var is not a string
{% endif %}
```

#### Output
```jinja2
Title Of Section
```

This test checks to see if a string is contained within another string. This expression test is used in conjunction with the "is" operator.

#### Example
```jinja2
{% if content.domain is string_containing ".es" %}
Markup that will only render on content hosted on .es domains
{% elif content.domain is string_containing ".jp" %}
Markup that will only render on content hosted on .jp domains
{% else %}
Markup that will render on all other domains
{% endif %}
```

#### Output
```jinja2
Markup that will render on all other domains
```

This expression test checks to see if a string starts with a particular string. It is used in conjunction with the "is" operator.

#### Example
```jinja2
{% if content.slug is string_startingwith "es/" %}
Markup that will only render on content hosted in a /es/ subdirectory
{% elif content.slug is string_startingwith "jp/" %}
Markup that will only render on content hosted in a /jp/ subdirectory
{% else %}
Markup that will render on all subdirectories
{% endif %}
```

#### Output
```jinja2
Markup that will render on all subdirectories
```

The **truthy** expression test checks to see whether an expression evaluates to True.

The example below uses a boolean checkbox module to display an alert message.

#### Example
```jinja2
{% boolean "check_box" label='Show alert', value=True, export_to_template_context=True %}

{% if widget_data.check_box.value is truthy %}
<div class='alert'>Danger!</div>
{% endif %}
```

#### Output
```jinja2
<div class='alert'>Danger!</div>
```

The **undefined** expression test checks to see whether a variable is undefined in the context of the template. This test is different from none, in that undefined will be true when the variable is present but has no value; whereas, none will be true when the variable has a null value.

The example below checks a template for the existence of the variable "my\_var".

#### Example
```jinja2
{% if my_var is undefined %}
A variable named "my_var" does not exist on this template.
{% else %}
{{ my_var }}
{% endif %}
```

#### Output
```jinja2
A variable named "my_var" does not exist on this template.
```

The **upper** expression test evaluates to true when a string is all uppercase. Below is an inverse example of the lower expression test above.

#### Example
```jinja2
{% module "my_text" path="@hubspot/text" label='Enter text', value='Some TEXT that should be Uppercase', export_to_template_context=True %}

{% unless widget_data.my_text.value is upper %}
{{ widget_data.my_text.value|upper }}
{% endunless %}
```

#### Output
```jinja2
SOME TEXT THAT SHOULD BE UPPERCASE
```

The **within** expression tests checks if a variable is within a list.

#### Example
```jinja2
{% set numbers = [1, 2, 3] %}

{% if 2 is within numbers %}
	2 is in the list!
{% endif %}

{% if 4 is within numbers %}
	4 is in the list!
{% endif %}
```

#### Output
```jinja2
2 is in the list!
```


# Loops
## 
For loops can be used in HubL to iterate through sequences of objects. They will most commonly be used with rendering [blog content](/docs/building-blocks/templates/blog-template-markup) in a listing format, but they can also be used to sort through other sequence variables.

For loops begin with a `{% for %}` statement and end with an ` {% endfor %} ` statement. Within the `{% for %}` statement a single sequence item is named followed by `in` and then the name of the sequence. The code between the opening and closing `for` statements is printed with each iteration, and generally includes the printed variable of the individual sequence item. Below is the basic syntax of a for loop:

#### Example
```jinja2
{% for item in items %}
	{{ item }}
{% endfor %}
```

Below is a basic example that shows how to print a sequence of variable values into a list.

#### Example
```jinja2
{% set languages = ['HTML', 'CSS', 'Javascript', 'Python', 'Ruby', 'PHP,', 'Java'] %}

<h1>Languages</h1>;
<ul>
    {% for language in languages %}
    <li>{{ language }}</li>
    {% endfor %}
</ul>
```

#### Output
```jinja2
<h1>Languages</h1>
<ul>
    <li>HTML</li>
    <li>CSS</li>
    <li>Javascript</li>
    <li>Python</li>
    <li>Ruby</li>
    <li>PHP</li>
    <li>Java</li>
</ul>
```


## Loop properties
As a loop iterates, you can use [conditional logic](/docs/hubl/if-statements) to define the loop's behavior. The variable property `loop.index` keeps a count of the current number of the iterations of the loop. There are several other loop variable properties that count the iterations in different ways. These properties are described below:
| Variable | Description | 
|  ------  |  ------  | 
| loop.cycle | A helper function to cycle between a list of sequences. See the explanation below. | 
| loop.depth | Indicates how deep in deep in a recursive loop the rendering currently is. Starts at level 1 | 
| loop.depth0 | Indicates how deep in deep in a recursive loop the rendering currently is. Starts at level 0 | 
| loop.first | This variable evaluates to true, if it is the first iteration of the loop. | 
| loop.index | The current iteration of the loop. This variable starts counting at 1. | 
| loop.index0 | The current iteration of the loop. This variable starts counting at 0. | 
| loop.last | This variable evaluates to true, if it is the last iteration of the loop. | 
| loop.length | The number of items in the sequence. | 
| loop.revindex | The number of iterations from the end of the loop. Counting down to 1. | 
| loop.revindex0 | The number of iterations from the end of the loop. Counting down to 1. | 

Below are some examples that use different loop variables. The following basic example uses `loop.index` to keep a count that is printed with each iteration.

#### Example
```jinja2
{% set loopy = ['Content', 'Social', 'Contacts', 'Reports'] %}
{% for app in loopy %}
    {{ loop.index }}. {{app}} <br>
{% endfor %}
```

#### Output
```jinja2
1. Content <br>
2. Social <br>
3. Contacts <br>
4. Reports <br>
```

The next example uses conditional logic to check whether the length of the loop is `divisibleby` certain numbers. It then renders the width of the post-item div accordingly. The example uses the standard blog post loop and assumes that there are 6 posts in the loop.

#### Example
```jinja2
{% for content in contents %}
{% if loop.length is divisibleby 4 %}
<div style="width:25%">Post content</div>

{% elif loop.length is divisibleby 3 %}
<div style="width:33.33332%">Post content</div>

{% else %}
<div style="width:50%">Post content</div>

{% endif %}
{% endfor %}
```

#### Output
```jinja2
<div style="width:33.33332%">Post content</div>
<div style="width:33.33332%">Post content</div>
<div style="width:33.33332%">Post content</div>
<div style="width:33.33332%">Post content</div>
<div style="width:33.33332%">Post content</div>
<div style="width:33.33332%">Post content</div>
<div style="width:33.33332%">Post content</div>
```


## Nested loops
Loops can also be nested with loops. The child for loop will run with each iteration of the parent for loop. In the example below, a list of child items is printed in a nested `` within a `` of parent items.

#### Example
```jinja2
{% set parents = ['Parent item 1', 'Parent item 2', 'Parent item 3'] %}
{% set children = ['Child item 1', 'Child item 2', 'Child item 3'] %}
<ul>
{% for parent in parents %}
<li>{{parent}}<ul>
    {% for child in children %}
    <li>{{child}}</li>
    {% endfor %}
    </ul>
</li>
{% endfor %}
</ul>
```

#### Output
```jinja2
<ul>
<li>Parent item 1<ul>
    <li>Child item 1</li>
    <li>Child item 2</li>
    <li>Child item 3</li>
    </ul>
</li>

<li>Parent item 2<ul>
    <li>Child item 1</li>
    <li>Child item 2</li>
    <li>Child item 3</li>
    </ul>
</li>

<li>Parent item 3<ul>
    <li>Child item 1</li>
    <li>Child item 2</li>
    <li>Child item 3</li>
    </ul>
</li>
</ul>
```


## cycle
The cycle tag can be used within a for loop to cycle through a series of string values and print them with each iteration. One of the most practical applications to this technique is applying alternating classes to your blog posts in a listing. This tag can be used on more than two values and will repeat the cycle if there are more loop iterations than cycle values. In the example below, a class of `odd` and `even` are applied to posts in a listing (the example assumes that there are 5 posts in the loop).

Please note that there are **no spaces** between the comma-separated cycle string values.

#### Example
```jinja2
{% for content in contents %}
    <div class="post-item {% cycle 'odd','even' %}">Blog post content</div>
{% endfor %}
```

#### Output
```jinja2
<div class="post-item odd">Blog post content</div>
<div class="post-item even">Blog post content</div>
<div class="post-item odd">Blog post content</div>
<div class="post-item even">Blog post content</div>
<div class="post-item odd">Blog post content</div>
```


## Variables within loops
You can call variables that are defined outside of a loop, from within a loop, but not the other way around.

## Key, value pairs in loops
If the dict of information you are looping through has key and value pairs, a simple for loop would only have access to the values. If you wish to have access to both the keys and values within the for loop, the HubL would be formatted as such:

#### Example
```jinja2
{‌% set dict_var = {'name': 'Cool Product', 'price': '$20', 'size':'XL'} %}  
{‌% for key, val in dict_var.items() %}
    {‌{ key }}: {‌{ val }}<br>
{‌% endfor %}
```

#### Output
```jinja2
name: Cool Product <br>
price: $20 <br>
size: XL <br>
```


## Iterate a set number of times
Sometimes you want to iterate a set number of times, this can be useful in generating HTML or CSS. You can do this using the range function.

#### Example
```jinja2
{% for x in range(0,5) %}
	{{loop.index}}
{% endfor %}
```

#### Output
```jinja2
1 2 3 4 5
```


# If Statements
## 
The following article examines HubL [if statements](#basic-if-statement-syntax) and [unless statements](#unless-statements). If statements often contain HubL [supported operators](/docs/hubl/operators-and-expression-tests) and can be used to execute [expression tests](/docs/hubl/operators-and-expression-tests#expression-tests).

## Basic if statement syntax
HubL uses if statements to help define the logic of a template. The syntax of HubL if statements is very similar to conditional logic in Python. `if` statements are wrapped in [statement delimiters](/docs/hubl/variables-macros-syntax), starting with an opening `if` statement and ending with an `endif`.

The example below provides the basic syntax of an if statement, where "condition" would be replaced with the boolean rule that you were going to evaluate as being true of false.

#### Example
```jinja2
{% if condition %}
	If the condition is true print this to template.
{% endif %}
```

Now that you have seen the basic syntax, let's look at a few actual examples of basic if statements. The next examples below show if statements that check to see whether or not a HubL module with the name `my_module` and whether a variable named `my_module` are present on a template. Notice that without any operators, the if statement will evaluate whether or not the module is defined in the context of the template.

#### Example
```jinja2
{% module "my_module" path="@hubspot/rich_text", label='My rich text module', html='Default module text' export_to_template_context=true %}

{% if widget_data.my_module %}
	A module named "my_module" is defined in this template.
{% endif %}


{% set my_variable = "A string value for my variable" %}    
{% if my_variable %}
	The variable named my_variable is defined in this template.
{% endif %}
```

Notice that when evaluating the HubL module, the module name is left in quotes within the `if` statement and while testing the variable no quotes are used around the variable name. In both examples above, the module and the variable exist in the template, so the statements evaluate to print the markup. Please note that these examples are only testing whether the module and variable are defined, not whether or not they have a value.

Now let's look at an `if` statement that evaluates whether a module has a value, instead of evaluating whether it exists on the template. To do this, we need to use the [export\_to\_template\_context](/docs/building-blocks/modules/export-to-template-context) parameter. In the example below, if the text module is valued in the content editor, the markup would print. If the module's text field were cleared, no markup would render. If you are working within custom modules, there is a simplified `widget.widget_name` syntax outlined in the [example here](/docs/building-blocks/modules/configuration).

#### Example
```jinja2
{% module "product_names" path="@hubspot/text", label='Enter the product names that you would like to render the coupon ad for', value='all of our products', export_to_template_context=True %}

{% if widget_data.product_names.value %}
<div class="coupon-ad">
<h3>For a limited time, get 50% off {{ widget_data.product_names.value}}! </h3>
</div>
{% endif %}
        
```

#### Output
```jinja2
<div class="coupon-ad">
<h3>For a limited time get 50% off all of our products! </h3>
</div>  
```


## Using elif and else
`if` statements can be made more sophisticated with additional conditional statements or with a rule that executes when the condition or conditions are false. `elif` statements allow you to add additional conditions to your logic that will be evaluated after the previous condition. **`else`** statements define a rule that executes when all other conditions are false. You can have an unlimited number of `elif` statements within a single if statement, but only one `else` statement.

Below is the basic syntax example of if statement that uses the [&lt;= operator](/docs/hubl/operators-and-expression-tests#comparison) to check the value of a variable. In this example, the template would print: "Variable named number is less than or equal to 6."

#### Example
```jinja2
{% set number = 5 %}

{% if number <= 2 %}
	Variable named number is less than or equal to 2.
{% elif number <= 4 %}
	Variable named number is less than or equal to 4.
{% elif number <= 6 %}
	Variable named number is less than or equal to 6.
{% else %}
	Variable named number is greater than 6.
{% endif %}
```

Below is one more example that uses a choice module to render different headings for a careers page, based on the department chosen by the user. The example uses the [== operator](/docs/hubl/operators-and-expression-tests#comparison), to check for certain predefined values in the choice module.

#### Example
```jinja2
{% choice "department" label='Choose department', value='Marketing', choices='Marketing, Sales, Dev, Services' export_to_template_context=True %}
        
{% if widget_data.department.value == 'Marketing' %}

<h3>Want to join our amazing Marketing team?!</h3>
<h4>We have exciting career opportunities on the {{ widget_data.department.value }} team.</h4>

{% elif widget_data.department.value == 'Sales' %}

<h3>Are you a Sales superstar?</h3>
<h4>We have exciting career opportunities on the {{ widget_data.department.value }} team.</h4>        
        
{% elif widget_data.department.value == 'Dev' %}
        
<h3>Do you love to ship code?</h3>
<h4>We have exciting career opportunities on the {{ widget_data.department.value }} team.</h4>
        
{% else %}
        
<h3>Want to work with our awesome customers?</h3>
<h4>We have exciting career opportunities on the {{ widget_data.department.value }} team.</h4>
        
{% endif %}
```


## Unless statements
`unless` statements are conditionals just like `if` statements, but they work on the inverse logic. They will render and compile the code between the opening and closing tags, unless the single boolean condition evaluates to true. Unless statements begin with an **`unless`** and end with an **`endunless`.** They do not support `elif` or `else`.

Below is an example that prints an "Under construction" header, unless the rich text field is valued. If the rich text field has content, then that content will display.

#### Example
```jinja2
{% module "my_page_content" path="@hubspot/rich_text", label='Enter your page content', html='' export_to_template_context=true %}

{{ widget_data.my_page_content.html }}

{% unless widget_data.my_page_content.html %}
<h1>This page is under construction.</h1>
<h3>Come back soon!</h3>
{% endunless %}
```


## ifchanged
In addition to if and unless statements, HubL supports `ifchanged` statements. These statements can be used to only render markup when a variable has changed since a prior invocation of this tag.

## Inline if statements
HubL supports inline `if` statements. These can be used to write conditional logic in a concise manner with [operators and expression tests](/docs/hubl/operators-and-expression-tests).

#### Example
```jinja2
{% set color = "Blue" if is_blue is truthy else "Red" %}     // color == "blue"  

{{ "Blue" if is_blue is truthy else "Red" }}     // "Blue"

{% set dl = true %}
<a href="http://example.com/some.pdf" {{"download" if dl }} >Download PDF</a>
```


## Ternary operators
It is also possible to use ternary operators to quickly write conditional logic with [operators and expression tests](/docs/hubl/operators-and-expression-tests#logical).

#### Example
```jinja2
// If the variable is_blue is true, output "blue", otherwise output"red"
{{ is_blue is truthy ? "blue" : "red" }}

// Set the variable is_red to false if is_blue is true, otherwise set to true
{% set is_red = is_blue is truthy ? false : true %}
```


# Variables and Macros
## 
HubL uses variables to store and output values to the template. Variables can be used in template logic or iterated through with for loops. In addition to variables, macros are another useful tool for printing repetitive yet dynamic sections of code throughout your templates.

Variables are expressions delimited by `}}`. The basic syntax of variables is as follows:

#### Example
```jinja2
// variables
{{ variable }}
{{ dict.attribute }}
```


## Variables
Variables are either a single word in an expression or an attribute of a dictionary. HubL uses Python-based data structures called dictionaries or **dicts** to store various sets of variables. For example, HubSpot uses a dictionary "content" to house many attributes that pertain to the content created with that template. For example the `content.absolute_url` prints the URL of the specific piece of content.

HubSpot has many predefined variables that can be used throughout your page, blog, and email templates. You can see a complete reference list of supported variables, [here](/docs/hubl/variables). You can also view the [developer info](/docs/developer-reference/debugging-and-errors#developer-info) when browsing any page from your portal.

In addition to printing the values of variables and dictionary attributes in a template, you can also define your own variables. You can store strings, booleans, integers, sequences, or create dictionaries within a single variable. Variables are defined within statement delimiters using the word "set". Once stored, variables can then be printed by stating the variable name as an expression. Below you can see various types of information stored in variables and then printed.

Variables should either be single words or use underscores for spaces (ie my\_variable). **HubL does not support hyphenated variable names.**

#### Example
```jinja2
{% set string_var = "This is a string value stored in a variable" %}
{{ string_var}}

{% set bool_var = True %}
{{ bool_var}}

{% set int_var = 53 %}
{{ int_var}}

{% set seq_var = ['Item 1', 'Item 2', 'Item 3'] %}
{{ seq_var}}

{% set var_one = "String 1" %}
{% set var_two = "String 2" %}
{% set sequence = [var_one,  var_two] %}
{{ sequence }}

{% set dict_var = {'name': 'Item Name', 'price': '$20', 'size':'XL'} %}
{{ dict_var.price }}
```

#### Output
```jinja2
This is a string value stored in a variable

True

53

[Item1, Item2, Item3]

[String 1, String 2]

$20
```

Each example above stores a different type of variable, with the final example storing two different variables in a sequence.

In addition to printing values, variables can be used in [if statements](/docs/hubl/if-statements), as [filter](/docs/hubl/filters) parameters, as [function](/docs/hubl/functions) parameters, as well as iterated through with [for loops](/docs/hubl/for-loops) (sequence variables only).

One common usage is to use variables to define common CSS values in your stylesheet. For example, if you have a color that you use over and over again throughout your CSS file. That way, if you need to change that color, you can change the variable value, and all references to that variable will be updated, the next time that you publish the file.

#### Example
```jinja2
<!-- defines variable and assigns HEX color -->
{% set primaryColor = '#F7761F' %} 
        
a {
    color: {{ primaryColor }}; {# prints variable HEX value #}
} 
```


## Macros
HubL macros allow you to print multiple statements with a dynamic value. For example, if there is a block of code that you find yourself writing over and over again, a macro may be a good solution, because it will print the code block while swapping out certain arguments that you pass it.

The macro is defined, named, and given arguments within a HubL statement. The macro is then called in a statement that passes its dynamic values, which prints the final code block with the dynamic arguments. The basic syntax of a macro is as follows:

#### Example
```jinja2
{% macro name_of_macro(argument_name, argument_name2)  %}
    {{ argument_name }}
    {{ argument_name2 }}
{% endmacro %}
{{ name_of_macro('value to pass to argument 1', 'value to pass to argument 2')  }}
```

If your macro is returning whitespace in the form of new lines, you can strip whitespace in templates by hand. If you add a minus sign (`-`) to the start or end of a block, a comment, or a variable expression, the whitespaces before or after that block will be removed.

#### Example
```jinja2
{% macro name_of_macro(argument_name, argument_name2) -%}
    {{ argument_name }}
    {{ argument_name2 }}
{%- endmacro %}
```

Below shows a practical application of a macro to print a CSS3 properties with the various vendor prefixes, with a dynamic value. This allows you to print 5 lines of code with a single macro tag.

#### Example
```jinja2
{% macro trans(value) %} 
-webkit-transition: {{value}};
-moz-transition: {{value}};
-o-transition: {{value}};
-ms-transition: {{value}};
transition: {{value}};
{% endmacro %}
 

a {
    {{ trans('all .2s ease-in-out') }}
}
```


## Call
In some instances, you may want to pass additional dynamic information back into the macro block. For example, you may have a large piece of code that you want to feed back into the macro, in addition to the arguments. You can do this using call block and caller(). A call block works essentially like a macro but does not get its own name. The expression caller() specifies where the contents of the call block will render.

In the example below, a `` is added into a macro in addition to the two arguments.

#### Example
```jinja2
 {% macro render_dialog(title, class) %}
  <div class="{{ class }}">
      <h2>{{ title }}</h2>
      <div class="contents">
          {{ caller() }}
      </div>
  </div>
 {% endmacro %}

 {% call render_dialog('Hello World', 'greeting') %}
     <p>This is a paragraph tag that I want to render in my.</p>
 {% endcall %}
```

#### Output
```jinja2
<div class="greeting">
      <h2>Hello World</h2>
      <div class="contents">
          
     <p>This is a simple dialog rendered by using a macro and
     a call block.</p>
 
      </div>
  </div>
```


## Import
Another useful feature of macros is that they can be used across templates by importing one template file into another. To do this you will need to use the **import** tag. The import tag will let you specify a Design Manager file path to the template that contains your macros and give the macros a name in the template that you are including them in. You can then pass values into these macros without needing to redefine them.

For example, let's say that you have a .html template file that contains the following 2 macros. One macro is defined to set up a header tag and one is defined to generate a footer tag. This file is saved in Design Manager with the name `my_macros.html`.

#### Example
```jinja2
<!-- my_macros.html file -->
{% macro header(tag, title_text) %}
    <header> <{{ tag }}>{{ title_text }} </{{tag}}> </header>
{% endmacro %}

{% macro footer(tag, footer_text) %}
     <footer> <{{ tag }}>{{ footer_text }} </{{tag}}> </footer>
{% endmacro %}
```

In the template that will use these macros, an import tag is used that specifies the file path to the `my_macros.html` file. It also names the group of macros (in this example `header_footer`). Macros can then be executed by appending the macro name to the name given to the imported template. See the example below.

#### Example
```jinja2
{% import 'custom/page/web_page_basic/my_macros.html' as header_footer %}
{{ header_footer.header('h1', 'My page title') }}
<p>Some content</p>
{{ header_footer.footer('h3', 'Company footer info') }}
```

#### Output
```jinja2
<header><h1>My page title</h1></header>
<p>Some content</p>
<footer><h3>Company footer info</h3></footer>
```


## From
If you want to only import specific macros, instead of all macros contained in a separate .html file, you can use the **from** tag. With the from tag, specify only the macros that you want to import. Generally, using **import** will provide more flexibility, but this alternative is also supported.

The example below accesses the same `my_macros.html` file from the previous section of this article. But this time instead of importing all macros, it accesses only the footer macro.

#### Example
```jinja2
{% from 'custom/page/web_page_basic/my_macros.html' import footer %}
{{ footer('h2', 'My footer info') }}
```

#### Output
```jinja2
<footer><h2>My footer info</h2></footer>
```


## Variables within loops
You can call variables that are defined outside of a loop, from within a loop, but not the other way around.

You can also use functions in order to mutate objects for settings values on dict's or performing list operations. The following example is using the [`.update` list operation](/docs/hubl/functions#update):

#### Example
```jinja2
{% set obj = {val : 0} %}
{% for i in range(0, 10) %}
  {% do obj.update('val', obj.val + i) %}
{% endfor %}
{{ obj.val }}
```


