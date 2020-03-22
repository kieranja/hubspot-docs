# RSS listing
Loads a list of content from an internal or external RSS feed.

#### Example
```jinja2
{% rss_listing "rss_listing" %}
{% rss_listing "my_rss_listing" rss_url='', publish_date_text='posted at', feed_source={rss_url='', is_external=False, content_group_id='24732847'}, click_through_text='Read more', show_date=True, include_featured_image=True, overrideable=False, publish_date_format='short', show_detail=True, show_author=True, number_of_items='5', is_external=False, title='', content_group_id='24732847', label='RSS Listing', limit_to_chars='200', attribution_text='by' %}
```

#### Output
```jinja2
<span id="hs_cos_wrapper_my_rss_listing" class="hs_cos_wrapper hs_cos_wrapper_widget hs_cos_wrapper_type_rss_listing" style="" data-hs-cos-general-type="widget" data-hs-cos-type="rss_listing">
    <h3></h3>
    <div class="hs-rss-module feedreader_box">
        <div class="hs-rss-item hs-with-featured-image">
            <div class="hs-rss-item-text">
                <a class="hs-rss-title" href="http://www.underseaband.com/blog/city-where-stars-are-not"><span>City
                        Where Stars Are Not</span></a>
                <div class="hs-rss-byline">by <span class="hs-rss-author">Matthew Vincenty</span>
                    <span class="hs-rss-posted-at">posted at</span> <span class="hs-rss-date">5/1/15 11:02 AM</span>
                </div>
                <div class="hs-rss-description">
                    <p> We are pleased to announce the release of our next single "City Where Stars Are Not"! It will be
                        available Tuesday May 5th and features lead vocals by bassist David Hunt. Thanks to Peter...<a
                            href="http://www.underseaband.com/blog/city-where-stars-are-not">Read more</a> </p>
                </div>
            </div>
            <div class="hs-rss-item-image-wrapper">
                <img class="hs-rss-featured-image" src="http://www.underseaband.com/hubfs/Blog_Images/citywherestarsarenot.png?t=1430835551915"> 
            </div>
        </div>
        <div class="hs-rss-item hs-with-featured-image">
            <div class="hs-rss-item-text">
                <a class="hs-rss-title" href="http://www.underseaband.com/blog/loud-louder"><span>New Pedal! ChadderBox
                        Effects Loud Louder</span></a>
                <div class="hs-rss-byline">by <span class="hs-rss-author">Corey Wade</span>
                    <span class="hs-rss-posted-at">posted at</span> <span class="hs-rss-date">4/27/15 10:30 AM</span>
                </div>
                <div class="hs-rss-description">
                    <p>
                        I have the good fortune to have recently met Chad from ChadderBox Effects. It turns out he works
                        part-time on the same floor in the same building where I also work part-time. When I found out
                        Chad...<a href="http://www.underseaband.com/blog/loud-louder">Read more</a> </p>
                </div>
            </div>
            <div class="hs-rss-item-image-wrapper"> <img class="hs-rss-featured-image"
                    src="http://www.underseaband.com/hubfs/Blog_Images/10724991_612551458879970_1563949619_n.jpg?t=1430835551915">
            </div>
        </div>
        <div class="hs-rss-item hs-with-featured-image">
            <div class="hs-rss-item-text"> <a class="hs-rss-title"
                    href="http://www.underseaband.com/blog/introducing-ariél-torres"><span>Introducing: Ariél
                        Torres</span></a>
                <div class="hs-rss-byline">by <span class="hs-rss-author">Corey Wade</span> <span
                        class="hs-rss-posted-at">posted at</span> <span class="hs-rss-date">4/24/15 10:30 AM</span>
                </div>
                <div class="hs-rss-description">
                    <p> Everyone needs to check out Boston-based visual artist Ariél Torres’ work. He was very nice to
                        let us use one of his pieces for “Your Teeth Shake”, and we couldn’t be more stoked about it.
                        Check out...<a href="http://www.underseaband.com/blog/introducing-ariél-torres">Read more</a>
                    </p>
                </div>
            </div>
            <div class="hs-rss-item-image-wrapper"> <img class="hs-rss-featured-image"
                    src="http://www.underseaband.com/hubfs/tangledupinblue-449270-edited.jpg?t=1430835551915"> </div>
        </div>
        <div class="hs-rss-item hs-with-featured-image">
            <div class="hs-rss-item-text"> 
                <a class="hs-rss-title" href="http://www.underseaband.com/blog/new-pedal-fuzzrocious-rat-tail"><span>New Pedal! Fuzzrocious Rat Tail</span></a>
                <div class="hs-rss-byline">by <span class="hs-rss-author">Matthew Vincenty</span> <span
                        class="hs-rss-posted-at">posted at</span> <span class="hs-rss-date">4/21/15 4:34 PM</span>
                </div>
                <div class="hs-rss-description">
                    <p> I found myself in the position of needing to put together a new board to fill in on guitar with
                        our friends Glacier.&nbsp;First I needed a distortion pedal that could pull of their heavier
                        bits so I...<a href="http://www.underseaband.com/blog/new-pedal-fuzzrocious-rat-tail">Read
                            more</a> </p>
                </div>
            </div>
            <div class="hs-rss-item-image-wrapper"> <img class="hs-rss-featured-image"
                    src="http://www.underseaband.com/hubfs/Blog_Images/11023171_476701342477661_420938091_n.jpg?t=1430835551915">
            </div>
        </div>
        <div class="hs-rss-item hs-with-featured-image">
            <div class="hs-rss-item-text"> <a class="hs-rss-title"
                    href="http://www.underseaband.com/blog/using-two-amps"><span>Using two amps</span></a>
                <div class="hs-rss-byline">by <span class="hs-rss-author">Matthew Vincenty</span> <span
                        class="hs-rss-posted-at">posted at</span> <span class="hs-rss-date">4/17/15 3:58 PM</span>
                </div>
                <div class="hs-rss-description">
                    <p> Sometimes just one amp isn't enough. Using multiple amps together can yield a sound that is more
                        than the sum of it's parts. Both Corey and myself have split our singal to multiple amps.
                        Currently...<a href="http://www.underseaband.com/blog/using-two-amps">Read more</a> </p>
                </div>
            </div>
            <div class="hs-rss-item-image-wrapper"> <img class="hs-rss-featured-image"
                    src="http://www.underseaband.com/hubfs/Blog_Images/E719C0A7-6C2A-41FB-9A59-FA8236DED4A5.jpg?t=1430835551915">
            </div>
        </div>
    </div>
</span>
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| show_title | Boolean |  Shows or hides RSS feed title. | True | 
| show_date | Boolean | Displays post date. | True | 
| show_author | Boolean | Displays author name. | True | 
| show_detail | Boolean | Display post summary up to number of characters set by limit_to_chars parameter. | True | 
| title | String | Populates a heading above the RSS feed listing. | 
           
           | 
| limit_to_chars | Number | Maximum number of characters to display in summary. | 200 | 
| publish_date_format | String | Format for the publish date. Possible values include 'short', 'medium' and 'long'. Also accepts custom formats including "MMMM d, yyyy 'at' h:mm a". | 'short' | 
| attribution_text | String | The text which attributes an author to a post. | 'by' | 
| click_through_text | String | The text which will be displayed for the click through link at the end of a post summary. | 'Read more' | 
| publish_date_text | String |  The text which indicates when a post was published. | 'posted at' | 
| include_featured_image | Boolean | Displays featured image with post link for HubSpot generated RSS feeds. | False | 
| item_title_tag | String | Specifies HTML tag of each post title. | span | 
| is_external | Boolean | RSS feed is from an external blog. | False | 
| number_of_items | Number | Maximum number of posts to display. | 5 | 
| publish_date_language | String | Specifies the language of the publish date. | en_US | 
| rss_url | String |  The URL where the RSS feed is located. | 
           
           | 
| content_group_id | String | ID for blog when feed source is internal blog. | 
           
           | 
| select_blog | String | Can be used to select an internal HubSpot blog feed. | default | 
| feed_source | String | Set source for RSS feed. When internal, general format is {rss_url='', is_external=False, content_group_id='2502431580'}. When external, general format is {rss_url='http://blog.hubspot.com/marketing/rss.xml', is_external=True}. | 
           
           | 
| tag_id | Number | ID for tag when feed source is internal blog. | 
           
           | 

