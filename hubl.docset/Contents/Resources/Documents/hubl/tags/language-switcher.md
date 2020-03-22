# Language switcher
Adds a Globe Icon with links to the translated versions of a given CMS page. Learn more about [multi-language content here](https://knowledge.hubspot.com/cos-general/how-to-manage-multi-language-content-with-hubspots-cos).

#### Example
```jinja2
{% language_switcher "language_switcher" overrideable=false, display_mode='localized', label='Language Switcher' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_module_1487954976079503" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_language_switcher" style="" data-hs-cos-general-type="widget" data-hs-cos-type="language_switcher">
  <div class="lang_switcher_class">
     <div class="globe_class">
         <ul class="lang_list_class">
             <li>
                 <a class="lang_switcher_link" href="http://www.hubspot.com">English</a>
             </li>
             <li>
                 <a class="lang_switcher_link" href="http://www.hubspot.com/es">Spanish</a>
             </li>
         </ul>
     </div>
  </div>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| display_mode | Enumeration | The language of the text in the language switcher. Values are:

Pagelang means the names of languages will display in the language of the page the switcher is on.
Localized means the name of each language will display in that language.
Hybrid is a combination of the two.
 | Localized | 

