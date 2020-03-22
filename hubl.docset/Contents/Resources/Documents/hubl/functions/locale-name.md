# locale_name
Returns a human-readable string representation of a language code, optionally translated to a target language.

#### Example
```jinja2
{{ locale_name('es') }}
{{ locale_name('es', 'en') }}
```

#### Output
```jinja2
Español
Spanish
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| language_code | String | The language code. | 
| target_language_code | String | The language that the output will be translated to. | 

