# xmlattr
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

