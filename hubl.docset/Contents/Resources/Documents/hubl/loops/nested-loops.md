# Nested loops
Loops can also be nested with loops. The child for loop will run with each iteration of the parent for loop. In the example below, a list of child items is printed in a nested `` within a `` of parent items.

#### Example
```jinja2
{% set parents = ['Parent item 1', 'Parent item 2', 'Parent item 3'] %}
{% set children = ['Child item 1', 'Child item 2', 'Child item 3'] %}
<ul>
{% for parent in parents %}
<li>{{parent}}<ul>
    {% for child in children %}
    <li>{{child}}</li>
    {% endfor %}
    </ul>
</li>
{% endfor %}
</ul>
```

#### Output
```jinja2
<ul>
<li>Parent item 1<ul>
    <li>Child item 1</li>
    <li>Child item 2</li>
    <li>Child item 3</li>
    </ul>
</li>

<li>Parent item 2<ul>
    <li>Child item 1</li>
    <li>Child item 2</li>
    <li>Child item 3</li>
    </ul>
</li>

<li>Parent item 3<ul>
    <li>Child item 1</li>
    <li>Child item 2</li>
    <li>Child item 3</li>
    </ul>
</li>
</ul>
```

