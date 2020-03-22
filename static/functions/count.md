# count
Returns the number of times a variable exists in a list.

#### Example
```jinja2
{% set attendees = ["Jack","Jon","Jerry","Jessica"] %}
{% set jon_count = attendees.count("Jon") %}
There are {{jon_count}} Jon's in the list.
<p>After append:</p>
{% do attendees.append("Jon") %}
{% set jon_count_after_append = attendees.count("Jon") %}
There are now {{jon_count_after_append}} Jon's in the list.
```

#### Output
```jinja2
There are 1 Jon's in the list.
<p>After append:</p>

There are now 2 Jon's in the list.
```

