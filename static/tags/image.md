# Image
Creates a image module that allows users to select an image from the content editor. If you want the image to be linked to a destination URL, you should use linked\_image below.

#### Example
```jinja2
{% image "image" %}
{% image "executive_image" label='Executive photo', alt='Photo of Brian Halligan', src='//cdn2.hubspot.net/hub/53/file-733888619-jpg/assets/hubspot.com/about/management/brian-home.jpg', width='300' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_executive_image" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_image" style="" data-hs-cos-general-type="widget" data-hs-cos-type="image">
    <img src="//cdn2.hubspot.net/hub/53/file-733888619-jpg/assets/hubspot.com/about/management/brian-home.jpg?width=300" class="hs-image-widget " width="300" alt="Photo of Brian Halligan" title="Photo of Brian Halligan">
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

