# Import
Another useful feature of macros is that they can be used across templates by importing one template file into another. To do this you will need to use the **import** tag. The import tag will let you specify a Design Manager file path to the template that contains your macros and give the macros a name in the template that you are including them in. You can then pass values into these macros without needing to redefine them.

For example, let's say that you have a .html template file that contains the following 2 macros. One macro is defined to set up a header tag and one is defined to generate a footer tag. This file is saved in Design Manager with the name `my_macros.html`.

#### Example
```jinja2
<!-- my_macros.html file -->
{% macro header(tag, title_text) %}
    <header> <{{ tag }}>{{ title_text }} </{{tag}}> </header>
{% endmacro %}

{% macro footer(tag, footer_text) %}
     <footer> <{{ tag }}>{{ footer_text }} </{{tag}}> </footer>
{% endmacro %}
```

In the template that will use these macros, an import tag is used that specifies the file path to the `my_macros.html` file. It also names the group of macros (in this example `header_footer`). Macros can then be executed by appending the macro name to the name given to the imported template. See the example below.

#### Example
```jinja2
{% import 'custom/page/web_page_basic/my_macros.html' as header_footer %}
{{ header_footer.header('h1', 'My page title') }}
<p>Some content</p>
{{ header_footer.footer('h3', 'Company footer info') }}
```

#### Output
```jinja2
<header><h1>My page title</h1></header>
<p>Some content</p>
<footer><h3>Company footer info</h3></footer>
```

