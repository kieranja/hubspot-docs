# datetimeformat
The `datetimeformat` function works just like the [datetimeformat filter](/docs/hubl/filters#datetimeformat), but uses function syntax instead of filter syntax. It uses the same parameters to format the date. [See the complete list of formatting parameters.](/docs/hubl/filters#widget_1582313600888)

#### Example
```jinja2
{{ datetimeformat(content.publish_date_local_time, '%B %e, %Y') }} 
```

#### Output
```jinja2
May 13, 2015
```

