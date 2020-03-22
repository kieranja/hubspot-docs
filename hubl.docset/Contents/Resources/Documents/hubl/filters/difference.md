# difference
This filter returns the difference of two sets or lists. The list returned from the filter contains all unique elements that are in the first list but not the second.
| Parameter | Description | 
|  ------  |  ------  | 
| list `Required` | The second list to compare to for use in finding differences from the original list. | 


#### Example
```jinja2
{{ [1, 2, 3]|difference([2, 3, 4, 5]) }}
```

#### Output
```jinja2
[1]
```

