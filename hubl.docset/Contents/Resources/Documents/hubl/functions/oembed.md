# oembed
Returns OEmbed data dictionary for given request.

#### Example
```jinja2
{{ oembed({ url: "https://www.youtube.com/watch?v=KqpFNtbEOh8"}) }}
```

#### Output
```jinja2
OEmbedResponse{type=video, version=1.0, html=<iframe width="480" height="270" src="https://www.youtube.com/embed/KqpFNtbEOh8?feature=oembed" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>, title=Marketing Is a Marathon — Build a Complete Customer Experience, authorName=HubSpot, authorUrl=https://www.youtube.com/user/HubSpot, providerName=YouTube, providerUrl=https://www.youtube.com/, thumbnailUrl=https://i.ytimg.com/vi/KqpFNtbEOh8/hqdefault.jpg, thumbnailWidth=480, thumbnailHeight=360}
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| request | String | Request object, {url: string, max_width: long, max_height: long}. | 

