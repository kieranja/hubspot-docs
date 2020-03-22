# Require_css
A HubL tag that enqueues a style element to be rendered in the &lt;head&gt;. To enqueue a stylesheet from a different file to render in the &lt;head /&gt; via a &lt;link /&gt; tag (as opposed to inline as shown here), use the HubL function require\_css(absolute\_url) instead.

#### Example
```jinja2
{{ standard_header_includes }}
<!-- more html -->

{% require_css %}
    <style>
        body {
            color: red;
        }
    </style>
{% end_require_css %}

{{ standard_footer_includes }}
```

#### Output
```jinja2
<!-- other standard header html -->
    <style>
        body {
            color: red;
        }
    </style>
<!-- more html -->
<!-- other standard footer html -->
```

