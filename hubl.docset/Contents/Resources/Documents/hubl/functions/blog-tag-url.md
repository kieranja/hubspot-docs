# blog_tag_url
The `blog_tag_url` function returns a full URL to the specified blog tag's listing page.

This function accepts two parameters. The first parameter specifies which blog the tag's listing page exists in. The second parameter specifies which tag to link. This parameter can use the **`topic.slug`** for a particular tag from `content.topic_list` or accepts a lowercase hyphenated name such as `'marketing-tips'`.

The example below shows how this function can be used as an anchor's href. This can be combined with `blog_topics` as shown in that function's examples.

#### Example
```jinja2
<a href="{{ blog_tag_url('default', 'inbound-marketing') }}">Inbound Marketing</a>
```

#### Output
```jinja2
<a href="http://blog.hubspot.com/marketing/tag/inbound-marketing">Inbound Marketing</a>
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| selected_blog | Blog id or 'default'	 | Specifies which blog to use. | 
| tag_slug | String | Specifies which tag to link to. | 

