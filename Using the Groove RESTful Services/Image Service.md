#Image Service
Every piece of content returned by content APIs contains a field, ImageUrl, that is a direct link to the content's default image, hosted on ```http://musicimage.xboxlive.com/```. This image link generates an image with specific default properties, but it is possible to modify the link in order to change some of the image properties, such as its size. Image resolution is context-aware, so the actual image might change depending on the size parameters used. The details of the image API are shown in this topic.  

You should use the image URL given in the response. The URL should not be modified or altered other than with the parameters described below. Any other use of the images will be considered as a breach of the [terms of use] of the API.  

You can optionally append to the URL the parameters shown in the following table.  

|Argument|Type|Description|
|:---|:---|:---|
|w|integer|Optional. Image width. Cannot be set without height parameter.|
|h|integer|Optional. Image height. Cannot be set without width parameter.|
|mode|string|Image resize mode:   **1**.  *scale* to resize to maximum size which fits dimension without changing the aspect ratio.   **2**. *letterbox* to pad to dimension after resize if aspect ratio didn't match.   **3**. *crop* to get the required width and height but image is cropped. Defaults to *crop* if w and h are provided.|
|background|string|HTML-compliant color for letterbox resize mode background. Cannot be specified if mode is not set to letterbox. The # character must be URL-encoded when specifying the letterbox background color. For example: *http://musicimage.xboxlive.com/content/music.A83EB907-0100-11DB-89CA-0019B92A3933/image?locale=en-US&w=200&h=100&mode=letterbox&background=%23ff00ff*|
Changing these parameters can trigger different images. The service will always try to provide the best image for the requested ratio.  

For example:  

**Default image:** *http://musicimage.xboxlive.com/content/music.24540000-0200-11DB-89CA-0019B92A3933/image?locale=en-US*  

**Square image:** *http://musicimage.xboxlive.com/content/music.24540000-0200-11DB-89CA-0019B92A3933/image?locale=en-US&w=200&h=200*

**Letterboxed:** *http://musicimage.xboxlive.com/content/music.24540000-0200-11DB-89CA-0019B92A3933/image?locale=en-US&w=240&h=200&mode=letterbox*


 [terms of use]: https://github.com/Microsoft/Groove-API-documentation/blob/master/Groove%API%Terms%of%use.md
