# Post Listing
Adds a listing of most popular or top posts.

#### Example
```jinja2
{% post_listing "post_listing" %}
{% post_listing "top_posts" select_blog='default', label='Recent Posts', overrideable=False, list_title='Recent Posts', listing_type='recent', max_links=5 %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_top_posts" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_post_listing" style="" data-hs-cos-general-type="widget" data-hs-cos-type="post_listing">
    <div class="block">
        <h3>Most popular posts</h3>
        <div class="widget-module">
            <ul>
                <li><a href="http://www.underseaband.com/blog/5-emerging-bands-that-you-need-to-hear">5 emerging bands that you need to hear</a></li>
                <li><a href="http://www.underseaband.com/blog/pedal-board-power-supplies">Pedal Board Power Supplies</a></li>
                <li><a href="http://www.underseaband.com/blog/pedal-board-wiring">Pedal Board Wiring</a></li>
                <li><a href="http://www.underseaband.com/blog/pedal-board-layouts">Pedal Board Layouts</a></li>
                <li><a href="http://www.underseaband.com/blog/your-teeth-shake">Your Teeth Shake</a></li>
            </ul>
        </div>
    </div>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| select_blog | 'default' or blog ID |  Selects the HubSpot blog to use for the listing. This parameter uses either an blog ID or 'default' value. | 'default' | 
| list_title | String | List title to display. | '' | 
| list_tag | String | Sets the tag used for the list. Value should generally be 'ul' or 'ol'. | 'ul' | 
| title_tag | String | Sets the tag used for the list title. | 'h3' | 
| listing_type | String | List the blog posts by most recent or most popular in a time range. Possible values include recent, popular_all_time, popular_past_year, popular_past_six_months, and popular_past_month. | 'recent' | 
| max_links | Number |  Maximum number of blog posts to list. | 5 | 
| include_featured_image | Boolean |  Display featured image along with post link. | False | 

