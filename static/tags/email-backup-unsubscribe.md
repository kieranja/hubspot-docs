# Email backup unsubscribe
The backup unsubscribe module renders for email recipients, if HubSpot is unable to determine their email address, when that recipient tries to unsubscribe. This module renders a form for the contact to enter his or her email address to unsubscribe from email communications. It should be used on an [Unsubscribe Backup system template.](https://knowledge.hubspot.com/cos-general/use-system-templates-to-customize-error-subscription-and-password-prompt-pages)

#### Example
```jinja2
{% email_simple_subscription "email_simple_subscription" %}
{% email_simple_subscription "email_simple_subscription" header='Email Unsubscribe', input_help_text='Your email address:', input_placeholder='email@example.com', button_text='Unsubscribe', label='Backup Unsubscribe' %}
```

#### Output
```jinja2
<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style=""></span>
<div class="page-header">
	<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style=""></span>
	<h1><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style="">Email Unsubscribe</span></h1><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style=""></span>
</div>
<form id="email-prefs-form" method="post" name="email-prefs-form" style="position: relative">
	<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style=""></span>
	<div id="content">
		<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style=""></span>
		<h3 style="font-weight: normal"><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style="">Your email address:</span></h3>
		<div style="padding-bottom: 10px">
			<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style=""><input class="email-edit hs-input" name="email" placeholder="email@example.com" style="padding: 6px; font-size: 15px; width: 507px; margin-left: 0px" type="email" value=""></span>
		</div><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style=""><input class="hs-button primary" id="submitbutton" type="submit" value="Unsubscribe"></span>
	</div><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_simple_subscription" data-hs-cos-general-type="widget" data-hs-cos-type="email_simple_subscription" id="hs_cos_wrapper_email_simple_subscription" style=""></span>
</form>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| header | String | Renders text in an h1 tag above the unsubscribe form. | "Email Unsubscribe" | 
| input_help_text | String | Renders help text in an h3 tag above your email unsubscribe form field. | "Your email address:" | 
| input_placeholder | String | Adds placeholder text within the email address form field. | "email@example.com" | 
| button_text | String | Changes the text of the unsubscribe form submit button. | "Unsubscribe" | 

