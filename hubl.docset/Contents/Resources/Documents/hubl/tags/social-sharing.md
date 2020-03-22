# Social sharing
Social sharing modules generate social media icons that can be used to share a particular page. This module can be used with [block syntax](/docs/building-blocks/modules/syntax-and-parameters) to customize the icon images and more.

#### Example
```jinja2
{% social_sharing "social_sharing" %}
{% social_sharing "my_social_sharing" use_page_url=True %}

Block Syntax Example:


{% widget_block social_sharing "my_social_sharing" label='Social Sharing', use_page_url=True, overrideable=True  %}
        {% widget_attribute "pinterest" is_json=True %}{"custom_link_format": "", "pinterest_media": "http://cdn1.hubspot.com/hub/158015/305390_10100548508246879_837195_59275782_6882128_n.jpg", "enabled": true, "network": "pinterest", "img_src": "https://static.hubspot.com/final/img/common/icons/social/pinterest-24x24.png"}{% end_widget_attribute %}
        {% widget_attribute "twitter" is_json=True %}{"custom_link_format": "", "enabled": true, "network": "twitter", "img_src": "https://static.hubspot.com/final/img/common/icons/social/twitter-24x24.png"}{% end_widget_attribute %}
        {% widget_attribute "linkedin" is_json=True %}{"custom_link_format": "", "enabled": true, "network": "linkedin", "img_src": "https://static.hubspot.com/final/img/common/icons/social/linkedin-24x24.png"}{% end_widget_attribute %}
        {% widget_attribute "facebook" is_json=True %}{"custom_link_format": "", "enabled": true, "network": "facebook", "img_src": "https://static.hubspot.com/final/img/common/icons/social/facebook-24x24.png"}{% end_widget_attribute %}
        {% widget_attribute "email" is_json=True %}{"custom_link_format": "", "enabled": true, "network": "email", "img_src": "https://static.hubspot.com/final/img/common/icons/social/email-24x24.png"}{% end_widget_attribute %}
{% end_widget_block %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_social_sharing" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_social_sharing" style="" data-hs-cos-general-type="widget" data-hs-cos-type="social_sharing">
    <a href="http://www.facebook.com/share.php?u=http%3A%2F%2Fexample.com%2Fmy-page%3Futm_medium%3Dsocial%26utm_source%3Dfacebook" target="_blank" style="width:24px;border-width:0px;border:0px;">
        <img src="//static.hubspot.com/final/img/common/icons/social/facebook-24x24.png?width=24" class="hs-image-widget hs-image-social-sharing-24" style="max-height:24px;max-width:24px;border-width:0px;border:0px;" width="24" hspace="0" alt="Share on Facebook">
    </a>
    <a href="http://www.linkedin.com/shareArticle?mini=true&url=http%3A%2F%2Fexample.com%2Fmy-page%3Futm_medium%3Dsocial%26utm_source%3Dlinkedin" target="_blank" style="width:24px;border-width:0px;border:0px;">
        <img src="//static.hubspot.com/final/img/common/icons/social/linkedin-24x24.png?width=24" class="hs-image-widget hs-image-social-sharing-24" style="max-height:24px;max-width:24px;border-width:0px;border:0px;" width="24" hspace="0" alt="Share on LinkedIn">
    </a>
    <a href="https://twitter.com/intent/tweet?original_referer=http%3A%2F%2Fexample.com%2Fmy-page%3Futm_medium%3Dsocial%26utm_source%3Dtwitter&url=http%3A%2F%2Fexample.com%2Fmy-page%3Futm_medium%3Dsocial%26utm_source%3Dtwitter&source=tweetbutton&text=" target="_blank" style="width:24px;border-width:0px;border:0px;">
        <img src="//static.hubspot.com/final/img/common/icons/social/twitter-24x24.png?width=24" class="hs-image-widget hs-image-social-sharing-24" style="max-height:24px;max-width:24px;border-width:0px;border:0px;" width="24" hspace="0" alt="Share on Twitter">
    </a>
    <a href="http://pinterest.com/pin/create/button/?url=http%3A%2F%2Fexample.com%2Fmy-page%3Futm_medium%3Dsocial%26utm_source%3Dpinterest&media=http%3A%2F%2Fcdn1.hubspot.com%2Fhub%2F158015%2F305390_10100548508246879_837195_59275782_6882128_n.jpg" target="_blank" style="width:24px;border-width:0px;border:0px;">
        <img src="//static.hubspot.com/final/img/common/icons/social/pinterest-24x24.png?width=24" class="hs-image-widget hs-image-social-sharing-24" style="max-height:24px;max-width:24px;border-width:0px;border:0px;" width="24" hspace="0" alt="Share on Pinterest"></a>
    <a href="mailto:?subject=Check out http%3A%2F%2Fexample.com%2Fmy-page%3Futm_medium%3Dsocial%26utm_source%3Demail &body=Check out http%3A%2F%2Fexample.com%2Fmy-page%3Futm_medium%3Dsocial%26utm_source%3Demail" target="_blank" style="width:24px;border-width:0px;border:0px;">
        <img src="//static.hubspot.com/final/img/common/icons/social/email-24x24.png?width=24" class="hs-image-widget hs-image-social-sharing-24" style="max-height:24px;max-width:24px;border-width:0px;border:0px;" width="24" hspace="0" alt="Share on Email">
    </a>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| use_page_url | Boolean | If true, the module shares the URL of the page by default. | True | 
| link | String | Specifies a different URL to share, if use_page_url is false. | 
           
           | 
| pinterest | JSON | Parameters for Pinterest link format and icon image source. | See block syntax example, above | 
| twitter | JSON | Parameters for Twitter link format and icon image source. | See block syntax example, above | 
| linked_in | JSON | Parameters for LinkedIn link format and icon image source. | See block syntax example, above | 
| facebook | JSON | Parameters for Facebook link format and icon image source. | See block syntax example, above | 
| email | JSON | Parameters for email sharing link format and icon image source. | See block syntax example, above | 

