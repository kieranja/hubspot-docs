# Video Player
Render a Vidyard video player for a File Manager video which is selected "Allow embedding, sharing, and tracking".

#### Example
```jinja2
{% video_player "embed_player" %}
{% video_player "embed_player" overrideable=False, type='scriptV4', hide_playlist=True, viral_sharing=False, embed_button=False, width='600', height='375', player_id='6178121750', style='', conversion_asset='{"type":"FORM","id":"9a77c63f-bee6-4ff8-9202-b0af020ea4b2","position":"POST"}' %}
```

| Parameter | Type | Description | Default | 
|  ------  |  ------  |  ------  |  ------  | 
| hide_playlist | Boolean | Hide the video playlist. | True | 
| playlist_color | String | A HEX color value for the playlist. | 
           
           | 
| play_button_color | String | A HEX color value for the play and pause buttons. | #2A2A2A | 
| embed_button | Boolean | Display embed button on the player | False | 
| viral_sharing | Boolean | Display the social networks sharing button on the player. | False | 
| width | Number | Width of the embedded video player. | Auto | 
| height | Number | Height of the embedded video player. | Auto | 
| player_id | Number | The player_id of the video to embed. Returned at GET /filemanager/api/v2/files/:file_id in the meta.video_data.hosting_infos dict. | 
           
           | 
| style | String | Additional style for player. | 
           
           | 
| conversion_asset | JSON | Event setting for player. Can render CTA or Form before or after video plays. This parameter takes a JSON object with three parameters: type (FORM or CTA), id (The guid of the type object), position (POST or PRE). | See above example | 

