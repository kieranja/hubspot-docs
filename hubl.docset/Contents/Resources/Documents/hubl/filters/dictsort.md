# dictsort
Sort a dict and yield (key, value) pairs. Dictionaries are unsorted by default, but you can print a dictionary, sorted by key or value. The first parameter is a boolean to determine, whether or not the sorting is case sensitive. The second parameter determines whether to sort the dict by key or value. The example below prints a sorted contact dictionary, with all the known details about the contact.
| Parameter | Description | 
|  ------  |  ------  | 
| case_sensitive `Required` | Determines if sorting is case sensitive | 
| sort_by `Required` | Determines whether to sort by key or value | 


#### Example
```jinja2
{% for item in contact|dictsort(false, 'value') %}
    {{item}}
{% endfor %}
```

#### Output
```jinja2
A sorted contact dictionary
```

