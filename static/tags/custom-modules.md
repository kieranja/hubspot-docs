# Custom modules
Custom Modules allow HubSpot designers to create a custom group of editable content objects to be used across templates and pages on HubSpot’s CMS, while still allowing marketers to control the specific content appearing within those modules on a page-by-page basis. You can learn more about [custom modules and their simplified HubL syntax, here](/docs/building-blocks/modules).   
  
Custom modules must be built in the Custom Module editor, but they can be included into coded templates and HubL modules. You will see a 'Usage Snippet' in the right sidebar of the Custom Module editor under 'Template Usage'.  
  
Custom modules require the ID of the module as a string as well as a path parameter in order to specify which module to load. The usage snippet will also include a label parameter. See the syntax below:

#### Example
```jinja2
{% module "module_15677217712485" path="/Custom/Test custom module"  %}
{% module "module_25642219712432" path="/Assets/Custom calendar module" label="Custom calendar module" %}
```

#### Output
```jinja2
<div id="hs_cos_wrapper_module_15677217712485" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_module" style="" data-hs-cos-general-type="widget" data-hs-cos-type="module">content!</div>
<style>
    @import "//cdn2.hubspotqa.com/qa/hub/126/file-613025667-css/custom_widget_example.css"
</style>
<div>
    <img class="persons-photo" src="//cdn2.hubspotqa.com/qa/hub/124/file-1360297556-jpeg/dharmesh.jpeg"
        alt="dharmesh.jpeg">
    <div>
        <img class="company-logo with-background"
            src="//cdn2.hubspotqa.com/qa/hub/124/file-221882251-png/HubSpot_Logo_2x.png" width="60px" height="inherit"
            alt="HubSpot_Logo_2x.png">
    </div>
</div>
<div>
    <p class="quote">
        <span class="quotation-mark"><b>" </b></span>The Content Optimization System matches content with context to
        create a highly personalized, relevant and meaningful customer experience.
        <span class="quotation-mark"><b>" </b></span>
    </p>
</div>
<div class="name-and-company">
    <span><b>Dharmesh Shah,</b></span>
    <span>HubSpot</span>
</div>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| module_id | String | The id of the module to render. | 
| path | String | The path of the module to render. Include leading slash for absolute path, otherwise path is relative to template. Reference HubSpot default modules with paths corresponding to their HubL tags such as @hubspot/rich_text, @hubspot/linked_image, etc. | 

