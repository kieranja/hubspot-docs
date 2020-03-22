# Ternary operators
It is also possible to use ternary operators to quickly write conditional logic with [operators and expression tests](/docs/hubl/operators-and-expression-tests#logical).

#### Example
```jinja2
// If the variable is_blue is true, output "blue", otherwise output"red"
{{ is_blue is truthy ? "blue" : "red" }}

// Set the variable is_red to false if is_blue is true, otherwise set to true
{% set is_red = is_blue is truthy ? false : true %}
```

