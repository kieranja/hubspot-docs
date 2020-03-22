# update
Updates the dict with the elements from another dict object or from an iterable of key/value pairs.

#### Example
```jinja2
{% set dict_var = {'authorName': 'Douglas Judy', 'authorTitle': 'Mastermind' } %}
{% set test = dict_var.update({'authorFriend': 'Jake'}) %}
{% set test = dict_var.update({'authorLocation': 'unknown'}) %}
{{ dict_var }}
```

#### Output
```jinja2
{authorName=Douglas Judy, authorTitle=Mastermind, authorFriend=Jake, authorLocation=unknown}
```

