# Post filter
Creates a linked listing of posts by topic, posts by month, or posts by author.

#### Example
```jinja2
{% post_filter "post_filter" %}
{% post_filter "posts_by_topic" select_blog='default', expand_link_text='see all', overrideable=False, list_title='Posts by Topic', max_links=5, filter_type='topic', label='Posts by Topic' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_posts_by_topic" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_post_filter" style="" data-hs-cos-general-type="widget" data-hs-cos-type="post_filter">
    <div class="block">
        <h3>Posts by Topic</h3>
        <div class="widget-module">
            <ul>
                <li><a href="http://www.underseaband.com/blog/topic/pedals">pedals (15)</a></li>
                <li><a href="http://www.underseaband.com/blog/topic/music-recommendations">music recommendations (7</a></li>
                <li><a href="http://www.underseaband.com/blog/topic/undersea">Undersea (6)</a> </li>
                <li> <a href="http://www.underseaband.com/blog/topic/band">band (2)</a> </li>
                <li> <a href="http://www.underseaband.com/blog/topic/diy-tips">DIY tips (2)</a> </li>
                <li> <a href="http://www.underseaband.com/blog/topic/visual-artists">Visual artists (1)</a> </li>
            </ul>
        </div>
    </div>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| select_blog | 'default' or blog ID | Selects the HubSpot blog to use. This parameter uses either an blog ID or 'default' value. | 'default' | 
| expand_link_text | String |  Text link to display if more posts than max_links number available. Exclude parameter to omit link. | 'see all' | 
| list_title | String | List title to display. | '' | 
| list_tag | String | Sets the tag used for the list. Value should generally be 'ul' or 'ol'. | 'ul' | 
| title_tag | String | Sets the tag used for the list title. | 'h3' | 
| max_links | Number | Maximum number of filter values to display. Excude parameter to show all. | 5 | 
| filter_type | Enumeration | Selects the type of filter. Possible values include 'topic', 'month', and 'author'. | 'topic' | 

