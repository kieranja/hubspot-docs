# Choice
A choice module creates a dropdown in the content editor UI that prints the value selected by the user. Choice modules are great for giving your users a preset set of options, such as printing the type of page as a page header.   
  
In addition to printing the choice value, this module is useful for defining conditional template logic, when combined with the parameter **export\_to\_template\_context**. Learn more about [**export\_to\_template\_context, here**](/docs/building-blocks/modules/export-to-template-context).

#### Example
```jinja2
{% choice "choice" %}
{% choice "type_of_page" label='Choose the type of page', value='About', choices='About, Careers, Contact, Store' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_type_of_page" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_choice" style="" data-hs-cos-general-type="widget" data-hs-cos-type="choice">
About
</span>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| value | Boolean | The default field value for the dropdown | 
| choices | Sequence | A comma-separated list of values, or list of value-label pairs. The syntax for value label pairs is as follows: choices='[[\"value1\", \"Label 1\"], [\"value2\", \"Label 2\"]]'. The editor will display the label, while it will print the value to the page. | 

