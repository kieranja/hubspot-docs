# Operators
| Symbol | Description | 
|  ------  |  ------  | 
| + | Adds two objects together. You will generally use this for the addition of numbers. If you are trying to concatenate strings of lists, you should use ~ instead. | 
| - | Subtracts one number from another. | 
| / | Divides numbers | 
| % | Returns the remainder from dividing numbers | 
| // | Divide two numbers and return the truncated integer result. Example: {{ 20 // 7 }} is 2 | 
| * | Multiplies numbers | 
| ** | Raise the left operand to the power of the right operand | 


#### Example
```jinja2
{% set my_num = 11 %}
{% set my_number = 2 %}
    
{{ my_num + my_number }}<br/>  <!-- 11 + 2 = 13 -->
{{ my_num - my_number }}<br/>  <!-- 11 - 2 = 9 -->
{{ my_num / my_number }}<br/>  <!-- 11 / 2 = 5.5 -->
{{ my_num % my_number }}<br/>  <!-- 11 % 2 = 1 -->
{{ my_num // my_number }}<br/> <!-- 11 // 2 = 5 -->
{{ my_num * my_number }}<br/>  <!-- 11 * 2 = 22 -->
{{ my_num ** my_number }}<br/> <!-- 11 ** 2 = 121 -->
```

#### Output
```jinja2
13
9
5.5
1
5
22
121
```

| Symbol | Description | 
|  ------  |  ------  | 
| == | Equal to. Evaluates to true if two objects are equal.  | 
| != | Not equal to. Evaluates to true if two objects are not equal. | 
| > | Greater than. Evaluates to true if the left-hand side is greater than the right-hand side. | 
| >= | Greater than or equal to. Evaluates to true if the left-hand side is greater or equal to the right-hand side. | 
| < | Less than. Evaluates to true if the left-hand side is lower than the right-hand side. | 
| <= | Less than or equal to. Evaluates to true if the left-hand side is lower or equal to the right-hand side. | 


#### Example
```jinja2
{% set my_num = 11 %}
{% set my_number = 2 %}

{{ my_num == my_number }}<br/>  <!-- false -->
{{ my_num != my_number }}<br/>  <!-- true -->
{{ my_num > my_number }}<br/>   <!-- true -->
{{ my_num >= my_number }}<br/>  <!-- true -->
{{ my_num < my_number }}<br/>   <!-- false -->
{{ my_num <= my_number }}<br/>  <!-- false -->
```

#### Output
```jinja2
false
true
true
true
false
false
```

Logical operators allow you to combine multiple expressions into single statements.
| Symbol | Description | 
|  ------  |  ------  | 
| and | Return true if the left and the right operand are true. | 
| or | Return true if the left or the right operand is true. | 
| not | Negates a statement and is used in conjunction with is. See examples below. | 
| (expr) | Group an expression for the order of operations. For example, (10 - 2) * variable. | 
| ?: | The ternary operator accepts 3 arguments (expression, true condition, false condition). Evaluates an expression and returns the corresponding condition. | 

Below are other important HubL operators that can be used to perform various tasks.
| Symbol | Description | 
|  ------  |  ------  | 
| in | Checks to see if a value is in a sequence. | 
| is | Performs an expression test. | 
| | | Applies a filter. | 
| ~ | Concatenates values. | 

