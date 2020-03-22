# attr
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

