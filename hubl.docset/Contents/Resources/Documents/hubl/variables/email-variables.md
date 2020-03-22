# Email variables
The following variables are specifically for HTML email templates or HubL template modules in email layouts.
| Variable | Type | Description | 
|  ------  |  ------  |  ------  | 
| background_color | String | Email-template only alias for the color and font setting described above. | 
| body_border_color | String | Email-template only alias for the color and font setting described above. | 
| body_border_color_choice | String | Email-template only alias for the color and font setting described above. | 
| body_color | String | Email-template only alias for the color and font setting described above. | 
| content.create_page | Boolean | This variable is True, if there is a web page version of the email. | 
| content.email_body | Richtext | The main body of the email. This variable renders a rich text module. | 
| content.emailbody_plaintext | String | The optional override of the plain text email body | 
| content.from_name | String | The from name of the email sender | 
| content.reply_to | String | The reply to address for the email | 
| content.subject | String | The subject of the email | 
| email_body_border_css | String | Email-template only alias for the color and font setting described above. | 
| email_body_padding | string | The email body padding setting. This setting is located in Settings > Marketing > Email > Configuration > Size. | 
| email_body_width | String | The email body width setting. This setting is located in Settings > Marketing > Email > Configuration > Size. | 
| primary_accent_color | String | Email-template only alias for the color and font setting described above. | 
| primary_font | Enumeration | Email-template only alias for the color and font setting described above. | 
| primary_font_color | String | Email-template only alias for the color and font setting described above. | 
| primary_font_size | String | Email-template only alias for the color and font setting described above. | 
| primary_font_size_num | String | Prints the font size number from Settings > Marketing > Email > Configuration > Font. Excludes "px". | 
| secondary_accent_color | String | Email-template only alias for the color and font setting described above. | 
| secondary_font | Enumeration | Email-template only alias for the color and font setting described above. | 
| secondary_font_color | String | Email-template only alias for the color and font setting described above. | 
| secondary_font_size_num | String | Prints the font size number from Settings > Marketing > Email > Configuration > Font. Excludes "px". | 
| site_settings.company_street_address_2 | String | Prints the address line 2 from Settings > Marketing > Email > Configuration > Footer. | 
| site_settings.office_location_name | String | Prints the office location name from Settings > Marketing > Email > Configuration > Footer. | 
| subscription_confirmation_url | String | Prints the URL of the subscription preferences confirmation page. This URL is dynamically generated on send. | 
| subscription_name | String | Prints the name of the Email Type specified for that email. | 
| unsubscribe_anchor | String | Generates an anchor tag with the work "unsubscribe" linked to your unsubscribe page. | 
| unsubscribe_link_all | String | Renders a link to unsubscribe from all email communications, as opposed to a link to manage subscription preferences. | 
| unsubscribe_section | String | Renders an unsubscribe section that includes an unsubscribe link, as well as help text. | 
| view_as_page_section | String | Generates a link with help text that leads to a webpage version of an email. | 
| view_as_page_url | String | Generates a link that leads to a webpage version of an email. | 

