# Using elif and else
`if` statements can be made more sophisticated with additional conditional statements or with a rule that executes when the condition or conditions are false. `elif` statements allow you to add additional conditions to your logic that will be evaluated after the previous condition. **`else`** statements define a rule that executes when all other conditions are false. You can have an unlimited number of `elif` statements within a single if statement, but only one `else` statement.

Below is the basic syntax example of if statement that uses the [&lt;= operator](/docs/hubl/operators-and-expression-tests#comparison) to check the value of a variable. In this example, the template would print: "Variable named number is less than or equal to 6."

#### Example
```jinja2
{% set number = 5 %}

{% if number <= 2 %}
	Variable named number is less than or equal to 2.
{% elif number <= 4 %}
	Variable named number is less than or equal to 4.
{% elif number <= 6 %}
	Variable named number is less than or equal to 6.
{% else %}
	Variable named number is greater than 6.
{% endif %}
```

Below is one more example that uses a choice module to render different headings for a careers page, based on the department chosen by the user. The example uses the [== operator](/docs/hubl/operators-and-expression-tests#comparison), to check for certain predefined values in the choice module.

#### Example
```jinja2
{% choice "department" label='Choose department', value='Marketing', choices='Marketing, Sales, Dev, Services' export_to_template_context=True %}
        
{% if widget_data.department.value == 'Marketing' %}

<h3>Want to join our amazing Marketing team?!</h3>
<h4>We have exciting career opportunities on the {{ widget_data.department.value }} team.</h4>

{% elif widget_data.department.value == 'Sales' %}

<h3>Are you a Sales superstar?</h3>
<h4>We have exciting career opportunities on the {{ widget_data.department.value }} team.</h4>        
        
{% elif widget_data.department.value == 'Dev' %}
        
<h3>Do you love to ship code?</h3>
<h4>We have exciting career opportunities on the {{ widget_data.department.value }} team.</h4>
        
{% else %}
        
<h3>Want to work with our awesome customers?</h3>
<h4>We have exciting career opportunities on the {{ widget_data.department.value }} team.</h4>
        
{% endif %}
```

