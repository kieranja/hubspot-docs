# intersect
This filter returns the intersection of two sets or lists. The list returned from the filter contains all unique elements that are contained in both lists.
| Parameter | Description | 
|  ------  |  ------  | 
| list `Required` | The second list to compare to for use in finding where the list intersects with the original list. | 


#### Example
```jinja2
{{ [1, 2, 3]|intersect([2, 3, 4, 5]) }}
```

#### Output
```jinja2
[2, 3]
```

