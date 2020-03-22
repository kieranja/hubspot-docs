# string
Converts a different variable type to a string. In the example below, a integer is converted into a string (pprint is used to confirm the change in variable type).

#### Example
```jinja2
{% set number_to_string = 45 %} 
{{ number_to_string|string|pprint }}
```

#### Output
```jinja2
(String: 45) 
```

