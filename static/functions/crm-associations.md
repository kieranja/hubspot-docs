# crm_associations
Gets a list of CRM objects associated to an object from the HubSpot CRM. This function returns an object with the following attributes: `has_more`, `total`, `offset` and `results`.

- `has_more` indicates there are more results available beyond this batch (total &gt; offset).
- `total` is the total number of results available.
- `offset` is the offset to use for the next batch of results.
- *`results`* returns an array of the specified associated objects matching the function's parameters

For security purposes, only Product objects can be retrieved on a publicly accessible page. Any other object type must be hosted on a page which is either [password protected](https://knowledge.hubspot.com/cos-pages-editor/how-can-i-password-protect-my-pages) or requires a [CMS Membership login](https://knowledge.hubspot.com/cms-pages-editor/control-audience-access-to-pages). Objects in the *results* array are returned as a dict of properties and values.

#### Example
```jinja2
{% set associated_contacts = crm_associations(847943847, 2, 'limit=3&years_at_company__gt=2&orderBy=email', 'firstname,email', false) %} 
{{ associated contacts }}
```

#### Output
```jinja2
{has_more=true, offset=3, total=203, results=[{firstname=Aimee, id=905, email=abanks@company.com}, {firstname=Amy, id=1056, email=abroma@company.com}, {firstname=Abigael, id=957, email=adonahu@company.com}]}
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| id | Id | Id of object to find associations from. | 
| association type id | Integer | Id of the association type to use. | 
| query | String | Query string delimited by &. All expressions are ANDed together. Supported operators are eq (default), neq, lt, lte, gt, gte, is_null and not_null. | 
| properties | String | Optional. A comma-separated list of properties to return. By default, a small set of common properties are returned. The id property is always returned. | 
| formatting | Boolean | Optional. Format values such as dates and currency according to this portal's settings. Omit or pass false for raw strings. | 

