# 
For loops can be used in HubL to iterate through sequences of objects. They will most commonly be used with rendering [blog content](/docs/building-blocks/templates/blog-template-markup) in a listing format, but they can also be used to sort through other sequence variables.

For loops begin with a `{% for %}` statement and end with an ` {% endfor %} ` statement. Within the `{% for %}` statement a single sequence item is named followed by `in` and then the name of the sequence. The code between the opening and closing `for` statements is printed with each iteration, and generally includes the printed variable of the individual sequence item. Below is the basic syntax of a for loop:

#### Example
```jinja2
{% for item in items %}
	{{ item }}
{% endfor %}
```

Below is a basic example that shows how to print a sequence of variable values into a list.

#### Example
```jinja2
{% set languages = ['HTML', 'CSS', 'Javascript', 'Python', 'Ruby', 'PHP,', 'Java'] %}

<h1>Languages</h1>;
<ul>
    {% for language in languages %}
    <li>{{ language }}</li>
    {% endfor %}
</ul>
```

#### Output
```jinja2
<h1>Languages</h1>
<ul>
    <li>HTML</li>
    <li>CSS</li>
    <li>Javascript</li>
    <li>Python</li>
    <li>Ruby</li>
    <li>PHP</li>
    <li>Java</li>
</ul>
```

