# postal_location
The `postal_location` function returns the latitude/longitude location pair for a given postal code and country code (limited to US, CA, and GB).

#### Example
```jinja2
{{ postal_location("02139") }}
{% set location = postal_location("02139", "US") %}
{{ location.latitude }}
{{ location.longitude }}
```

#### Output
```jinja2
LatLon{latitude=42.3647, longitude=-71.1042}
42.3647
-71.1042
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| postal_code | String | Postal code of the location. | 
| country_code | String | Country code for the postal code. If not provided, the country will try to be inferred from the postal code. | 

