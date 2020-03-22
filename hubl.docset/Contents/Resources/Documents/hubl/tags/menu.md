# Menu
Generates an advanced menu based on a menu tree in **Content Settings &gt; Advanced Menus.**

#### Example
```jinja2
{% menu "menu" %}
{% menu "my_menu" id=456, site_map_name='Default', overrideable=False, root_type='site_root', flyouts='true', max_levels='2', flow='horizontal', label='Advanced Menu' %}
```

#### Output
```jinja2
<div id="hs_menu_wrapper_my_menu" class="hs-menu-wrapper active-branch flyouts hs-menu-flow-horizontal" data-sitemap-name="Default">
    <ul>
        <li class="hs-menu-item hs-menu-depth-1"><a href="http://www.underseaband.com/music">Music</a></li>
        <li class="hs-menu-item hs-menu-depth-1"><a href="http://www.underseaband.com/shows">Shows</a></li>
        <li class="hs-menu-item hs-menu-depth-1"><a href="http://www.underseaband.com/blog">Blog</a></li>
        <li class="hs-menu-item hs-menu-depth-1"><a href="http://www.underseaband.com/contact">Contact</a></li>
    </ul>
</div>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| id | Integer | ID of Menu Tree from Advanced Menus in Content Settings. | 
           
           | 
| site_map_name | String | Name of Menu Tree from Advanced Menus in Content Settings. |  'default' | 
| root_type | Enumeration | Specifies the type of advanced menus. Options include: "site_root", "top_parent", "parent", "page_name", "page_id", and "breadcrumb". These values correspond to static, dynamic by section, dynamic by page, and breadcrumb. |  'site_root' | 
| flyouts | String | When true, a class is added to the menu tree that can be styled to allow child menu items will appear when you hover over the parent. When false, child menu items will always appear. |  'true' | 
| max_levels | Integer | Determines how many levels of nested menus render in the markup. This parameter dictates number of menu tree children that can be expanded in the menu. | 2 | 
| flow | Enumeration | Sets orientation of menu items. This adds classes to menu tree, so that they can be styled accordingly. Possible values include "horizontal", "vertical" or "vertical_flyouts". Horizontal menus display items side-by-side, and vertical menus are top-to-bottom. |  'horizontal' | 
| root_key | String | Used to find the menu root. When root_type is set to page_id or page_name, this param should be the page ID or the label of the page, respectively. | 'horizontal' | 

