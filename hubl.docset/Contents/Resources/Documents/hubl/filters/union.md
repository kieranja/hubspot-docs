# union
This filter returns the union of two sets or lists. The list returned from the filter contains all unique elements that are in either list.
| Parameter | Description | 
|  ------  |  ------  | 
| list `Required` | The second list to union with the original list. | 


#### Example
```jinja2
{{ [1, 2, 3]|union([2, 3, 4, 5]) }}
```

#### Output
```jinja2
[1, 2, 3, 4, 5]
```

