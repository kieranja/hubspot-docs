# crm_object
Gets a single object from the HubSpot CRM.

For security purposes, only Product objects can be retrieved on a publicly accessible page. Any other object type must be hosted on a page which is either [password protected](https://knowledge.hubspot.com/cos-pages-editor/how-can-i-password-protect-my-pages) or requires a [CMS Membership login](https://knowledge.hubspot.com/articles/kcs_article/cms-pages-editor/control-audience-access-to-pages). Objects are returned as a dict of properties and values.

The first parameter (required) is a string specifying the CRM object type to get (contact, product, company, deal, ticket or quote).

The second parameter (required) specifies which CRM object to get. This parameter can either be a number, or a string. If you wish to get a specific CRM object by ID, pass a number of the ID of the object. If you wish to get a CRM object by querying `crm_objects`, pass a query string, delimited by `&`. All expressions are ANDed together. Supported operators are eq (default), `neq`, `lt`, `lte`, `gt`, `gte`, `is_null` and `not_null`.

The third parameter is a comma-separated list of properties to return. By default, a small set of common properties are returned.

The final parameter specifies if values such as dates and currency should be formatted according to the portal's settings. Pass 'false' for raw values.

#### Example
```jinja2
<!-- by query -->
{% set contact = crm_object("contact", "email=contact@company.com", "firstname,lastname", false) %}
<!-- by id -->
{% set contact = crm_object("contact", 123) %}
{{ contact.firstname }}
{{ contact.lastname }}
```

#### Output
```jinja2
Brian
Halligan
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| object_type | String | Contact, product, company, deal, ticket or quote. | 
| query | String | The id of the object OR a query string, delimited by &. All expressions are ANDed together. Supported operators are eq (default), neq, lt, lte, gt, gte, is_null and not_null. | 
| properties | String | Optional. A comma-separated list of properties to return. By default, a small set of common properties are returned. The id property is always returned. | 
| formatting | Boolean | Optional. Format values such as dates and currency according to this portal's settings. Omit or pass false for raw strings. | 

