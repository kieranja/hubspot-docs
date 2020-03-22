# minus_time
Subtracts an amount of time to a datetime object.
| Parameter | Description | 
|  ------  |  ------  | 
| diff `Required` | Amount to subtract. | 
| timeunit `Required` | Valid time units are nanos , micros , millis , seconds , minutes , hours , half_days , days , weeks , months , years , decades , centuries , millennia , and eras . | 


#### Example
```jinja2
{% set date = "2018-07-14T14:31:30+0530"|strtotime("yyyy-MM-dd'T'HH:mm:ssZ") %}
{{ date }}
{{ date|minus_time(2, 'months') }}
```

#### Output
```jinja2
2018-07-14 14:31:30
2018-05-14 14:31:30
```

