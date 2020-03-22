# blog_post_archive_url
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

