# blog_by_id
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

