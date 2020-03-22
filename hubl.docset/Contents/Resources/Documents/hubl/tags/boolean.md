# Boolean
A boolean module creates a checkbox in the UI that prints "true" or "false." In addition to printing the value, this module is useful for defining conditional template logic, when combined with the parameter **export\_to\_template\_context**. Learn more about [**export\_to\_template\_context here**](/docs/building-blocks/modules/export-to-template-context).

#### Example
```jinja2
{% boolean "boolean" %}
{% boolean "nav_toggle" label='Hide navigation', value=False, no_wrapper=True %}
```

#### Output
```jinja2
false
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| value | Boolean | Determines whether the checkbox is checked or unchecked. | False | 

