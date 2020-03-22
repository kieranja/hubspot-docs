# geo_distance
Calculates the ellipsoidal 2D distance between two points on Earth.

#### Example
```jinja2
<!-- in the example below the HubDB Location = 42.3667, -71.1060 (Cambridge, MA) | Chicago, IL = 37.3435, -122.0344 -->
{{ row.location | geo_distance(37.3435, -122.0344, "mi") }} MI
```

#### Output
```jinja2
861.1655563461395 MI
```

