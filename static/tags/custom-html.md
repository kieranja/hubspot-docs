# Custom HTML
A custom HTML module allows users to enter raw HTML into the content editor. If you need to add extensive default HTML to the module, you may want to use [block syntax](/docs/hubl/hubl-module-syntax-and-parameters#block-syntax).

#### Example
```jinja2
{% raw_html "raw_html" %}
{% raw_html "my_custom_html_module" label="Enter HTML here" value='<div>My HTML Block</div>' %}


Block Syntax Example:

{% widget_block raw_html "my_custom_html_module" overrideable=True, label='My custom HTML module'  %}
        {% widget_attribute "value" %}
            <div>Default HTML block</div>
        {% end_widget_attribute %}
{% end_widget_block %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_my_custom_html_module" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_raw_html" style="" data-hs-cos-general-type="widget" data-hs-cos-type="raw_html">
    <div>My HTML block</div>
</span>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| value | String | Sets the default content HTML of the module. | 

