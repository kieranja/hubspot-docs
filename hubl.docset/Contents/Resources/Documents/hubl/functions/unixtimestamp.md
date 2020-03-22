# unixtimestamp
This function returns a unix timestamp. By default it will return the timestamp of now or you can optionally supply a datetime object to be converted to a unix timestamp.

#### Example
```jinja2
{{ unixtimestamp() }}
{{ unixtimestamp(d) }}

```

#### Output
```jinja2
1582822133978
1565983117868
```

