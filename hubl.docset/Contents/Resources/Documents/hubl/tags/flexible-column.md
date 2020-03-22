# Flexible column
Flexible columns are vertical columns in a template that allow the end user to insert and remove a variety of modules of their choosing into the template, while [editing in the content editor](https://knowledge.hubspot.com/cos-pages-editor/how-to-use-flexible-columns-in-your-pages). When coding a flexible column with HubL, you can choose to wrap other HubL modules to make them appear in the flexible column by default. The sample code below shows the basic syntax and a sample flexible column with a rich-text and form module contained as default content. Please note that flexible columns can only be added to page templates, not blog or email templates.

#### Example
```jinja2
{% widget_container "my_flexible_column" %}
    {% rich_text "my_rich_text" %}
    {% rich_text "second_rich_text" %}
{% end_widget_container %}
```

#### Output
```jinja2
<span class="hs_cos_wrapper hs_cos_wrapper_widget_container hs_cos_wrapper_type_widget_container" data-hs-cos-general-type="widget_container" data-hs-cos-type="widget_container" id="hs_cos_wrapper_my_flexible_column" style=""></span>
<div class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_rich_text" data-hs-cos-general-type="widget" data-hs-cos-type="rich_text" id="hs_cos_wrapper_widget_2822416670" style="">
	<span class="hs_cos_wrapper hs_cos_wrapper_widget_container hs_cos_wrapper_type_widget_container" data-hs-cos-general-type="widget_container" data-hs-cos-type="widget_container" id="hs_cos_wrapper_my_flexible_column" style=""></span>
</div>
<div class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_rich_text" data-hs-cos-general-type="widget" data-hs-cos-type="rich_text" id="hs_cos_wrapper_widget_2822416675" style="">
	<span class="hs_cos_wrapper hs_cos_wrapper_widget_container hs_cos_wrapper_type_widget_container" data-hs-cos-general-type="widget_container" data-hs-cos-type="widget_container" id="hs_cos_wrapper_my_flexible_column" style=""></span>
</div>
```

