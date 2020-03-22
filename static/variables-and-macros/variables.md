# Variables
Variables are either a single word in an expression or an attribute of a dictionary. HubL uses Python-based data structures called dictionaries or **dicts** to store various sets of variables. For example, HubSpot uses a dictionary "content" to house many attributes that pertain to the content created with that template. For example the `content.absolute_url` prints the URL of the specific piece of content.

HubSpot has many predefined variables that can be used throughout your page, blog, and email templates. You can see a complete reference list of supported variables, [here](/docs/hubl/variables). You can also view the [developer info](/docs/developer-reference/debugging-and-errors#developer-info) when browsing any page from your portal.

In addition to printing the values of variables and dictionary attributes in a template, you can also define your own variables. You can store strings, booleans, integers, sequences, or create dictionaries within a single variable. Variables are defined within statement delimiters using the word "set". Once stored, variables can then be printed by stating the variable name as an expression. Below you can see various types of information stored in variables and then printed.

Variables should either be single words or use underscores for spaces (ie my\_variable). **HubL does not support hyphenated variable names.**

#### Example
```jinja2
{% set string_var = "This is a string value stored in a variable" %}
{{ string_var}}

{% set bool_var = True %}
{{ bool_var}}

{% set int_var = 53 %}
{{ int_var}}

{% set seq_var = ['Item 1', 'Item 2', 'Item 3'] %}
{{ seq_var}}

{% set var_one = "String 1" %}
{% set var_two = "String 2" %}
{% set sequence = [var_one,  var_two] %}
{{ sequence }}

{% set dict_var = {'name': 'Item Name', 'price': '$20', 'size':'XL'} %}
{{ dict_var.price }}
```

#### Output
```jinja2
This is a string value stored in a variable

True

53

[Item1, Item2, Item3]

[String 1, String 2]

$20
```

Each example above stores a different type of variable, with the final example storing two different variables in a sequence.

In addition to printing values, variables can be used in [if statements](/docs/hubl/if-statements), as [filter](/docs/hubl/filters) parameters, as [function](/docs/hubl/functions) parameters, as well as iterated through with [for loops](/docs/hubl/for-loops) (sequence variables only).

One common usage is to use variables to define common CSS values in your stylesheet. For example, if you have a color that you use over and over again throughout your CSS file. That way, if you need to change that color, you can change the variable value, and all references to that variable will be updated, the next time that you publish the file.

#### Example
```jinja2
<!-- defines variable and assigns HEX color -->
{% set primaryColor = '#F7761F' %} 
        
a {
    color: {{ primaryColor }}; {# prints variable HEX value #}
} 
```

