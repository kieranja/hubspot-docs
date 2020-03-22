# super
Super prints content from the parent template into a child template, when you have created parent and children templates, using the extends tag. For example in the code below, a basic HTML template has been created with a HubL block named "sidebar" and saved as parent.html. A second template file is created that will extend that parent file. Normally the &lt;h3&gt; would be printed in the parent HTML's sidebar block. But by using super, content from the parent template sidebar block is combined with the content from the child template.

#### Example
```jinja2
{% extends "custom/page/web_page_basic/parent.html" %}

{% block sidebar %}
    <h3>Table Of Contents</h3>
    {{ super() }}
{% endblock %}
```

#### Output
```jinja2
<!doctype html>
<html>
    <head>
        <meta charset="utf-8">
        <title>This is the parent template </title>
    </head>
    <body>
             <h3>Table of contents</h3>
            Sidebar content from parent.
    </body>
</html>
```

