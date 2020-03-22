# Linked image
Creates a user-selectable image that is wrapped in a link. This module has all of the parameters of an image module with two additional parameters that specify the link destination URL and whether the link opens in a new window.

#### Example
```jinja2
{% linked_image "linked_image" %}
{% linked_image "executive_image" label='Executive photo', link="https://twitter.com/bhalligan", open_in_new_tab=True, alt='Photo of Brian Halligan', src='//cdn2.hubspot.net/hub/53/file-733888619-jpg/assets/hubspot.com/about/management/brian-home.jpg', width='300' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_executive_image" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_linked_image" style="" data-hs-cos-general-type="widget" data-hs-cos-type="linked_image">
    <a href="https://twitter.com/bhalligan" target="_blank" id="hs-link-executive_image" style="border-width:0px;border:0px;">
        <img src="//cdn2.hubspot.net/hub/53/file-733888619-jpg/assets/hubspot.com/about/management/brian-home.jpg?width=300" class="hs-image-widget " style="width:300px;border-width:0px;border:0px;" width="300" alt="Photo of Brian Halligan" title="Photo of Brian Halligan">
    </a>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| alt | String | Sets the default alt text for the image. | 
           
           | 
| src | String | Populates the src attribute of the img tag. | 
           
           | 
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
| target | String | Sets the target attribute of the link tag. | 
           
           | 

