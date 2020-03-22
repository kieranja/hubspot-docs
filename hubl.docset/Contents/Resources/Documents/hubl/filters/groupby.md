# groupby
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

