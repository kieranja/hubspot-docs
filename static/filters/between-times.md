# between_times
Calculates the time between two datetime objects in a specified time unit.
| Parameter | Description | 
|  ------  |  ------  | 
| end `Required` | The ending datetime object | 
| timeunit `Required` | Valid time units are nanos , micros , millis , seconds , minutes , hours , half_days , days , weeks , months , years , decades , centuries , millennia , and eras . | 


#### Example
```jinja2
{% set begin = "2018-07-14T14:31:30+0530"|strtotime("yyyy-MM-dd'T'HH:mm:ssZ") %}
{% set end = "2018-07-20T14:31:30+0530"|strtotime("yyyy-MM-dd'T'HH:mm:ssZ") %}
{{ begin|between_times(end, 'days') }}
```

#### Output
```jinja2
6
```

