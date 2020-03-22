# geo_distance
This function contains 4 parameters and calculates the ellipsoidal 2D distance between two points on Earth.

#### Example
```jinja2
{% for row in hubdb_table_rows(1234567, "geo_distance(loc,1.233,-5.678,mi)__gt=500") %}
    {{row.name}} <br> 
{% endfor %}
```

#### Output
```jinja2
Cambridge, MA<br>
Salem, MA<br>
San Diego, CA<br>
Chicago, IL<br>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| point1 | Location | location from a HubDB column. | 
| point2_lat | Latitude | Latitude of point2. | 
| point2_long | Longitude | Longitude of point2. | 
| units | String | Units for the return value. Options are FT for feet, MI for miles, M for meters or KM for kilometers. | 

