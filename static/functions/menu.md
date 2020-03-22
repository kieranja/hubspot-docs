# menu
Returns the nested link structure of an advanced menu. Menu nodes have a variety of [properties](/docs/hubl/variables#menu-node-variables) that can be used on objects that are returned.

#### Example
```jinja2
{% set node = menu(987) %}
{% for child in node.children %}
	{{ child.label }}<br>
{% endfor %}
```

#### Output
```jinja2
page1<br>
page2<br>
page3<br>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| menu_id | Id | Required. The id of the menu passed as a number. | 
| root_type | Enumeration | Root type of the menu ("site_root", "top_parent", "parent", "page_name", "page_id", "breadcrumb").

"site_root" denotes static - Always show top-level pages in menu.
"top_parent" denotes dynamic by section - Show pages in menu that are related to section being viewed.
"parent" denotes dynamic by page - Show pages in menu that are related to page being viewed.
"breadcrumb" denotes breadcrumb style path menu (uses horizontal flow).
 | 
| root_key | String | Root key (id or name) when using "page_name" or "page_id". | 

