# blog_page_link
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

