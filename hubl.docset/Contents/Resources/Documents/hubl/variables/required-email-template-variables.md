# Required email template variables
To be [CAN-SPAM ](https://knowledge.hubspot.com/email/can-i-customize-my-can-spam-email-footer)compliant, all emails sent through HubSpot require certain company and opt-out information; therefore, HubSpot email templates require certain variables. There are additional email variables that are optional which are listed [further down this page](#email-variables).
| Variable | Type | Description | 
|  ------  |  ------  |  ------  | 
| site_settings.company_city | String | Prints the company city (set in Settings > Marketing > Email > Configuration > Footer). | 
| site_settings.company_name | String | Prints the company name (set in Settings > Marketing > Email > Configuration > Footer). | 
| site_settings.company_state | String | Prints the company state (set in Settings > Marketing > Email > Configuration > Footer). | 
| site_settings.company_street_address_1 | String | Prints the company address (set in Settings > Marketing > Email > Configuration > Footer). | 
| unsubscribe_link | String | Prints the URL of the page that allows recipients to manage subscription preferences or unsubscribe from email communications. This variable should be used in the href attribute of an <a>. | 

