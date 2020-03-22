# Expression tests
Expression tests are various boolean conditions that can be evaluated by using logical operators.
The `containing` expression test checks to see whether a list variable has a value in it.

#### Example
```jinja2
{% set numbers = [1, 2, 3] %}

{% if numbers is containing 2 %}
	Set contains 2!
{% endif %}
```

#### Output
```jinja2
Set contains 2!
```

The `containingall` expression test checks if a list variable contains all of the values of another list.

#### Example
```jinja2
{% set numbers = [1, 2, 3] %}

{% if numbers is containingall [2, 3] %}
	Set contains 2 and 3!
{% endif %}

{% if numbers is containingall [2, 4] %}
	Set contains 2 and 4!
{% endif %}
```

#### Output
```jinja2
Set contains 2 and 3!
```

The **defined** expression test checks to see whether a variable is defined within the context of the template. While you can use this expression test, writing an if statement without any operators will default to checking whether or not the variable is defined.

In the example below, a color module's color parameter is tested. If the color parameter had no value, the template would render a default black background color. If it is defined, it renders the background color set by the user.

#### Example
```jinja2
{% color "my_color" color='#930101', export_to_template_context=True %}
<style>
{% if widget_data.my_color.color is defined %}
body{
    background: {{ widget_data.my_color.color }};
}
{% else %}
body{
    background: #000;
}
{% endif %}
</style>
```

#### Output
```jinja2
<style>
 
body{
    background: #930101;
}
 
</style> 
```

The expression test **divisibleby** can be used to test whether an object is divisible by another number.

For example, below a for loop is created that iterates through a list of types of animals. Each type of animal gets printed in a div, and every 5th div has different inline styling applied (width:100%). This concept could be applied to a blog where different markup is rendered for a certain pattern of posts. To learn more about for loops and loop.index, [check out this article](https://designers.hubspot.com/docs/hubl/for-loops?hsLang=en).

#### Example
```jinja2
{% set animals = ['lions', 'tigers', 'bears', 'dogs', 'sharks'] %} 
{% for animal in animals %} 
    {% if loop.index is divisibleby 5 %}
    <div style="width:100%">{{animal}}</div> 
    {% else %}
    <div style="width:25%">{{animal}}</div>
    {% endif %}
{% endfor %}
```

#### Output
```jinja2
<div style="width:25%">lions</div> 
<div style="width:25%">tigers</div> 
<div style="width:25%">bears</div> 
<div style="width:25%">dogs</div> 
<div style="width:100%">sharks</div> 
```

The **equalto** expression test checks to see if a variable's value is equal to a constant or another variable. You can also use the operator == to do the same test.

In the example below, the width of the blog posts is adjusted based on the total number of posts in the loop. The example output assumes there were 4 posts in the blog.

#### Example
```jinja2
{% for content in contents %}
    {% if loop.length is equalto 2 %}
        <div style="width:50%;">Post content</div>
    {% elif loop.length is equalto 3 %}  
        <div style="width:33.333332%;">Post content</div>
    {% elif loop.length is equalto 4 %}  
        <div style="width:25%;">Post content</div>    
    {% else %}
        <div style="width:100%;>Post content</div>
    {% endif %}
{% endfor %}
```

#### Output
```jinja2
<div style="width:25%;">Post content</div>
<div style="width:25%;">Post content</div>
<div style="width:25%;">Post content</div>
<div style="width:25%;">Post content</div>
```

The **even** expression test checks to see whether a numeric variable is an even number.

The example below shows a simplified blog listing loop, where if the current iteration of the loop is even, a class of even-post is assigned to the post item div. Otherwise, a class of odd-post is assigned.

#### Example
```jinja2
{% for content in contents %}
   {% if loop.index is even %}
        <div class="post-item even-post">Post content</div>
    {% else %}
        <div class="post-item odd-post">Post content</div>
    {% endif %}
{% endfor %} 
```

#### Output
```jinja2
<div class="post-item odd-post">Post content</div>
<div class="post-item even-post">Post content</div>
<div class="post-item odd-post">Post content</div>
<div class="post-item even-post">Post content</div>
```

Checks to see whether a variable is **iterable** and can be looped through.

This example checks a variable called "jobs" to see if it can be iterated through. Since the variable contains a list of jobs, the if statement would evaluate to true, and the loop would run. If the variable had contained a single value, the [if statement](http://developers-web1-hubspot.sites.hubspot.com/docs/hubl/if-statements?hsLang=en) would print that value with different markup instead. [You can learn more about for loops here](https://designers.hubspot.com/docs/hubl/for-loops?hsLang=en).

#### Example
```jinja2
{% set jobs = ['Accountant', 'Developer', 'Manager', 'Marketing', 'Support'] %} 

{% if jobs is iterable %}
<h3>Available positions</h3>
<ul>
{% for job in jobs %}
    <li>{{ job }}</li>
{% endfor %}
</ul>
{% else %}
<h3>Available position</h3>
<div class="single-position">{{ jobs }}</div>
{% endif %}
```

#### Output
```jinja2
<h3>Available positions</h3>
<ul>
    <li>Accountant</li>
    <li>Developer</li>
    <li>Manager</li>
    <li>Marketing</li>
    <li>Support</li>
</ul>
```

The **lower** expression test evaluates to true when a string is lowercase.

The example below uses an [unless statement](http://developers-web1-hubspot.sites.hubspot.com/docs/hubl/if-statements?hsLang=en#unless-statements) and a lower filter to ensure that a string of text entered into a text module is always lowercase.

#### Example
```jinja2
{% module "my_text" path="@hubspot/text" label='Enter text', value='Some TEXT that should be Lowercase', export_to_template_context=True %}

{% unless widget_data.my_text.value is lower %}
{{ widget_data.my_text.value|lower }}
{% endunless %}
```

#### Output
```jinja2
some text that should be lowercase
```

The **mapping** expression test checks to see whether or not an object is a dict (dictionary).

The example below is checking to see if the contact object is a dictionary, in which case it is.

#### Example
```jinja2
{% if contact is mapping %}
This object is a dictionary.
{% else %}
This object is not a dictionary.
{% endif %}
```

#### Output
```jinja2
This object is a dictionary.
```

The **none** expression test checks to see whether a variable has a null value.

#### Example
```jinja2
{% module "user_email" path="@hubspot/text" label='Enter user email', value='example@hubspot.com', export_to_template_context=True %}
{% unless widget_data.user_email.value is none %}
{{ widget_data.user_email.value }}
{% endunless %}
```

#### Output
```jinja2
example@hubspot.com
```

The **number** expression test checks to see whether or not the value of a variable is a number.

The example below checks a variable to see whether or not it is a variable, and if so it converts it into millions.

#### Example
```jinja2
{% set my_var = 40 %}
{% if my_var is number %}
{{ my_var * 1000000 }}
{% else %}
my_var is not a number.
{% endif %}
```

#### Output
```jinja2
40000000
```

The **odd** expression test checks to see whether a numeric variable is an odd number.

Below is the same example as the inverse even expression test previously described.

#### Example
```jinja2
{% for content in contents %}
   {% if loop.index is odd %}
        <div class="post-item odd-post">Post content</div>
    {% else %}
        <div class="post-item even-post">Post content</div>
    {% endif %}
{% endfor %} 
```

#### Output
```jinja2
<div class="post-item odd-post">Post content</div>
<div class="post-item even-post">Post content</div>
<div class="post-item odd-post">Post content</div>
<div class="post-item even-post">Post content</div>
```

The **sameas** expression test checks to see whether or not two variables have the same value.

The example below sets two variables and then checks to see whether or not they are the same.

#### Example
```jinja2
{% set var_one = True %}
{% set var_two = True %}
{% if var_one is sameas var_two  %}
The variables values are the same.
{% else %}
The variables values are different.
{% endif %}
```

#### Output
```jinja2
The variables values are the same.
```

The **sequence** expression test is similar to the **iterable** test, in that it checks to see whether or not a variable is a sequence.

The example below checks whether a variable is a sequence and then iterates through that sequence of musical genres.

#### Example
```jinja2
{% set genres = ['Pop', 'Rock', 'Disco', 'Funk', 'Folk', 'Metal', 'Jazz', 'Country', 'Hip-Hop', 'Classical', 'Soul', 'Electronica' ] %} 
{% if genres is sequence %}
<h3>Favorite genres</h3>
<ul>
{% for genre in genres %}
    <li>{{ genre }}</li>
{% endfor %}
</ul>
{% else %}
<h3>Favorite genre:</h3>
    <div class='single-genre'>{{ genres }}</div>
{% endif %}
```

#### Output
```jinja2
<ul>
    <li>Pop</li>
    <li>Rock</li>
    <li>Disco</li>
    <li>Funk</li>
    <li>Folk</li>
    <li>Metal</li>
    <li>Jazz</li>
    <li>Country</li>
    <li>Hip-Hop</li>
    <li>Classical</li>
    <li>Soul</li>
    <li>Electronica</li>
</ul>
```

The **string** expression test checks to see whether the value stored in a variable is text.

The example below checks whether or not a variable is a string, and if so it applies a title filter to change the capitalization.

#### Example
```jinja2
{% set my_var = "title of section" %}
{% if my_var is string %}
{{ my_var|title }}
{% else %}
my_var is not a string
{% endif %}
```

#### Output
```jinja2
Title Of Section
```

This test checks to see if a string is contained within another string. This expression test is used in conjunction with the "is" operator.

#### Example
```jinja2
{% if content.domain is string_containing ".es" %}
Markup that will only render on content hosted on .es domains
{% elif content.domain is string_containing ".jp" %}
Markup that will only render on content hosted on .jp domains
{% else %}
Markup that will render on all other domains
{% endif %}
```

#### Output
```jinja2
Markup that will render on all other domains
```

This expression test checks to see if a string starts with a particular string. It is used in conjunction with the "is" operator.

#### Example
```jinja2
{% if content.slug is string_startingwith "es/" %}
Markup that will only render on content hosted in a /es/ subdirectory
{% elif content.slug is string_startingwith "jp/" %}
Markup that will only render on content hosted in a /jp/ subdirectory
{% else %}
Markup that will render on all subdirectories
{% endif %}
```

#### Output
```jinja2
Markup that will render on all subdirectories
```

The **truthy** expression test checks to see whether an expression evaluates to True.

The example below uses a boolean checkbox module to display an alert message.

#### Example
```jinja2
{% boolean "check_box" label='Show alert', value=True, export_to_template_context=True %}

{% if widget_data.check_box.value is truthy %}
<div class='alert'>Danger!</div>
{% endif %}
```

#### Output
```jinja2
<div class='alert'>Danger!</div>
```

The **undefined** expression test checks to see whether a variable is undefined in the context of the template. This test is different from none, in that undefined will be true when the variable is present but has no value; whereas, none will be true when the variable has a null value.

The example below checks a template for the existence of the variable "my\_var".

#### Example
```jinja2
{% if my_var is undefined %}
A variable named "my_var" does not exist on this template.
{% else %}
{{ my_var }}
{% endif %}
```

#### Output
```jinja2
A variable named "my_var" does not exist on this template.
```

The **upper** expression test evaluates to true when a string is all uppercase. Below is an inverse example of the lower expression test above.

#### Example
```jinja2
{% module "my_text" path="@hubspot/text" label='Enter text', value='Some TEXT that should be Uppercase', export_to_template_context=True %}

{% unless widget_data.my_text.value is upper %}
{{ widget_data.my_text.value|upper }}
{% endunless %}
```

#### Output
```jinja2
SOME TEXT THAT SHOULD BE UPPERCASE
```

The **within** expression tests checks if a variable is within a list.

#### Example
```jinja2
{% set numbers = [1, 2, 3] %}

{% if 2 is within numbers %}
	2 is in the list!
{% endif %}

{% if 4 is within numbers %}
	4 is in the list!
{% endif %}
```

#### Output
```jinja2
2 is in the list!
```

