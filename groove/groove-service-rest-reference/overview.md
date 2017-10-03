---
title: Groove Music API REST Reference overview | Groove Services
description:  Discover Groove Music API REST Reference, endpoints and parameters.
keywords: groove music, groove api, groove rest
author: sakley
ms.assetid: f07471e2-96b0-48a9-b05d-66f270859bc4
---

| Notice to customers|
|----- |
|Starting Oct 2nd, the Onboarding to the Groove Music API is disabled. As part of the partnership, the Groove Music Pass service will be discontinued on December 31, 2017.  
After that date, Groove Music Pass content will not stream or play and our API features will not be accessible.
Please check our FAQ on <https://aka.ms/groovepartnerfaq> . All features of the Music API will be supported until Dec 31st.|



# Groove Service REST Reference  
The Groove Service delivers Groove functionality to third-party application developers for integration within their own apps.

The API follows the REST API convention and returns JSON (or XML) results. The following calling conventions are used:  

 + Parameters are provided as query parameters in the GET HTTP method. Response content is serialized in JSON by default, but can be switched to XML if the HTTP header ``` Accept: application/xml ```  is provided.  
 + The API is versioned. Version is to be prepended to the URI. Currently, all Groove RESTful API calls must begin with **/1/.**
 + Third-party developer authentication is mandatory in all methods and is done by passing an OAuth token as a mandatory query parameter in all methods.
 +  GZIP compression is supported and responses are compressed if the HTTP header ``` Accept-Encoding: gzip ``` is provided in the request.
 +   CORS is supported in the standard way, by using the headers  ```Origin ``` and  ```Access-Control-Request-*. ```
 +   JSONP is also supported via an optional query parameter, **&jsonp**=value, in all methods.
 +   Flash cross-domain calls are supported as well.
 +   Locale parameters are the same across all methods; they all have two optional query parameters, *language* and *country*, whose values are two-letter standard language and country codes. When no country information is provided via the country parameter or user authentication, the country is determined by geolocation of the caller's IP address.
 +   All APIs share a common notion of namespace that indicates the type of content referred to. Currently the only supported namespace is music.  

## URI  
|METHOD  | ENDPOINT |  USAGE | RETURNS| |
| :---|:-----|:----------| :---|:---|  
|GET|[/1/content/{id}/{source}/{browseType}/{extra}/browse](uri-browse-sub-items.md)|Browse specific sub-items of a given ID (for example, the albums of an artist or the tracks of a playlist).|[ContentResponse (JSON)](JSON-ContentResponse.md)||
|GET|[/1/content/{namespace}/catalog/genres](uri-get-genres.md)|Get a list of genres available for a locale.|[ContentResponse (JSON)](JSON-ContentResponse.md)||
|GET|[/1/content/{namespace}/catalog/{type}/browse](uri-browse-catalog.md)|Browse the music catalog.|[ContentResponse (JSON)](JSON-ContentResponse.md)||
|POST|[/1/content/{namespace}/collection/add](uri-add-track-collection.md)|Add tracks to a user's collection.|[TrackActionResponse (JSON)](JSON-TrackActionResponse.md)|[Auth](../Using-the-Groove-RESTful-Services/User-Authentication.md)|
|POST|[/1/content/{namespace}/collection/delete](uri-delete-track-collection.md)|Delete tracks from a user's collection.|[TrackActionResponse (JSON)](JSON-TrackActionResponse.md)|[Auth](../Using-the-Groove-RESTful-Services/User-Authentication.md)|
|POST|[/1/content/{namespace}/collection/playlists/create](uri-create-playlist.md)|Create a playlist on behalf of a user.|[PlaylistActionResponse (JSON)](JSON-PlaylistActionResponse.md)|[Auth](../Using-the-Groove-RESTful-Services/User-Authentication.md)|
|POST|[/1/content/{namespace}/collection/playlists/delete](uri-delete-playlist.md)|Delete a playlist of a user.|[PlaylistActionResponse (JSON)](JSON-PlaylistActionResponse.md)|[Auth](../Using-the-Groove-RESTful-Services/User-Authentication.md)|
|POST|[/1/content/{namespace}/collection/playlists/update](uri-update-playlist.md)|Update a playlist on behalf of a user.|[PlaylistActionResponse (JSON)](JSON-PlaylistActionResponse.md).|[Auth](../Using-the-Groove-RESTful-Services/User-Authentication.md)|
|GET|[/1/content/{namespace}/collection/{type}/browse](uri-browse-user-collection-playlist.md)|Browse a user's collection or playlists.|[ContentResponse (JSON)](JSON-ContentResponse.md)||
|GET|[/1/content/{id}/lookup](uri-content-lookup.md)|Look up one or several items from a media catalog and/or user's collection.|[ContentResponse (JSON)](JSON-ContentResponse.md)||
|GET|[/1/content/{namespace}/newreleases](uri-get-new-releases.md)|Discover new releases.|[ContentResponse (JSON)](JSON-ContentResponse.md)||
|GET|[/1/content/{id}/preview](uri-get-preview.md)|Request preview streaming.|[StreamResponse (JSON)](JSON-StreamResponse.md)||
|GET|[/1/content/{namespace}/search?q={query}](uri-search-content.md)|Search for items in a media catalog, user's collection, or both.|[ContentResponse (JSON)](JSON-ContentResponse.md)|[Auth](../Using-the-Groove-RESTful-Services/User-Authentication.md)|
|GET|[/1/content/{namespace}/spotlight](uri-get-spotlight.md)|Discover content for a specified language or culture.|[ContentResponse (JSON)](JSON-ContentResponse.md)||
|GET|[/1/content/{id}/stream](uri-get-stream.md)|Request streaming.|[StreamResponse (JSON)](JSON-StreamResponse.md)|[Auth](../Using-the-Groove-RESTful-Services/User-Authentication.md)|
|GET|[/1/user/{namespace}/profile](uri-access-user-profile.md)|Access a user's profile.|[UserProfileResponse (JSON)](JSON-UserProfileResponse.md)|[Auth](../Using-the-Groove-RESTful-Services/User-Authentication.md)|
|POST|[/1/content/{namespace}/radio/create](uri-create-radio.md)|Create a radio station for the user|[RadioResponse (JSON)](JSON-RadioResponse.md)|[Auth](../Using-the-Groove-RESTful-Services/User-Authentication.md)|
|GET|[/1/content/{namespace}/radio/{id}/next](uri-create-radio.md)|Continue a radio station|[RadioResponse (JSON)](JSON-RadioResponse.md)|[Auth](../Using-the-Groove-RESTful-Services/User-Authentication.md)|
|GET|[/1/content/{namespace}/radio/recentlyplayed](uri-recently-played-radio.md)|Browse a user's recently played radio stations|[ContentResponse (JSON)](JSON-ContentResponse.md)|[Auth](../Using-the-Groove-RESTful-Services/User-Authentication.md)|

## JSON
|OBJECT|DESCRIPTION|
|:---|:---|
|[Album (JSON)](JSON-Album.md)|A musical recording.|
|[Artist (JSON)](JSON-Artist.md)|The creator or creators of a musical recording.|
|[CollectionState (JSON)](JSON-CollectionState.md)|The state of the user's collection (if the request was user-authenticated).|
|[ContentItem (JSON)](JSON-ContentItem.md)|Media content (either an Album or an Artist).|
|[ContentResponse (JSON)](JSON-ContentResponse.md)|The output element for most content APIs.|
|[Contributor (JSON)](JSON-Contributor.md)|An artist and the artist's role
|[CreateRadioRequest (JSON)](JSON-CreateRadioRequest.md)|The input element for every radio station creation request
|[Error (JSON)](JSON-Error.md)|Error object for attempts to query the Music catalog.|
|[Genre (JSON)](JSON-Genre.md)|A Musical genre|
|[PaginatedList (JSON)](JSON-PaginatedList.md)|Describes paginated lists, a type of response from the Groove Service that can be continued by using a token.|
|[Playlist (JSON)](JSON-Playlist.md)|A list of tracks and their metadata.|
|[PlaylistAction (JSON)](JSON-PlaylistAction.md)|The input element for every playlist action request: create, update, and delete.|
|[PlaylistActionResponse (JSON)](JSON-PlaylistActionResponse.md)|The output element for every playlist action request: create, update, and delete.|
|[PlaylistActionResult (JSON)](JSON-PlaylistActionResult.md)|The object describing a playlist action result, used by add and delete.|
|[Radio (JSON)](JSON-Radio.md)|A radio station|
|[RadioResponse (JSON)](JSON-RadioResponse.md)|A list of tracks for a given radio along with the radio session id
|[Seed (JSON)](JSON-Seed.md)|A radio seed|
|[StreamResponse (JSON)](JSON-StreamResponse.md)|Response to all stream APIs.|
|[Track (JSON)](JSON-Track.md)|Describes a track, an individual piece of musical content from an album.|
|[TrackAction (JSON)](JSON-TrackAction.md)|An action (such as add or delete) on a specific track.|
|[TrackActionRequest (JSON)](JSON-TrackActionRequest.md)|The input element for every track action request: add and delete.|
|[TrackActionResponse (JSON)](JSON-TrackActionResponse.md)|The output element for every track action request: add and delete.|
|[TrackActionResult (JSON)](JSON-TrackActionResult.md)|The object describing a track action result, used by add and delete.|
|[UserProfileResponse (JSON)](JSON-UserProfileResponse.md)|Profile of the user, including subscription, collection, and culture information.|

## Additional material  
[Parameters common to every Groove RESTful API](Common-Parameters.md)  
	&nbsp;&nbsp;&nbsp;&nbsp; Describes the parameters common to all methods in the Groove RESTful API.  

[Extra parameters for Lookup API](Extras.md)  
	&nbsp;&nbsp;&nbsp;&nbsp;Optional query parameter that allows requesting a list of extra fields that are by default not included in the responses.  

 [Namespaces supported](Namespace.md)  
	&nbsp;&nbsp;&nbsp;&nbsp;Description of the different namespaces used across the Groove RESTful API .

[orderBy parameter for Catalog and Collection Browse APIs](OrderBy.md)  
	&nbsp;&nbsp;&nbsp;&nbsp;Allows ordering browse results in a specific order.  

[Groove RESTful API HTTP Status Codes](http-status-codes.md)   
	&nbsp;&nbsp;&nbsp;&nbsp;Describes the standard HTTP status codes that are returned by the service.
