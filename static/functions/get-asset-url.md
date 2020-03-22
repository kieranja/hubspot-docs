# get_asset_url
This function returns the public URL of a specified template or code file. The parameter of this function is the path in Design Manager. Coded file URLs update each time you publish them; therefore, by using this function your ensure you are always using the latest version of the file.

You can automatically generate this function in the app, by either right-clicking on a file name and choosing "Copy public URL" or by choosing **Actions &gt; Copy public URL**. The example below gets the URL of a Javascript file authored in Design Manager that can be included as the `src` of a ``.

#### Example
```jinja2
{{ get_asset_url("/custom/styles/style.css") }} 
```

#### Output
```jinja2
//cdn2.hubspot.net/hub/1234567/hub_generated/template_assets/1565970767575/custom/styles/style.min.css
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| path | String | The Design Manager file path to the template or file. | 

