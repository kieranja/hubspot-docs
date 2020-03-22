# Email subscriptions confirmation
The email subscriptions update confirmation is a module that can be added to the thank you template for when a recipient updates his or her subscription preferences or unsubscribes. It should be used on a [Subscription Preference system template.](https://knowledge.hubspot.com/cos-general/use-system-templates-to-customize-error-subscription-and-password-prompt-pages)

#### Example
```jinja2
{% email_subscriptions_confirmation "email_subscriptions_confirmation" %}
{% email_subscriptions_confirmation "email_subscriptions_confirmation" label='Subscriptions Update Confirmation', unsubscribe_all_success='You have successfully unsubscribed from all email communications.', subscription_update_success='You have successfully updated your email preferences.', subheader_text='\n    If this is not your email address, please ignore this page since the email associated with this page was most likely forwarded to you.\n' %}
```

#### Output
```jinja2
<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions_confirmation" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions_confirmation" id="hs_cos_wrapper_email_subscriptions_confirmation" style=""></span>
<div class="page-header">
	<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions_confirmation" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions_confirmation" id="hs_cos_wrapper_email_subscriptions_confirmation" style=""></span>
	<h2><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions_confirmation" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions_confirmation" id="hs_cos_wrapper_email_subscriptions_confirmation" style="">example@email.com</span></h2><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions_confirmation" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions_confirmation" id="hs_cos_wrapper_email_subscriptions_confirmation" style=""><br></span>
	<p><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions_confirmation" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions_confirmation" id="hs_cos_wrapper_email_subscriptions_confirmation" style="">If this is not your email address, please ignore this page since the email associated with this page was most likely forwarded to you.</span></p>
</div>
<div class="success" id="content">
	<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions_confirmation" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions_confirmation" id="hs_cos_wrapper_email_subscriptions_confirmation" style="">You have successfully updated your email preferences.</span>
</div>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| header | String | Renders text in an h1 tag above the unsubscribe form. | "Communication Preferences" | 
| subheader_text | String | Populates text above the confirmation message. | "<p>\n    If this is not your email address, please ignore this page since the email associated with this page was most likely forwarded to you.\n</p>" | 
| unsubscribe_all_success | String | Sets the text that will display when someone unsubscribes from all email communications. | "You have successfully unsubscribed from all email communications." | 
| subscription_update_success | String | Sets the text when a recipient updates his or her subscription preferences. | "You have successfully updated your email preferences." | 

