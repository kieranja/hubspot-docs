# capitalize
Capitalize the first letter of a variable value. The first character will be uppercase, all others letters will retain their original case.

#### Example
```jinja2
{% set sentence = "the first letter of a sentence should always be capitalized." %} 
{{ sentence|capitalize }}
```

#### Output
```jinja2
The first letter of a sentence should always be capitalized.
```

