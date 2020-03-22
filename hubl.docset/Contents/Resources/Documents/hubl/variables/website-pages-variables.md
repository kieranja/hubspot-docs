# Website pages variables
The following variables are available for site pages, landing pages, system pages, and blogs.
| Variable | Type | Description | 
|  ------  |  ------  |  ------  | 
| builtin_body_classes | String | This variable dynamicaly prints helpful classes that help differentiate the markup of content created with that template (ie type of content, content name, etc). This makes styling different types of content or particular pages easier. This variable should be used in the class attribute of the body tag on coded templates. | 
| request_contact.is_logged_in | String | This variable defines whether or not the requesting contact is logged in to a website's gated content (see control audience access documentation for further information). The value of this variable will return true if the requesting contact is logged in, and false if the requesting contact has logged out. A contact can be logged out by directing them to the URL https://www.yourdomain.com/_hcms/mem/logout.Use of this variable will disable page caching.  | 
| request_contact.list_memberships | String | This variable returns a dict of ids that represents the lists of which the contact is a member.Use of this variable will disable page caching.  | 
| content.language | Dict | This variable returns a dict of information about the language settings of a page. {{ content.language.languageTag }} returns the language identifier of a page (i.e. "en" or "es"). {{ content.language.textDirection }} returns the text direction of the language of the page (i.e. "rtl" or "ltr"). | 

