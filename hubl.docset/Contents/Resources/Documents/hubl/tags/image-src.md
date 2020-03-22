# Image src
An image src module creates a image selector in the content editor, but rather than printing a img tag, it renders the URL of the image. This tag is generally used with no\_wrapper=True parameter, so that the image src can be added to inline CSS or other markup. An alternative to using this tag is to use the export\_to\_template\_context parameter.

#### Example
```jinja2
{% image_src "image_src" %}
{% image_src "executve_image_src" src='//cdn2.hubspot.net/hub/53/file-733888614-jpg/assets/hubspot.com/about/management/dharmesh-home.jpg', no_wrapper=True %}
```

#### Output
```jinja2
//cdn2.hubspot.net/hub/53/file-733888614-jpg/assets/hubspot.com/about/management/dharmesh-home.jpg
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| src | String |  Specifies the default URL image src. | 
           
           | 

