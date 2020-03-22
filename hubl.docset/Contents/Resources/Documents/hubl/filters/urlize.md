# urlize
Converts URLs in plain text into clickable links. If you pass the filter an additional integer it will shorten the urls to that number. The second parameter is a boolean that dictates whether the link is rel="no follow". The final parameter lets you specify whether the link will open in a new tab.
| Parameter | Description | 
|  ------  |  ------  | 
| shorten_text `Optional` | Integer that will shorten the urls to desired number. | 
| no_follow `Optional` | Boolean value to indicate whether the link is rel="no follow". | 
| target='_blank' `Optional` | Specifies whether the link will open in a new tab. | 


#### Example
```jinja2
{{ "http://hubspot.com/"|urlize }}
{{ "http://hubspot.com/"|urlize(10,true) }}
{{ "http://hubspot.com/"|urlize('',true) }}
{{ "http://hubspot.com/"|urlize('',false,target='_blank') }}
```

#### Output
```jinja2
<a href="//hubspot.com/">http://hubspot.com/</a>
<a href="//hubspot.com/" rel="nofollow">http://...</a>
<a href="//hubspot.com/" rel="nofollow">http://hubspot.com/</a>
<a href="//hubspot.com/" target="_blank">http://hubspot.com/</a>
```

