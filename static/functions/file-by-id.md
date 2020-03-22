# file_by_id
This function returns the metadata of a file by ID. It accepts a single parameter, the numeric ID of the file to look up.

#### Example
```jinja2
{% set file = file_by_id(123) %} 
{{ file.friendlyUrl }}
```

#### Output
```jinja2
https://www.hubspot.com/hubfs/HubSpot_Logos/HSLogo_color.svg
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| file_id | Id | The ID of the file to look up. | 

