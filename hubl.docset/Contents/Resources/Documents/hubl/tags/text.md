# Text
Creates a single line of text. This module can be useful to be mixed into your markup, when used in conjunction with the no\_wrapper=True parameter. For example, if you wanted your end users to be able to define a destination of a predefined anchor, you could populate the href with a text module with **no\_wrapper=True**.

#### Example
```jinja2
{% text "text" %}
{% text "simple_text_field" label="Enter text here", value="This is the default value for this text field" %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_simple_text_field" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_text" style="" data-hs-cos-general-type="widget" data-hs-cos-type="text">This is the default value for this text field</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| value | String | Sets the default text of the single line text field. | 
           
           | 

