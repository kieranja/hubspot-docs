# Email subscriptions
This module renders when an email recipient goes to edit his or her subscription preferences. It should be used on a [Subscription Preference system template.](https://knowledge.hubspot.com/cos-general/use-system-templates-to-customize-error-subscription-and-password-prompt-pages)

#### Example
```jinja2
{% email_subscriptions "email_subscriptions" %}
{% email_subscriptions "email_subscriptions" resubscribe_button_text='Yes, resubscribe me!', unsubscribe_single_text='Uncheck the types of emails you do not want to receive:', subheader_text='\n    If this is not your email address, please ignore this page since the email associated with this page was most likely forwarded to you.\n', unsubscribe_all_unsubbed_text='You are presently unsubscribed from all of our emails. Would you like to receive our emails again?', button_text='Update email preferences', label='Subscription Preferences', header='Communication Preferences', unsubscribe_all_option='Unsubscribe me from all mailing lists.', unsubscribe_all_text='Or check here to never receive any emails:' %}
```

#### Output
```jinja2
<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style=""></span>
<form id="email-prefs-form" method="post" name="email-prefs-form">
	<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style=""></span>
	<div class="page-header">
		<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style=""></span>
		<h1><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style="">Communication Preferences</span></h1>
		<h2><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style="">example@email.com</span></h2><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style=""><br></span>
		<p><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style="">If this is not your email address, please ignore this page since the email associated with this page was most likely forwarded to you.</span></p>
	</div>
	<div class="email-prefs" id="content">
		<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style=""></span>
		<p class="header"><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style="">Uncheck the types of emails you do not want to receive:</span></p><span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style=""><input name="email" type="hidden" value="example@email.com"> <input name="unsub_url" type="hidden" value=""> <input name="unsubed_all" type="hidden" value="false"> <input name="subscription_ids" type="hidden" value=""></span>
		<div class="item">
			<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style=""></span>
			<div class="item-inner">
				<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style=""></span>
				<div class="checkbox-row">
					<span class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_email_subscriptions" data-hs-cos-general-type="widget" data-hs-cos-type="email_subscriptions" id="hs_cos_wrapper_email_subscriptions" style=""><span class="fakelabel"><input id="id_0" name="id_0" type="checkbox"> <span>Example Subscription #1</span></span></span>
				</div>
				<p>Your email type description</p>
			</div>
		</div>
		<div class="item">
			<div class="item-inner">
				<div class="checkbox-row">
					<span class="fakelabel"><input id="id_0" name="id_0" type="checkbox"> <span>Example Subscription #2</span></span>
				</div>
				<p>Your email type description</p>
			</div>
		</div>
		<div class="subscribe-options" style="margin-right: 0">
			<p class="header">Or check here to never receive any emails:</p>
			<p><label for="globalunsub"><input id="globalunsub" name="globalunsub" type="checkbox"> <span>Unsubscribe me from all mailing lists.</span></label></p>
		</div><input class="hs-button primary" id="submitbutton" type="submit" value="Update email preferences">
		<div class="clearer"></div>
	</div>
</form>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| header | String | Renders text in an h1 tag above the subscription preferences form. | "Communication Preferences" | 
| subheader_text | String | Populates text below the heading above the unsubscribe preferences. | "<p>\n    If this is not your email address, please ignore this page since the email associated with this page was most likely forwarded to you.\n</p>" | 
| unsubscribe_single_text | String | Renders text in a <p class="header"> above the subscription options. | "Uncheck the types of emails you do not want to receive:" | 
| unsubscribe_all_text | String | Renders text in a <p class="header"> above the unsubscribe from all emails checkbox input. | "Or check here to never receive any emails:" | 
| unsubscribe_all_unsubbed_text | String | Populates text within a <p> that renders, if a contact is currently unsubscribed from all emails. | "You are presently unsubscribed from all of our emails. Would you like to receive our emails again?" | 
| unsubscribe_all_option | String | Sets the text next to the unsubscribe from all emails checkbox input. | "Unsubscribe me from all mailing lists." | 
| button_text | String | Sets the text of the submit button that updates subscription preferences. | "Update email preferences"  | 
| resubscribe_button_text | String | Sets the text of the submit button for when contacts are resubscribing. | "Yes, resubscribe me!" | 

