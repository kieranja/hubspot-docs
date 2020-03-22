# set_response_code
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

