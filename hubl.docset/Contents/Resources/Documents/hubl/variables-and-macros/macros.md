# Macros
HubL macros allow you to print multiple statements with a dynamic value. For example, if there is a block of code that you find yourself writing over and over again, a macro may be a good solution, because it will print the code block while swapping out certain arguments that you pass it.

The macro is defined, named, and given arguments within a HubL statement. The macro is then called in a statement that passes its dynamic values, which prints the final code block with the dynamic arguments. The basic syntax of a macro is as follows:

#### Example
```jinja2
{% macro name_of_macro(argument_name, argument_name2)  %}
    {{ argument_name }}
    {{ argument_name2 }}
{% endmacro %}
{{ name_of_macro('value to pass to argument 1', 'value to pass to argument 2')  }}
```

If your macro is returning whitespace in the form of new lines, you can strip whitespace in templates by hand. If you add a minus sign (`-`) to the start or end of a block, a comment, or a variable expression, the whitespaces before or after that block will be removed.

#### Example
```jinja2
{% macro name_of_macro(argument_name, argument_name2) -%}
    {{ argument_name }}
    {{ argument_name2 }}
{%- endmacro %}
```

Below shows a practical application of a macro to print a CSS3 properties with the various vendor prefixes, with a dynamic value. This allows you to print 5 lines of code with a single macro tag.

#### Example
```jinja2
{% macro trans(value) %} 
-webkit-transition: {{value}};
-moz-transition: {{value}};
-o-transition: {{value}};
-ms-transition: {{value}};
transition: {{value}};
{% endmacro %}
 

a {
    {{ trans('all .2s ease-in-out') }}
}
```

