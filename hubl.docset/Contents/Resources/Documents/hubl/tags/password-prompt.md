# Password prompt
Adds a password prompt to password-protected pages.

#### Example
```jinja2
{% password_prompt "password_prompt" %}
{% password_prompt "my_password_prompt" submit_button_text='Submit', bad_password_message='Sorry, please try again.\n', label='Password Prompt' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_password_prompt" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_password_prompt" style="" data-hs-cos-general-type="widget" data-hs-cos-type="password_prompt">
    <form method="post" action="/_hcms/protected/auth">
        <input name="content_id" type="hidden" value="1">
        <input name="redirect_url" type="hidden" value="https://preview.hs-sites.com/content-rendering/v1/public/_hcms/preview/template/multi">
        <input name="password" type="password" id="hs-pwd-widget-password" style="height: 22px; margin-top: -5px">
        <input type="submit" class="hs-button primary large" value="Submit">
    </form>
    <script type="text/javascript">
        document.getElementById("hs-pwd-widget-password").focus();
    </script>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| submit_button_text | String |  Label for button below password entry field. | 'Submit' | 
| bad_password_message | String |  Message displayed if incorrect password entered. |  '<p>Sorry, please try again.</p>' | 
| password_placeholder | String |  Defines placeholder text within the password field. | 'Password' | 

