# crm_objects
Gets a list of objects from the HubSpot CRM.

This function returns an object with the following attributes: `has_more`, `total`, `offset` and `results`.

- `has_more` indicates there are more results available beyond this batch (total &gt; offset).
- `total` is the total number of results available.
- `offset` is the offset to use for the next batch of results.
- *`results`* returns an array of the specified objects matching the function's parameters.

Results can be sorted using at least one order parameter in the query. For example, `crm_objects("contact", "firstname=Bob&order=lastname&order=createdate")` will order contacts with the first name `"Bob"` by last name and then by `createdate`. To reverse a sort, prepend `-` to the property name like `order=-createdate`.  
For security purposes, only Product objects can be retrieved on a publicly accessible page. Any other object type must be hosted on a page which is either [password protected](https://knowledge.hubspot.com/cos-pages-editor/how-can-i-password-protect-my-pages) or requires a [CMS Membership login](https://knowledge.hubspot.com/articles/kcs_article/cms-pages-editor/control-audience-access-to-pages). Objects in the `results` array are returned as a dict of properties and values.

#### Example
```jinja2
{% set objects = crm_objects("contact", "firstname__not_null=&limit=3", "firstname,lastname") %} 
{{ objects }}
```

#### Output
```jinja2
{has_more=true, offset=3, total=331, results=[{firstname=Brian, id=44151, lastname=Halligan}, {firstname=Dharmesh, id=44051, lastname=Shah}, {firstname=George, id=88551, lastname=Washington}]}
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| object_type | String | Contact, product, company, deal, ticket or quote. | 
| query | String | A query string, delimited by &. All expressions are ANDed together. Supported operators are eq (default), neq, lt, lte, gt, gte, is_null and not_null. | 
| properties | String | A comma-separated list of properties to return. By default, a small set of common properties are returned. The id property is always returned. | 
| formatting | Boolean | Format values such as dates and currency according to this portal's settings. Omit or pass false for raw strings. | 

