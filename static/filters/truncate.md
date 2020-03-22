# truncate
Cuts off text after a certain number of characters. The default is 255. Please note that HTML characters are included in this count. The length is specified with the first parameter which defaults to 255. If the second parameter is true the filter will cut the text at length. Otherwise it will discard the last word. If the text was in fact truncated it will append an ellipsis sign ("..."). If you want a different ellipsis sign than "..." you can specify it using the third parameter.
| Parameter | Description | 
|  ------  |  ------  | 
| number_of_characters `Required` | Number of characters to truncate the text by. Default is 255. | 
| breakword `Optional` | Boolean value. If true, the filter will cut the text at length. If false, it will discard the last wrod.  | 
| end `Optional` | Override the default '...' trailing characters after the truncation. | 


#### Example
```jinja2
{{ "I only want to show the first sentence. Not the second."|truncate(40) }} 
{{ "I only want to show the first sentence. Not the second."|truncate(35, True, '..........') }}
```

#### Output
```jinja2
I only want to show the first sentence.
I only want to show the first sente.......... 
```

