---
title: Deep linking to Groove Music content| Groove Services
description:  Learn how to use deep linking for Groove music integration.
keywords: groove music, groove api, groove deeplinks
author: sakley
ms.assetid: 447e555b-1340-da86-c792-88abeaa921d1
---

# Deep Link
## Introduction
The Link property of every piece of content returned by content APIs is the key for third-party integration with Groove applications: it contains a deep link that opens the piece of content on a Groove client. These links exist and are used within Groove applications for sharing the pages of artists, albums, and tracks. (See the table of examples in this topic.) They open native applications, such as the Windows 10 Groove application, Windows Phone 10 Groove application, the Windows Store and the *https://music.microsoft.com* web client, depending on the user's platform.    

The template of the redirect URL is as follows:   

```
https://music.microsoft.com/{type}/{Id}?action={action}&target={target}
```

The parameters *type* and *Id* are the only mandatory parameters to identify the content to point to.  

|Parameter|Type|Description|
|:----|:----|:----|
|type|enum|Type of content being redirected to; see table of enumerations in this topic.|
|id|string|ID of the item. Parameter type depends on the value of the type parameter.|
|action|enum|Optional action to apply when opening the content. See the table below for possible values and corresponding actions. |
|target|enum|Optional choice of preferred target application. This parameter depends on a lot of different factors, so it is honored only as best-effort. See the table below for possible values and corresponding actions.|

#### Type parameter list of possible values for deep links   
|Value|Description|
|:----|:----|
|Album|Music album|
|Artist|Music artist|
|Playlist|List of tracks and their metadata|
|Track|Music song|

The *action* parameter is optional.

#### Action parameter
|Value|Description|Fallback when not supported|
|:----|:----|:----|
|view|Default. Launches the content details view.|Groove marketing page|
|play|Launches playback of the media content.|"view" experience|
|buy|Opens the appropriate purchase flow on the Groove service.|"view" experience|
The *target* parameter is optional.  

You can influence the behavior of the redirect by adding the target query parameter in the deep link. The redirect will try to honor that parameter if it makes sense and is possible. However, it is a best effort and might be overridden by our spec choices (for example, on Windows Phone 10, since the Groove app is always installed, we will always try to redirect to it). You shouldn't assume this parameter will always be honored.

If the target parameter is not provided, the redirect will by default open the best available experience on the user's device.

#### Target parameter
|Value|Description|
|:----|:----|
|app|Force opening a rich application if available on the user's device.|
|web|Force opening the [web client](http://www.music.microsoft.com) if supported on the user's web browser.

#### Examples
|Entity|URL pattern|Example URL|
|:----|:----|:----|
|Artist|https://music.microsoft.com/Artist/xxx|https://music.microsoft.com/Artist/07070000-0200-11db-89ca-0019b92a3933|
|Album|https://music.microsoft.com/Album/xxx?action=yyy|https://music.microsoft.com/Album/bcafef07-0100-11db-89ca-0019b92a3933?action=play|
|Track|https://music.microsoft.com/Track/xxx?action=yyy|https://music.microsoft.com/Track/c1afef07-0100-11db-89ca-0019b92a3933?action=buy|

## App-to-app direct linking
In Windows 10 we currently don't support direct app-to-app linking. We recommend launching the deeplink in a browser which will handle opening the native application in some cases:

```csharp
string deeplink = content.Link;
await Launcher.LaunchUriAsync(new Uri(deeplink));
```
