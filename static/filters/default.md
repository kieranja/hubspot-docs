# default
If the value is undefined it will return the first parameter, otherwise the value of the variable will be printed. If you want to use default with variables that evaluate to false, you have to set the second parameter to **true**. The first example below would print the message if the variable is not defined. The second example applied the filter to an empty string, which is not undefined, but it prints a message due to the second parameter.
| Parameter | Description | 
|  ------  |  ------  | 
| default_variable `Required` | Value to return if the variable is undefined. If the variable is defined, the value of the variable will be returned instead. | 
| boolean `Optional` | Returns the default_value if the variable is an empty string | 


#### Example
```jinja2
{{ my_variable|default('my_variable is not defined') }} 
{{ ''|default('the string was empty', true) }}
```

#### Output
```jinja2
my_variable is not defined
the string was empty
```

