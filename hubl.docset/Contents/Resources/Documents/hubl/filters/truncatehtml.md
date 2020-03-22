# truncatehtml
Truncates a given string, respecting html markup (i.e. will properly close all nested tags). This will prevent a tag from being remaining open after truncation. HTML characters do not count towards the character total. This filter has a length parameter and a truncation symbol parameter. There is a third boolean parameter that specifies whether words will be broken at length. This parameter is false by default in order to preserve the length of words.
| Parameter | Description | 
|  ------  |  ------  | 
| number_of_characters `Required` | Number of characters to truncate the text by. Default is 255. | 
| end `Optional` | Override the default '...' trailing characters after the truncation. | 
| breakword `Optional` | Boolean value. If true, the filter will cut the text at length. If false, it will discard the last wrod.  | 


#### Example
```jinja2
{% set html_text = "<p>I want to truncate this text without breaking my HTML<p>" %} 
{{ html_text|truncatehtml(28, '..' , false) }}
```

#### Output
```jinja2
<p>I want to truncate this..</p>
```

