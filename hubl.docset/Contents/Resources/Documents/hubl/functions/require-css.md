# require_css
This function enqueues a CSS file to be rendered in the head element. All CSS link tags are grouped together and render before any JavaScript tags. The HubL is replaced with an empty line and then a link tag is added to `{{ standard_header_includes }}`. This method requires an absolute URL; CMS content with a known relative URL can be required by using the `get_asset_url()` function.

To enqueue an inline style to be rendered in the `head` via a style tag element, use the `{% require_css %} and {% end_require_css %}` tag instead with your style tags and CSS inside of that.

#### Example
```jinja2
{{ standard_header_includes }}
<!-- more html -->
{{ require_css("http://example.com/path/to/file.css") }}
{{ require_css(get_asset_url("/relative/path/to/file.css")) }}
```

#### Output
```jinja2
<!-- other standard header html -->
<link type="text/css" rel="stylesheet" href="http://example.com/path/to/file.css">
<link type="text/css" rel="stylesheet" href="http://example.com/relative/path/to/file.css">
<!-- more html -->
```

