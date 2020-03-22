# Loop properties
As a loop iterates, you can use [conditional logic](/docs/hubl/if-statements) to define the loop's behavior. The variable property `loop.index` keeps a count of the current number of the iterations of the loop. There are several other loop variable properties that count the iterations in different ways. These properties are described below:
| Variable | Description | 
|  ------  |  ------  | 
| loop.cycle | A helper function to cycle between a list of sequences. See the explanation below. | 
| loop.depth | Indicates how deep in deep in a recursive loop the rendering currently is. Starts at level 1 | 
| loop.depth0 | Indicates how deep in deep in a recursive loop the rendering currently is. Starts at level 0 | 
| loop.first | This variable evaluates to true, if it is the first iteration of the loop. | 
| loop.index | The current iteration of the loop. This variable starts counting at 1. | 
| loop.index0 | The current iteration of the loop. This variable starts counting at 0. | 
| loop.last | This variable evaluates to true, if it is the last iteration of the loop. | 
| loop.length | The number of items in the sequence. | 
| loop.revindex | The number of iterations from the end of the loop. Counting down to 1. | 
| loop.revindex0 | The number of iterations from the end of the loop. Counting down to 1. | 

Below are some examples that use different loop variables. The following basic example uses `loop.index` to keep a count that is printed with each iteration.

#### Example
```jinja2
{% set loopy = ['Content', 'Social', 'Contacts', 'Reports'] %}
{% for app in loopy %}
    {{ loop.index }}. {{app}} <br>
{% endfor %}
```

#### Output
```jinja2
1. Content <br>
2. Social <br>
3. Contacts <br>
4. Reports <br>
```

The next example uses conditional logic to check whether the length of the loop is `divisibleby` certain numbers. It then renders the width of the post-item div accordingly. The example uses the standard blog post loop and assumes that there are 6 posts in the loop.

#### Example
```jinja2
{% for content in contents %}
{% if loop.length is divisibleby 4 %}
<div style="width:25%">Post content</div>

{% elif loop.length is divisibleby 3 %}
<div style="width:33.33332%">Post content</div>

{% else %}
<div style="width:50%">Post content</div>

{% endif %}
{% endfor %}
```

#### Output
```jinja2
<div style="width:33.33332%">Post content</div>
<div style="width:33.33332%">Post content</div>
<div style="width:33.33332%">Post content</div>
<div style="width:33.33332%">Post content</div>
<div style="width:33.33332%">Post content</div>
<div style="width:33.33332%">Post content</div>
<div style="width:33.33332%">Post content</div>
```

