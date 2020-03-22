# Textarea
A textarea is similar to a text module in that it allows users to enter plain text, but it gives them a larger area to work in the content editor. This module does not support HTML. If you want to use directly within a predefined wrapping tag, add the **no\_wrapper=true** parameter.

#### Example
```jinja2
{% textarea "my_textarea" %}
{% textarea "my_textarea" label='Enter plain text block', value='Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean a urna quis lacus vehicula rutrum.', no_wrapper=True %}
```

#### Output
```jinja2
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean a urna quis lacus vehicula rutrum.
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| value | String | Sets the default text of the textarea. | 
           
           | 

