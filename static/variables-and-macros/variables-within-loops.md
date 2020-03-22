# Variables within loops
You can call variables that are defined outside of a loop, from within a loop, but not the other way around.

You can also use functions in order to mutate objects for settings values on dict's or performing list operations. The following example is using the [`.update` list operation](/docs/hubl/functions#update):

#### Example
```jinja2
{% set obj = {val : 0} %}
{% for i in range(0, 10) %}
  {% do obj.update('val', obj.val + i) %}
{% endfor %}
{{ obj.val }}
```

