# Simple menu
Simple menus allow you to create basic navigation menus that can be modified at the page level. Unlike regular menu modules, simple menus are not managed from the Advanced Menus screen in Content Settings, but rather from the template and page editors. You can use [block syntax](/docs/building-blocks/modules/syntax-and-parameters) to set up a default menu tree.

#### Example
```jinja2
{% simple_menu "simple_menu" %}
{% simple_menu "my_simple_menu" orientation='horizontal', label='Simple Menu' %}


Block Syntax Example:


{% widget_block simple_menu "block_simple_menu" overrideable=True, orientation='horizontal', label='Simple Menu'  %}
        {% widget_attribute "menu_tree" is_json=True %}[{"contentType": null, "subCategory": null, "pageLinkName": null, "pageLinkId": null, "isPublished": false, "categoryId": null, "linkParams": null, "linkLabel": "Home", "linkTarget": null, "linkUrl": "http://www.hubspot.com", "children": [], "isDeleted": false}, {"contentType": null, "subCategory": null, "pageLinkName": null, "pageLinkId": null, "isPublished": false, "categoryId": null, "linkParams": null, "linkLabel": "About", "linkTarget": null, "linkUrl": "http://www.hubspot.com/internet-marketing-company", "children": [{"contentType": null, "subCategory": null, "pageLinkName": null, "linkUrl": "http://www.hubspot.com/company/management", "isPublished": false, "children": [], "linkParams": null, "linkLabel": "Our Team", "linkTarget": null, "pageLinkId": null, "categoryId": null, "isDeleted": false}], "isDeleted": false}, {"contentType": null, "subCategory": null, "pageLinkName": null, "pageLinkId": null, "isPublished": false, "categoryId": null, "linkParams": null, "linkLabel": "Pricing", "linkTarget": null, "linkUrl": "http://www.hubspot.com/pricing", "children": [], "isDeleted": false}]{% end_widget_attribute %}
{% end_widget_block %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_my_simple_menu" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_simple_menu" style="" data-hs-cos-general-type="widget" data-hs-cos-type="simple_menu">
    <ul></ul>
</span>


<span id="hs_cos_wrapper_block_simple_menu" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_simple_menu"
    style="" data-hs-cos-general-type="widget" data-hs-cos-type="simple_menu">
    <div id="hs_menu_wrapper_module_143093417497114626" class="hs-menu-wrapper active-branch flyouts hs-menu-flow-horizontal" data-sitemap-name="">
        <ul>
            <li class="hs-menu-item hs-menu-depth-1"><a href="//www.hubspot.com" target="_self">Home</a></li>
            <li class="hs-menu-item hs-menu-depth-1 hs-item-has-children"><a href="//www.hubspot.com/internet-marketing-company" target="_self">About</a>
                <ul class="hs-menu-children-wrapper">
                    <li class="hs-menu-item hs-menu-depth-2"><a href="//www.hubspot.com/company/management" target="_self">Our Team</a></li>
                </ul>
            </li>
            <li class="hs-menu-item hs-menu-depth-1"><a href="//www.hubspot.com/pricing" target="_self">Pricing</a></li>
        </ul>
    </div>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| orientation | Enumeration | Defines classes of menu markup to allow to style the orientation of menu items on the page. Possible values include 'horizontal' and 'vertical'. | 'horizontal' | 
| menu_tree | JSON | Menu structure including page link names and target URLs. | [] | 

