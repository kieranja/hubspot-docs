# Blog subscription
A blog subscription module renders the blog subscriber form for a particular blog. This form is automatically created whenever a blog is created in Content Settings, and there is always one subscription form per blog. Please note that the subscribe form's fields are configured within the Forms editor UI.

#### Example
```jinja2
{% blog_subscribe "blog_subscribe" %}
{% blog_subscribe "subscribe_designers_blog" select_blog='default', title='Subscribe to the Designers Blog', response_message='Thanks for Subscribing!', label='Blog Email Subscription', overrideable=False %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_blog_subscription" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_blog_subscribe" style="" data-hs-cos-general-type="widget" data-hs-cos-type="blog_subscribe">
<h3 id="hs_cos_wrapper_blog_subscription_title" class="hs_cos_wrapper form-title" data-hs-cos-general-type="widget_field" data-hs-cos-type="text">Subscribe to Designers Blog</h3>
<div id="hs_form_target_blog_subscription"></div>
<script charset="utf-8" src="//js.hsforms.net/forms/current.js"></script>
<script>
hbspt.forms.create({ portalId: '327485', formId: 'a8d73dc6-0d3a-486d-8938-b19f28b69c3c', formInstanceId: '60', pageId: 2749976739, pageName: 'Apple, Google & Starbucks: Inside the Web Design Style Guides of 10 Famous Companies', redirectUrl: 'http://designers.hubspot.com/blog/web-design-style-guides-examples?hsFormKey=a56a754bc4c3465015935953363b8ff3#blog_subscription', css: '', target: '#hs_form_target_blog_subscription', formData: { cssClass: 'hs-form stacked' } });
</script>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| select_blog | 'default' or blog ID | Selects which blog subscription form to render. This parameter accepts arguments of either 'default' or a blog ID (available in the URL of the Blog dashboard). If want to use your default blog, this parameter is unnecessary. | default | 
| title | String | Defines text in an h3 tag title above the subscribe form. | "Subscribe Here!" | 
| no_title | Boolean | If True, the h3 tag above the title is removed. | false | 
| response_message | String | Defines the inline thank-you message that is rendered when a user submits a form. Supports HTML. | "Thanks for Subscribing!" | 
| edit_form_link | String | This parameter generates a link that allows users to click through to the corresponding Form editor screen. This option will only show in the editor UI if the modules has the parameter overrideable=True. Here is an example where HubID and form ID would be replaced with the information from the URL of your default blog subscriber form: edit_form_link=' <ul>\n <li><a href="/forms/HubID/FormID/edit/" target="_blank">Default Blog</a></li> \n</ul> '. \n drops the code onto a new line. | 
           
           | 

