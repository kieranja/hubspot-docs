# plus_time
Adds an amount of time to a datetime object.
| Parameter | Description | 
|  ------  |  ------  | 
| diff `Required` | Amount to add. | 
| timeunit `Required` | Valid time units are nanos , micros , millis , seconds , minutes , hours , half_days , days , weeks , months , years , decades , centuries , millennia , and eras . | 


#### Example
```jinja2
{% set date = "2018-07-14T14:31:30+0530"|strtotime("yyyy-MM-dd'T'HH:mm:ssZ") %}
{{ date }}
{{ date|plus_time(5, 'days') }}
```

#### Output
```jinja2
2018-07-14 14:31:30
2018-07-19 14:31:30
```

