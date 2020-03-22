# Rich text
Creates a WYSIWYG content editor.

#### Example
```jinja2
{% rich_text "rich_text" %}
{% rich_text "left_column" label="Enter HTML here" html='<div>My rich text default content</div>' %}


Block Syntax Example:


{% widget_block rich_text "right_column" overrideable=True, label='Right Column'  %}
    {% widget_attribute "html" %}
            <h2>Something Powerful</h2>
            <h3>Tell The Reader More</h3>
            <p>The headline and subheader tells us what you're offering, and the form header closes the deal. Over here you can explain why your offer is so great it's worth filling out a form for.</p>
            <p>Remember:</p>
            <ul>
                <li>Bullets are great</li>
                <li>For spelling out <a href="#">benefits</a> and</li>
                <li>Turning visitors into leads.</li>
            </ul>
    {% end_widget_attribute %}
{% end_widget_block %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_right_column" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_rich_text" style="" data-hs-cos-general-type="widget" data-hs-cos-type="rich_text">
    <h2>Something Powerful</h2>
    <h3>Tell The Reader More</h3>
    <p>The headline and subheader tells us what you're offering, and the form header closes the deal. Over here you can explain why your offer is so great it's worth filling out a form for.</p>
    <p>Remember:</p>
    <ul>
        <li>Bullets are great</li>
        <li>For spelling out benefits and</li>
        <li>Turning visitors into leads.</li>
    </ul>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| html | String | Default rich text content for module. | <h2>Something Powerful</h2> <h3>Tell The Reader More</h3> <p>The headline and subheader tells us what you're offering, and the form header closes the deal. Over here you can explain why your offer is so great it's worth filling out a form for.</p> <p>Remember:</p> <ul> <li>Bullets are great</li> <li>For spelling out <a href="#">benefits</a> and</li> <li>Turning visitors into leads.</li> </ul> | 

