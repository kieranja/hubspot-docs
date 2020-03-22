# Inline if statements
HubL supports inline `if` statements. These can be used to write conditional logic in a concise manner with [operators and expression tests](/docs/hubl/operators-and-expression-tests).

#### Example
```jinja2
{% set color = "Blue" if is_blue is truthy else "Red" %}     // color == "blue"  

{{ "Blue" if is_blue is truthy else "Red" }}     // "Blue"

{% set dl = true %}
<a href="http://example.com/some.pdf" {{"download" if dl }} >Download PDF</a>
```

