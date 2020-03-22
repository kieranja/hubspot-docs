# trim
Strips leading and trailing whitespace. HubSpot already trims whitespace from markup, but this filter is documented for the sake of comprehensiveness.

#### Example
```jinja2
{{ " remove whitespace " }} 
{{ " remove whitespace "|trim }}
```

#### Output
```jinja2
 remove whitespace 
remove whitespace
```

