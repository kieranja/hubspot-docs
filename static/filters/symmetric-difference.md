# symmetric_difference
This filter returns the symmetric difference of two sets or lists. The list returned from the filter contains all unique elements that are in the first list but not the second, or are in the second list but not the first
| Parameter | Description | 
|  ------  |  ------  | 
| list `Required` | The second list to compare to for use in finding the symmetric difference with the original list. | 


#### Example
```jinja2
{{ [1, 2, 3]|symmetric_difference([2, 3, 4, 5]) }}
```

#### Output
```jinja2
[1, 4, 5]
```

