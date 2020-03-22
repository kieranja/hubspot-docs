# get_public_template_url_by_id
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

