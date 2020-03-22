# Require_js
A HubL tag that enqueues a script element to be rendered. To enqueue a script to render in the &lt;head /&gt;from a different file via a &lt;script /&gt; element (as opposed to inline as shown here), use the HubL function require\_js(absolute\_url) instead.

#### Example
```jinja2
{{ standard_header_includes }}
<!-- more html -->

{% require_js position="footer" %}
    <script>
        console.log("The CMS is awesome!");
    </script>
{% end_require_js %}

{{ standard_footer_includes }}
```

#### Output
```jinja2
<!-- other standard header html -->
<!-- more html -->
<script>
    console.log("The CMS is awesome!");
</script>
<!-- other standard footer html -->
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| position | String | Set the position where the inline script will be rendered. Options include: "head" and "footer". | 'footer' | 

