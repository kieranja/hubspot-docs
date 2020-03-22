# Spacer
A spacer module generates an empty span tag. This tag can be styled to act as a spacer. In drag and drop layouts, the spacer module is wrapped in a container with a class of span1-span12 to determine how much space the module should take up in the twelve column responsive grid.

#### Example
```jinja2
{% space "space" %}
{% space "spacer" label='Horizontal Spacer' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_module_spacer" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_space" style="" data-hs-cos-general-type="widget" data-hs-cos-type="space"></span>
```

