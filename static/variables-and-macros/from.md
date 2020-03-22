# From
If you want to only import specific macros, instead of all macros contained in a separate .html file, you can use the **from** tag. With the from tag, specify only the macros that you want to import. Generally, using **import** will provide more flexibility, but this alternative is also supported.

The example below accesses the same `my_macros.html` file from the previous section of this article. But this time instead of importing all macros, it accesses only the footer macro.

#### Example
```jinja2
{% from 'custom/page/web_page_basic/my_macros.html' import footer %}
{{ footer('h2', 'My footer info') }}
```

#### Output
```jinja2
<footer><h2>My footer info</h2></footer>
```

