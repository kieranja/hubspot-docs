# require_js
This function enqueues a script to be rendered in either the head tag or footer. The HubL is replaced by an empty line and included in either `{{ standard_footer_includes }}` (the default) or `{{ standard_header_includes }}` if the call contains the `'head'` parameter.

To enqueue an inline script to be rendered in the head tag via a script element, use the `{% require_js %} and {% end_require_js %}` tag instead with you script tags and JS code inside.

#### Example
```jinja2
{{ standard_header_includes }}
<!-- more html -->
{{ require_js("http://example.com/path/to/footer-file.js", "footer") }}
{{ require_js("http://example.com/path/to/head-file.js", "head") }}

{{ standard_footer_includes }}
```

#### Output
```jinja2
<!-- other standard header html -->
<script src="http://example.com/path/to/head-file.js"></script>

<!-- more html -->

<script src="http://example.com/path/to/footer-file.js"></script>
<!-- other standard footer html -->
```

