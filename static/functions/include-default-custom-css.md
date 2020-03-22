# include_default_custom_css
This function generates a link tag that references the [Primary CSS file](https://knowledge.hubspot.com/cos-general/create-edit-and-attach-css-files-to-style-your-site) (`default_custom_style.min.css`). This file is designed to be a global CSS file that can be added to all templates. To render, the function requires a boolean parameter value of `True`.

#### Example
```jinja2
{{ include_default_custom_css(True) }} 
```

#### Output
```jinja2
<link href="//cdn2.hubspot.net/hub/327485/hub_generated/style_manager/1420345777097/custom/styles/default/hs_default_custom_style.min.css" rel="stylesheet">
```

