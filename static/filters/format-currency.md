# format_currency
Formats a given number as a currency based on portal's default currency and locale passed in as a parameter.
| Parameter | Description | 
|  ------  |  ------  | 
| locale `Optional` | The Java local Language tag. The default is the page's locale.Format : ISO639LanguageCodeInLowercase-ISO3166CountryCodeInUppercase | 


#### Example
```jinja2
{% set price = 100 %}
{{ price|format_currency("en-US") }}
{{ price|format_currency("fr-FR") }}
```

#### Output
```jinja2
$100
100 $
```

