# truncate
The truncate function works just like the [truncate filter](/docs/hubl/filters#truncate), but uses function syntax instead of filter syntax. The first parameter specifies the string. The second parameter specifies the length at which to truncate. The final parameter specifies the characters to add when the truncation occurs.

#### Example
```jinja2
{{ truncate('string to truncate at a certain length', 19, end='...') }} 
```

#### Output
```jinja2
string to truncate ...
```

