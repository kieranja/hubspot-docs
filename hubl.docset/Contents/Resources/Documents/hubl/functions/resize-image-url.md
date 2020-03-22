# resize_image_url
Rewrites the URL of image stored in File Manager to a URL that will resize the image on request. The function accepts one required parameter, and five optional parameters. At least one optional parameter must be passed.

Required

- `URL`: string, URL of a HubSpot-hosted image

Optional

- width: number, the new image width in pixels
- height: number, the new image height in pixels
- length: number, the new length of the largest side, in pixels
- upscale: boolean, use the resized image dimensions even if they would scale up the original image (images may appear blurry)
- upsize: boolean, return the resized image even if it is larger than the original in bytes

#### Example
```jinja2
{{ resize_image_url("http://your.hubspot.site/hubfs/img.jpg", 0, 0, 300) }}
```

#### Output
```jinja2
http://your.hubspot.site/hubfs/img.jpg?length=300&name=img.jpg
```

| Parameter | Type | Description | 
|  ------  |  ------  |  ------  | 
| url | String | URL of a HubSpot-hosted image. | 
| width | Integer (px) | The new image width, in pixels. | 
| height | Integer (px) | The new image height, in pixels. | 
| length | Integer (px) | The new length of the largest side, in pixels. | 
| upscale | Boolean | Use the resized image dimensions even if they would scale up the original image (images may appear blurry). | 
| upsize | Boolean | Return the resized image even if it is larger than the original in bytes. | 

