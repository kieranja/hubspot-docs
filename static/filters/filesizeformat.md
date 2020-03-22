# filesizeformat
Format the value like a ‘human-readable’ file size (i.e. 13 kB, 4.1 MB, 102 Bytes, etc). Per default decimal prefixes are used (Mega, Giga, etc.), if the parameter is set to True the binary prefixes are used (Mebi, Gibi).
| Parameter | Description | 
|  ------  |  ------  | 
| boolean `Optional` | If set to true, binary prefixes are used such as Mebi & Gibi. | 


#### Example
```jinja2
{% set bytes = 100000 %} 
{{ bytes|filesizeformat }}
```

#### Output
```jinja2
100.0 KB
```

