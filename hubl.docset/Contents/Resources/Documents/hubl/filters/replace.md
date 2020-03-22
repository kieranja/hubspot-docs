# replace
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

