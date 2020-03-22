# Form
Allows users to select a HubSpot form to add to their page.

#### Example
```jinja2
{% form "form" %}
{% form "my_form" form_to_use='08bd9f0d-3be9-41c2-93b6-231a3a71b143', title='Free Trial' %}


Block Syntax Example:
{% widget_block form "my_form" form_follow_ups_follow_up_type='', response_redirect_id=306590405, form_to_use='08bd9f0d-3be9-41c2-93b6-231a3a71b143', title='Free Trial', notifications_are_overridden=True, sfdc_campaign='', response_message='Thanks for submitting the form.', response_response_type='redirect', response_redirect_url='', overrideable=True, gotowebinar_webinar_key='', response_redirect_name='Homepage (http://www.hubspot.com/)', label='Form', response={message='Thank you for submitting the form.', redirect_url=''}  %}
        {% widget_attribute "notifications_override_email_addresses" is_json=True %}["noreply@hubspot.com"]{% end_widget_attribute %}
{% end_widget_block %}
```

#### Output
```jinja2
<div id="hs_cos_wrapper_my_form" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_form" style="" data-hs-cos-general-type="widget" data-hs-cos-type="form">
    <h3 id="hs_cos_wrapper_module_13885064832664947_title" class="hs_cos_wrapper form-title" data-hs-cos-general-type="widget_field" data-hs-cos-type="text">Free Trial</h3>
    <div id="hs_form_target_module_13885064832664947">
        <form accept-charset="UTF-8" enctype="multipart/form-data" id="hsForm_08bd9f0d-3be9-41c2-93b6-231a3a71b143_6756" class="hs-form stacked hs-custom-form" action="https://forms.hubspot.com/uploads/form/v2/158015/08bd9f0d-3be9-41c2-93b6-231a3a71b143" method="POST" novalidate="novalidate">
            <div class="hs_lastname field hs-form-field">
                <label placeholder="Enter your Last Name" for="lastname-08bd9f0d-3be9-41c2-93b6-231a3a71b143_6756">Last Name</label>
                <div class="hs-field-desc" style="display: none;"></div>
                <div class="input">
                    <input class="hs-input" type="text" id="lastname-08bd9f0d-3be9-41c2-93b6-231a3a71b143_6756" name="lastname" value="" placeholder="">
                </div>
            </div>
            <div class="hs_firstname field hs-form-field">
                <label placeholder="Enter your First Name" for="firstname-08bd9f0d-3be9-41c2-93b6-231a3a71b143_6756">First Name</label>
                <div class="hs-field-desc" style="display: none;"></div>
                <div class="input">
                    <input class="hs-input" type="text" id="firstname-08bd9f0d-3be9-41c2-93b6-231a3a71b143_6756" name="firstname" value="" placeholder="">
                </div>
            </div>
            <div class="hs_email field hs-form-field">
                <label placeholder="Enter your Email" for="email-08bd9f0d-3be9-41c2-93b6-231a3a71b143_6756">Email<span class="hs-form-required"> * </span></label>
                <div class="hs-field-desc" style="display: none;"></div>
                <div class="input">
                    <input class="hs-input" type="email" required="required" id="email-08bd9f0d-3be9-41c2-93b6-231a3a71b143_6756" name="email" value="" placeholder="">
                </div>
            </div>
            <div class="hs_submit">
                <div class="hs-field-desc" style="display: none;"></div>
                <div class="actions">
                    <input class="hs-button primary large" type="submit" value="Submit">
                </div>
            </div>
        </form>
    </div>
    <script charset="utf-8" src="//js.hsforms.net/forms/current.js"></script>
    <script>
        hbspt.forms.create({
            portalId: '158015',
            formId: '08bd9f0d-3be9-41c2-93b6-231a3a71b143',
            formInstanceId: '6756',
            pageId: 1,
            redirectUrl: "http:\/\/www.davidjosephhunt.com\/404",
            deactivateSmartForm: true,
            css: '',
            target: '#hs_form_target_module_13885064832664947',
            contentType: "landing-page",
            formData: {
            cssClass: 'hs-form stacked hs-custom-form'
            }
        });
    </script>
</div>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| form_key | String | Specifies a unique id for the form at the page level. | 
           
           | 
| form_to_use | String | Specifies which form to load by default, based on the Form ID. This ID is available in the form editor URL of a each form. | 
           
           | 
| title | String | Populates an h3 header tag above the form. | 
           
           | 
| no_title | Boolean |  If True, the h3 tag above the title is removed. | False | 
| form_follow_ups_follow_up_type | Enumeration | Specifies follow up actions such as enrolling a contact into a workflow or sending a simple follow up email. Possible values include: no_action, simple, and automation. | 
           
           | 
| simple_email_for_live_id | Number | Specifies the ID of the simple follow-up email for the live page. | 
           
           | 
| simple_email_for_buffer_id | Number | Specifies the ID of the simple follow-up email for the auto-save version of a page. | 
           
           | 
| follow_up_type_simple | Boolean | If true, enables a simple follow-up email. Alternative to form_follow_ups_follow_up_type. | 
           
           | 
| follow_up_type_automation | Boolean | If true, enrolls submissions in a workflow. Alternative to form_follow_ups_follow_up_type. | 
           
           | 
| simple_email_campaign_id | Number | Specifies the ID of the simple follow-up email. Alternative to simple_email_for_live_id. | 
           
           | 
| form_follow_ups_workflow_id | Number | Specifies the ID of the workflow in which to enroll submissions. | 
           
           | 
| response_redirect_url | String | If redirecting to an external page, this parameter specifies the URL to redirect to. | 
           
           | 
| response_redirect_id | Number | If redirecting to HubSpot hosted page, this parameter specifies the page ID of that page. The page ID is available in the page editor URL of each page. | 
           
           | 
| response_response_type | Enumeration | Determines whether to redirect to another page or to display an inline thank you message on submission. The value of this parameter should either be 'redirect' or 'inline'. | inline | 
| response_message | String | Sets an inline thank you message. This parameter supports HTML. | 
           
           | 
| notifications_are_overridden | Boolean | If True, the form will send form notifications to specified email addresses selected in the notifications_override_email_addresses parameter, instead of the form defaults | False | 
| notifications_override_guid_buffer | String | ID of override settings in auto-save version of page. | 
           
           | 
| notifications_override_guid | String | ID of override settings in live version of page. | 
           
           | 
| notifications_override_email_addresses | JSON | Block syntax supports a JSON list of email recipients that will be notified upon form submission. These email addresses will override the email notification settings set in the form. | 
           
           | 
| gotowebinar_webinar_key | String | Specifies the GoToWebinar webinar to enroll contacts who submit the form into. Only available for portals using the GoToWebinar integration. | 
           
           | 
| sfdc_campaign | String | Specifies the Salesforce campaign to enroll contacts who submit the form into. This parameter's value should be the SFDC campaign ID and is only available for portals that are integrated with Salesforce. | 
           
           | 

