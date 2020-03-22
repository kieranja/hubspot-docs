# wordwrap
Causes words to wrap at a given character count. This works best in a &lt;pre&gt; because HubSpot strips whitespace by default.
| Parameter | Description | 
|  ------  |  ------  | 
| character_count `Required` | Number of characters to wrap the content at. | 


#### Example
```jinja2
{% set wrap_text = "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam efficitur, ipsum non sagittis euismod, ex risus rhoncus lectus, vel maximus leo enim sit amet dui. Ut laoreet ultricies quam at fermentum." %} 
{{ wrap_text|wordwrap(10) }}
```

#### Output
```jinja2
Lorem
ipsum
dolor sit
amet,
consectetur
adipiscing
elit.
Etiam
efficitur,
ipsum non
sagittis
euismod,
ex risus
rhoncus
lectus,
vel
maximus
leo enim
sit amet
dui. Ut
laoreet
ultricies
quam at
fermentum.
```

