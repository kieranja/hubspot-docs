# Variables available in all templates
Many predefined HubSpot variables can be used in email, page, or blog templates. Below is a list of these variables.

*(Note: If you want to see additional information what these variables can output, [try using the pprint parameter](/docs/hubl/filters#pprint))*
The following variables will render on any type of content.
| Variable | Type | Description | 
|  ------  |  ------  |  ------  | 
| account | Dict	 | This variable is a dictionary that stores company personalization properties for a known contact. Properties can be accessed from this dict, by adding a period and the property name. For example, account.name would print the company name of a contact.Use of this variable will disable page caching.  | 
| company_domain | String | Prints the company domain from Website > Pages > Branding > Logo Link. | 
| contact | Dict | This variable is a dictionary that stores contact personalization properties for a known contact. Properties can be accessed from this dict, by adding a period and the property name. For example, contact.firstname would print the first name of a contact.Use of this variable will disable page caching.  | 
| content | Dict	 | This variable is a dictionary that stores various properties pertaining to a specific piece of content such as an email, a page, or a post. | 
| content.absolute_url | String | Prints the full URL of a page, post, or web page version of an email. | 
| content.archived | Boolean | This variable evaluates to True, if the page or email was marked as archived by the user. | 
| content.author_email | String | The email address of the content creator. | 
| content.author_name | String | The first and last name of the content creator. | 
| content.author_username | String | The HubSpot username of the content creator. | 
| content.campaign | String | The GUID for the marketing campaign that this page or email is associated with. This unique ID can be found in the URL of a particular campaign in the Campaign's tool. | 
| content.campaign_name | String | The name of the marketing campaign that this page, this post, or this email is associated with. | 
| content.created | Datetime | A datetime object for when the content was originally created, in UTC time. This variable can be formatted with the datetime filter. | 
| content.meta_description | String | When pulling the meta description of a page, it is better to use the variable page_meta.meta_description. | 
| content.name | String | The name of a post, email, or page. For pages and emails this will print the internal content name, while for posts this will print the post title. For blog posts, this is the post title that displays. For other types of content, this is generally an internal name. This variable includes a wrapper so that it is editable via the UI, when included in blog posts. If you want to print the content name without a wrapper, use page_meta.name. | 
| content.publish_date | Datetime | A datetime object representing when the content was published, in UTC time. This variable can be formatted with the datetime filter. | 
| content.publish_date_localized | String | A string representing the datetime when the content was published, in the local time as defined in the HubSpot Report settings. This variable is also subject to the language and  date format settings in Settings > Website > Blog > Date Formats. | 
| content.template_path | String | The Design Manager file path to your template (ie custom/page/web_page_basic/my_template.html). | 
| content.updated | Datetime | A datetime object for when the user last updated the content, in UTC time. This variable can be formatted with the datetime filter. | 
| content_id | String | Prints the unique ID for a page, post, or email. This ID can be found in the URL of the editor. You can use this variable as an alias for content.id. | 
| favicon_link | String | Prints the source URL of the favicon. This image is set in Settings > Website > Pages > Branding. | 
| hub_id | String | The portal ID of your HubSpot account. | 
| hubspot_analytics_tracking_code | String | Includes the analytics tracking code. This tag is not necessary, because standard_footer_includes, already renders the tracking code. | 
| local_dt | Datetime | A datetime object of the current time in the time zone defined in your Report Settings. | 
| local_time_zone | String | The time zone, as configured in your HubSpot Report Settings. | 
| page_meta.canonical_url | String | The official URL that this page should be accessed at. Usually does not include any query string parameters. Use this for the rel='canonical' tag. HubSpot automatically canonicalizes URLs. | 
| page_meta.html_title | String | The title of the page. This variable should be used in the <title> tag of HTML templates.   | 
| page_meta.meta_description | String | The meta description of a page. This variable should be used in the "description" <meta> tag of HTML templates. | 
| page_meta.name | String | An alias for content.name. | 
| portal_id | String | An alias for hub_id | 
| request_contact | Dict | A dictionary containing data about the requested contact.Use of this variable will disable page caching.  | 
| site_settings | Dict | The site_settings dict contains various settings from such as colors and fonts (see below). | 
| year | String | Prints the current year. | 

