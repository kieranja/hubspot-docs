# map
Applies a filter on a sequence of objects or looks up an attribute. This is useful when dealing with lists of objects but you are really only interested in a certain value of it.

The basic usage is mapping on an attribute. For example, if you want to use conditional logic to check if a value is present in a particular attribute of a dict. Alternatively, you can let it invoke a filter by passing the name of the filter and the arguments afterwards.
| Parameter | Description | 
|  ------  |  ------  | 
| attribute | Attribute to return in the sequence of objects. | 
| filter | Filter to apply to the sequence of objects. | 


#### Example
```jinja2
{% set seq = ['item1', 'item2', 'item3'] %}
{{ seq|map('upper') }}
{{ content|map('currentState')}}
```

#### Output
```jinja2
[ITEM1, ITEM2, ITEM3]
DRAFT
```

