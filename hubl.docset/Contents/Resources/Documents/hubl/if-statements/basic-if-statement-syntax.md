# Basic if statement syntax
HubL uses if statements to help define the logic of a template. The syntax of HubL if statements is very similar to conditional logic in Python. `if` statements are wrapped in [statement delimiters](/docs/hubl/variables-macros-syntax), starting with an opening `if` statement and ending with an `endif`.

The example below provides the basic syntax of an if statement, where "condition" would be replaced with the boolean rule that you were going to evaluate as being true of false.

#### Example
```jinja2
{% if condition %}
	If the condition is true print this to template.
{% endif %}
```

Now that you have seen the basic syntax, let's look at a few actual examples of basic if statements. The next examples below show if statements that check to see whether or not a HubL module with the name `my_module` and whether a variable named `my_module` are present on a template. Notice that without any operators, the if statement will evaluate whether or not the module is defined in the context of the template.

#### Example
```jinja2
{% module "my_module" path="@hubspot/rich_text", label='My rich text module', html='Default module text' export_to_template_context=true %}

{% if widget_data.my_module %}
	A module named "my_module" is defined in this template.
{% endif %}


{% set my_variable = "A string value for my variable" %}    
{% if my_variable %}
	The variable named my_variable is defined in this template.
{% endif %}
```

Notice that when evaluating the HubL module, the module name is left in quotes within the `if` statement and while testing the variable no quotes are used around the variable name. In both examples above, the module and the variable exist in the template, so the statements evaluate to print the markup. Please note that these examples are only testing whether the module and variable are defined, not whether or not they have a value.

Now let's look at an `if` statement that evaluates whether a module has a value, instead of evaluating whether it exists on the template. To do this, we need to use the [export\_to\_template\_context](/docs/building-blocks/modules/export-to-template-context) parameter. In the example below, if the text module is valued in the content editor, the markup would print. If the module's text field were cleared, no markup would render. If you are working within custom modules, there is a simplified `widget.widget_name` syntax outlined in the [example here](/docs/building-blocks/modules/configuration).

#### Example
```jinja2
{% module "product_names" path="@hubspot/text", label='Enter the product names that you would like to render the coupon ad for', value='all of our products', export_to_template_context=True %}

{% if widget_data.product_names.value %}
<div class="coupon-ad">
<h3>For a limited time, get 50% off {{ widget_data.product_names.value}}! </h3>
</div>
{% endif %}
        
```

#### Output
```jinja2
<div class="coupon-ad">
<h3>For a limited time get 50% off all of our products! </h3>
</div>  
```

