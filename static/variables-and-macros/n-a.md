# 
HubL uses variables to store and output values to the template. Variables can be used in template logic or iterated through with for loops. In addition to variables, macros are another useful tool for printing repetitive yet dynamic sections of code throughout your templates.

Variables are expressions delimited by `}}`. The basic syntax of variables is as follows:

#### Example
```jinja2
// variables
{{ variable }}
{{ dict.attribute }}
```

