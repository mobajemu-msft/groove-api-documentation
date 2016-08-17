# Groove Service REST Reference  

The Groove Service delivers Groove functionality to third-party application developers for integration within their own apps and possibly for revenue sharing. The role of the service is to abstract and merge all existing Xbox entertainment services into a single entry point with a set of consistent and simple APIs that hide the complexity of background services.  

The API follows the REST API convention and returns JSON (or XML) results. The following calling conventions are used:  

 + Parameters are provided as query parameters in the GET HTTP method. Response content is serialized in JSON by default, but can be switched to XML if the HTTP header ``` Accept: application/xm ``` l is provided.  
 + The API is versioned. Version is to be prepended to the URI. Currently, all Groove RESTful API calls must begin with **|GET|/1/.**
 + Third-party developer authentication is mandatory in all methods and is done by passing an Azure Data Market OAuth token as a mandatory query parameter in all methods.
 +  GZIP compression is supported and responses are compressed if the HTTP header ``` Accept-Encoding: gzip ``` is provided in the request.
 +   CORS is supported in the standard way, by using the headers  ```Origin ``` and  ```Access-Control-Request-*. ```
 +   JSONP is also supported via an optional query parameter, **&jsonp**=value, in all methods.
 +   Flash cross-domain calls are supported as well.
 +   Locale parameters are the same across all methods; they all have two optional query parameters, *language* and *country*, whose values are two-letter standard language and country codes. When no country information is provided via the country parameter or user authentication, the country is determined by geolocation of the caller's IP address.
 +   All APIs share a common notion of namespace that indicates the type of content referred to. Currently the only supported namespace is music.  
 
##URI  (to be generated automatically)

|METHOD  | ENDPOINT |  USAGE | RETURNS|   |
| :---|:-----|:----------| :---|:---|  
|GET|[/1/content/{id}/{source}/{browseType}/{extra}/browse]()|Browse specific sub-items of a given ID (for example, the albums of an artist or the tracks of a playlist).|||
|GET|[/1/content/{namespace}/catalog/genres]()|Get a list of genres available for a locale.|||
|GET|[/1/content/{namespace}/catalog/{type}/browse]()|Browse the music catalog.|||
|GET|[/1/content/{namespace}/collection/add]()|Add tracks to a user's collection.|||
|GET|[/1/content/{namespace}/collection/delete]()|Delete tracks from a user's collection.|||
|GET|[/1/content/{namespace}/collection/playlists/create]()|Create a playlist on behalf of a user.|||
|GET|[/1/content/{namespace}/collection/playlists/delete]()|Delete a playlist of a user.|||
|GET|[/1/content/{namespace}/collection/playlists/update]()|Update a playlist on behalf of a user.|||
|GET|[/1/content/{namespace}/collection/{type}/browse]()|Browse a user's collection or playlists.|||
|GET|[/1/content/{id}/lookup]()|Look up one or several items from a media catalog and/or user's collection.|||
|GET|[/1/content/{namespace}/newreleases]()|Discover new releases.|||
|GET|[/1/content/{id}/preview]()|Request preview streaming.|||
|GET|[/1/content/{namespace}/search?q={query}]()|Search for items in a media catalog, user's collection, or both.|||
|GET|[/1/content/{namespace}/spotlight]()|Discover content for a specified language or culture.|||
|GET|[/1/content/{id}/stream]()|Request streaming.|||
|GET|[/1/user/{namespace}/profile]()|Access a user's profile.|||
 
##JSON (to be generated automatically if relevant)
|OBJECT|DESCRIPTION|
|:---|:---|
|[Album (JSON)]()|A musical recording.|
|[Artist (JSON)]()|The creator or creators of a musical recording.|
|[CollectionState (JSON)]()|The state of the user's collection (if the request was user-authenticated).|
|[ContentItem (JSON)]()|An item of content (either an Album or an Artist).|
|[ContentResponse (JSON)]()|The output element for most content APIs.|
|[Contributor (JSON)]()|An artist and the artist's role
|[Error (JSON)]()|Error object for attempts to query the Music catalog.|
|[PaginatedList (JSON)]()|Describes paginated lists, a type of response from the Groove Service that can be continued by using a token.|
|[Playlist (JSON)]()|A list of tracks and their metadata.|
|[PlaylistAction (JSON)]()|The input element for every playlist action request: create, update, and delete.|
|[PlaylistActionResponse (JSON)]()|The output element for every playlist action request: create, update, and delete.|
|[PlaylistActionResult (JSON)]()|The object describing a playlist action result, used by add and delete.|
|[StreamResponse (JSON)]()|Response to all stream APIs.|
|[Track (JSON)]()|Describes a track, an individual piece of musical content from an album.|
|[TrackAction (JSON)]()|An action (such as add or delete) on a specific track.|
|[TrackActionRequest (JSON)]()|The input element for every track action request: add and delete.|
|[TrackActionResponse (JSON)]()|The output element for every track action request: add and delete.|
|[TrackActionResult (JSON)]()|The object describing a track action result, used by add and delete.|
|[UserProfileResponse (JSON)]()|Profile of the user, including subscription, collection, and culture information.|

##Additional material  

Parameters common to every Groove RESTful API  
	&nbsp;&nbsp;&nbsp;&nbsp; Describes the parameters common to all methods in the Groove RESTful API.  

Extra parameters for Lookup API  
	&nbsp;&nbsp;&nbsp;&nbsp;Optional query parameter that allows requesting a list of extra fields that are by default not included in the responses.  

Namespaces supported  
	&nbsp;&nbsp;&nbsp;&nbsp;Description of the different namespaces used across the Groove RESTful API  n

orderBy parameter for Catalog and Collection Browse APIs  
	&nbsp;&nbsp;&nbsp;&nbsp;Allows ordering browse results in a specific order.  

Groove RESTful API HTTP Status Codes  
	&nbsp;&nbsp;&nbsp;&nbsp;Describes the standard HTTP status codes that are returned by the service.
