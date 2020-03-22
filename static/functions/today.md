# today
Returns the start of today (12:00am). Optionally you can add a parameter to change the timezone from the default UTC.

#### Example
```jinja2
{{ today() }}
{{ today("America/New_York") }}
{{ unixtimestamp(today("America/New_York").plusDays(1)) }}
```

#### Output
```jinja2
2018-10-23T00:00Z
2018-10-23T00:00-04:00[America/New_York]
1540353600000
```

