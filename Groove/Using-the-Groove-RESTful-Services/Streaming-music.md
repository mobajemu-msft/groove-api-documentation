# Streaming music
To stream a full music track you need an authenticated user with an active Groove Music Pass subscription.
See [User Authentication] for more details on how to authenticate users.
Once you have a user token, you should check if the user has an active Groove Music subscription. See [/1/user/music/profile].
If the user has a subscription, you can stream full music tracks. See [/1/content/{id}/stream].

If the user doesn't have a subscription or no user is signed-in, you can get access to a 30-second sample of all the music tracks. See [/1/content/{id}/preview].

 [/1/content/{id}/preview]: ../Groove-service-REST-Reference/URI_ContentNamespacePreviewGET.md
 [/1/content/{id}/stream]: ../Groove-service-REST-Reference/URI_ContentNamespaceStreamGET.md
 [User Authentication]: User-Authentication.md
