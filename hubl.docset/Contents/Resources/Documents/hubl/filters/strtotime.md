# strtotime
Converts a datetime string and a datetime format into a datetime object.
| Parameter | Description | 
|  ------  |  ------  | 
| datetimeFormat `Required` | Date and time patterns. | 


#### Example
```jinja2
{{ "2018-07-14T14:31:30+0530"|strtotime("yyyy-MM-dd'T'HH:mm:ssZ")|unixtimestamp }}

```

#### Output
```jinja2
1531558890000
```

