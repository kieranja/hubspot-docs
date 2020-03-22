# module_asset_url
Gets the URL for an asset attached to a custom module via **Linked Files &gt; Other Files**.

#### Example
```jinja2
{{ module_asset_url("smile.jpg") }} 
```

#### Output
```jinja2
https://cdn2.hubspot.net/hubfs/6178146/logo-black-color.png
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| name | String | The name of the asset. | 

