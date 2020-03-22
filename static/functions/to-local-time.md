# to_local_time
Converts a UNIX timestamp to the local time, based on your HubSpot Report Settings. You can then apply a datetimeformat filter to format the date.

#### Example
```jinja2
{{ to_local_time(eastern_dt) }} 
```

#### Output
```jinja2
2015-05-13 10:37:31
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| date | Datetime | UNIX timestamp to convert to local time. | 

