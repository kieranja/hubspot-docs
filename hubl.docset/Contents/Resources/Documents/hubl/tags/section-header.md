# Section header
Generates an h1 header and &lt;p&gt; subheader.

#### Example
```jinja2
{% section_header "section_header" %}
{% section_header "my_section_header" subheader='A more subdued subheader', header='A clear and bold header', label='Section Header'  %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_my_section_header" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_section_header" style="" data-hs-cos-general-type="widget" data-hs-cos-type="section_header">
    <div class="page-header section-header">
        <h1>A clear and bold header</h1>
        <p class="secondary-header"><span id="hs_cos_wrapper_subheader" class="section-subheader">A more subdued subheader</span></p>
    </div>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| header | String | Text to display in header. | 'A clear and bold header' | 
| subheader | String | Text to display in subheader. | 'A more subdued subheader' | 

