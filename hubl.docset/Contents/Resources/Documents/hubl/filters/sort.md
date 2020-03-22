# sort
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

