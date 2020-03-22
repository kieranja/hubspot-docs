# Gallery
Generates a HubSpot gallery module. This gallery module is based on [Slick](http://kenwheeler.github.io/slick/). While you can create a gallery module with standard module HubL syntax, If you want to predefine default slides using HubL, you must use block syntax. Both methods are shown below.

#### Example
```jinja2
{% gallery "crm_gallery" %}

<-- Block syntax -->
{% widget_block gallery "Gallery" display_mode='standard' sizing='static', transition='slide', caption_position='below', auto_advance=True, overrideable=True, description_text='', show_pagination=True, label='Gallery', loop_slides=True, num_seconds=5  %}
    {% widget_attribute "slides" is_json=True %}
        [{
            "caption": "CRM Contacts App", 
            "show_caption": true, 
            "link_url": "http://www.hubspot.com/crm", 
            "alt_text": "Screenshot of CRM Contacts", 
            "img_src": "http://go.hubspot.com/hubfs/Contacts-View-1.png?t=1430860504240", 
            "open_in_new_tab": true
        }, 
        {
            "caption": "HubSpot CRM Contact Profile", 
            "show_caption": true, 
            "link_url": "http://www.hubspot.com/", 
            "alt_text": "HubSpot CRM Contact Profile", 
            "img_src": "http://cdn2.hubspot.net/hubfs/53/Contact-Profile.png?t=1430860504240", 
            "open_in_new_tab": true
        }]
    {% end_widget_attribute %}
{% end_widget_block %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_crm_gallery" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_gallery" style=""
    data-hs-cos-general-type="widget" data-hs-cos-type="gallery">
    <div id="hs_cos_flex_gallery_crm_gallery" class="hs_cos_flex-gallery flex-gallery-main gallery-mode-gallery">
        <div class="hs_cos_flex-viewport" style="overflow: hidden; position: relative;">
            <ul class="hs_cos_flex-slides hs_cos_flex-slides-main "
                style="width: 800%; -webkit-transition-duration: 0s; transition-duration: 0s; -webkit-transform: translate3d(-1090px, 0px, 0px);">
                <li class="hs_cos_flex-slide-main clone" aria-hidden="true"
                    style="width: 1090px; float: left; display: block;">
                    <a href="//www.hubspot.com/" target="_blank"><img
                            src="//cdn2.hubspot.net/hubfs/53/Contact-Profile.png?t=1430860504240&t=1430335520686"
                            alt="HubSpot CRM Contact Profile" draggable="false"></a>
                    <div class="caption">
                        HubSpot CRM Contact Profile
                    </div>
                </li>
                <li class="hs_cos_flex-slide-main hs_cos_flex-active-slide"
                    style="width: 1090px; float: left; display: block;">
                    <a href="//www.hubspot.com/crm" target="_blank"><img
                            src="http://go.hubspot.com/hubfs/Contacts-View-1.png?t=1430860504240&t=1430335520686"
                            alt="Screenshot of CRM Contacts" draggable="false"></a>
                    <div class="caption">
                        CRM Contacts App
                    </div>
                </li>
                <li class="hs_cos_flex-slide-main" style="width: 1090px; float: left; display: block;">
                    <a href="//www.hubspot.com/" target="_blank"><img
                            src="//cdn2.hubspot.net/hubfs/53/Contact-Profile.png?t=1430860504240&t=1430335520686"
                            alt="HubSpot CRM Contact Profile" draggable="false"></a>
                    <div class="caption">
                        HubSpot CRM Contact Profile
                    </div>
                </li>
                <li class="hs_cos_flex-slide-main clone" aria-hidden="true"
                    style="width: 1090px; float: left; display: block;">
                    <a href="//www.hubspot.com/crm" target="_blank"><img
                            src="http://go.hubspot.com/hubfs/Contacts-View-1.png?t=1430860504240&t=1430335520686"
                            alt="Screenshot of CRM Contacts" draggable="false"></a>
                    <div class="caption">
                        CRM Contacts App
                    </div>
                </li>
            </ul>
        </div>
        <ol class="hs_cos_flex-control-nav hs_cos_flex-control-paging">
            <li><a class="hs_cos_flex-active">1</a></li>
            <li><a class="">2</a></li>
        </ol>
        <ul class="hs_cos_flex-direction-nav">
            <li><a class="hs_cos_flex-prev" href="#">Previous</a></li>
            <li><a class="hs_cos_flex-next" href="#">Next</a></li>
        </ul>
    </div>
    <script>
        window.hsSliderConfig = window.hsSliderConfig || {};
        window.hsSliderConfig['crm_gallery'] = {
            mode: 'gallery',
            mainConfig: {
                "animationLoop": true,
                "direction": "horizontal",
                "slideshowSpeed": 5000.0,
                "controlNav": true,
                "smoothHeight": false,
                "namespace": "hs_cos_flex-",
                "slideshow": true,
                "selector": ".hs_cos_flex-slides > li",
                "animation": "slide"
            }
        };
    </script>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| slides | JSON | A JSON list of the default caption, the link url, the alt text, the image src, and whether to open in a new tab. See block syntax above. | 
           
           | 
| loop_slides | Boolean | When True, continuously loop through slides. | True | 
| num_seconds | Number | Time in seconds to pause between slides. | 5 | 
| show_pagination | Boolean | Provide buttons below slider to navigate among slides. | True | 
| sizing | Enumeration | Determines whether the slider changes sizes, based on the height of the slides. Possible values include: "static" or "resize". | "static" | 
| auto_advance | Boolean | Automatically advance slides after the time set in num_seconds. | False | 
| transition | Enumeration | Sets the type of slide transition. Possible values include: "fade" or "slide". | "slide" | 
| caption_position | Enumeration | Affects positioning of caption on or below the slide. Possible values include "below" or "superimpose". | "below" | 
| display_mode | Enumeration | Determines how the image gallery will be displayed. Possible values include: "standard", "lightbox", "thumbnail". | "standard" | 
| lightboxRows | Number | If "display_mode" is set to "lightbox", this parameter will control the number of rows displayed within the lightbox. | 3 | 

