# Header
Generates a header module that will render text as an h1-h6 tag.

#### Example
```jinja2
{% header "header"  %}
{% header "my_header" header_tag='h1', overrideable=True, value='A clear and bold header', label='Header' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_my_header" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_header" style="" data-hs-cos-general-type="widget" data-hs-cos-type="header">
    <h1>A clear and bold header</h1>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| header_tag | String | Select which heading tag to render. Possible values include: h1, h2, h3, h4, h5, h6. | h1 | 
| value | String | Renders default text within the heading module. | "A clear bold header" | 

