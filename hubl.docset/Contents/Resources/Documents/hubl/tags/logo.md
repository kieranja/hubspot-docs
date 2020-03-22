# Logo
A logo module renders your company's logo image from Content Settings.

#### Example
```jinja2
{% logo "logo" %}
{% logo "my_logo" width='200' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_my_logo" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_logo" style="" data-hs-cos-general-type="widget" data-hs-cos-type="logo">
    <a href="//www.hubspot.com" id="hs-link-my_logo">
        <img src="//cdn2.hubspot.net/hub/53/file-1237149549-png/assets/hubspot.com/V2-Global/hubspot-logo-dark.png?t=1430948896766&amp;width=200" class="hs-image-widget " width="200" alt="HubSpot logo" title="HubSpo logot">
    </a>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| suppress_company_name | Boolean | Hides company name if an image logo isn't set. | False | 
| alt | String | Sets the default alt text for the image. | Value in Content Settings | 
| src | String | Populates the src attribute of the img tag. | Value in Content Settings | 
| width | Number | Sets the width attribute of the img tag. | The width of the image | 
| height | Number | Sets a min-height in a style attribute of the img tag for email templates only. | The height of the image | 
| hspace | Number | Sets the hspace attribute of the img tag. | 
           
           | 
| align | String | Sets the align attribute of the img tag. Possible values include: left, right, & center. | 
           
           | 
| style | String | Adds inline CSS declarations to the img tag. For example style="border:1px solid blue; margin:10px" | 
           
           | 
| open_in_new_tab | Boolean | Selects whether or not to open the destination URL in another tab. | False | 
| link | String | Sets the destination URL of the link that wraps the img tag. | 
           
           | 
| override_inherited_src | Boolean | If true, use src from logo widget rather than src inherited from settings or template. | True | 

