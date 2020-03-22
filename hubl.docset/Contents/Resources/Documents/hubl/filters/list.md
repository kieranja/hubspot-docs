# list
Convert the number values into a list. If it was a string the returned list will be a list of characters. To add strings to a sequence, simply add them to the string variables to the sequence delimiters \[ \].

#### Example
```jinja2
{% set one = 1 %}
{% set two = 2 %}
{% set three = 3 %}
{% set four = ["four"] %}
{% set list_num = one|list + two|list + three|list + four|list %}
{{ list_num }}
```

#### Output
```jinja2
[1,2,3]
```

