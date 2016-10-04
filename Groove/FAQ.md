#FAQ
- [I signed up to Azure Datamarket, but my Customer ID and my Primary Account Key do not work on the Groove API. What am I doing wrong?](#1)
- [I have my application Client ID and Secret but the authentication fails. What am I doing wrong?](#2)
- [ Can I use the same Client ID and Secret for more than one application?](#3)
- [ How long does the API access token last? ](#4)
- [ Why do I get an error when trying to use the Azure Datamarket Explorer and tools?](#5)
- [ Should I actually keep the application Secret secret?](#6)
- [ How can I link to Groove from my application or website?](#7)
- [ Can I deep link to the native Groove app Windows, Windows Phone, and related platforms without going through a browser?](#8)
- [ What is the revenue share of the affiliate program?](#10)
- [ Can I become an affiliate without using the APIs? Can I use the API and not become an affiliate?](#11)
- [ Can I put advertising in my application or website if I'm using the data from the API? Can I sell my application?](#12)
- [ Can I cache the content retrieved from the API or save it locally?](#13)
- [ I want to stream music, but I can't because I need to log in a Groove user. What should I do?](#14)
- [ I want to access a Groove user's collection, but I can't because I need to log in a Groove user. What should I do?](#15)
- [ I'm coding a game. Can I use the Groove API?](#16)
- [ I keep receiving 4xx/5xx HTTP error codes in response to my requests to the API. What am I doing wrong?](#17)
- [ May I download audio files with my application and provide a download feature to my application users?](#18)
- [ I'm using the Windows Media Library on Windows Phone 8.1 to get details on the user's local files, but I can't find any art. How can I get the the images?](#19)
- [ Where did the Pilot program go?](#20)

### <a name="1"> </a> I signed up to Azure Datamarket, but my Customer ID and my Primary Account Key do not work on the Groove API. What am I doing wrong?
The Customer ID and Primary Account Key are your Azure Datamarket main account credentials. They cannot be used to authenticate on the Groove API.  

To get access to the Groove API, you must first register your application in Azure Datamarket. Make sure you provide accurate information about your application. Once registered, your application will be assigned a Client ID and a Client Secret. These credentials are the ones you should use to get a token and authenticate on the Groove API.  

Finally, make sure that you subscribed to the Groove API on Datamarket [here](http://go.microsoft.com/fwlink/p/?LinkID=389224).  

### <a name="2"> </a>  I have my application Client ID and Secret but the authentication fails. What am I doing wrong?  

Subscribe to the Groove API on Azure Datamarket [here](http://go.microsoft.com/fwlink/p/?LinkID=389224).  
. Also make sure that all parameter values in your authentication POST request are properly encoded.  

###<a name="3"> </a>Can I use the same Client ID and Secret for more than one application?
No, you should register an application in Azure Datamarket for every application or website that will use the Groove API. Every application should use its assigned Client ID and Secret. Also, make sure the details of your application are accurate.
###<a name="4"> </a>How long does the API access token last?
It lasts for 10 minutes, so you will need to refresh it before it expires. This can be done asynchronously for better performance within your app or server-side code. The expiration time is given in the response along with the token.
### <a name="5"> </a>Why do I get an error when trying to use the Azure Datamarket Explorer and tools?
The Groove API doesn't make use of the Azure Datamarket explorer and tools. You must use Azure Datamarket only to get the API authentication token. This token should then be used directly on the Groove API endpoint ```https://music.xboxlive.com.```

### <a name="6"> </a>Should I actually keep the application Secret secret?
Yes, the Secret provided by the Azure Datamarket portal should be kept secret. If you're running a website, the recommended implementation is to run the authentication code server side to prevent the secret from being visible in client-side code or on the network.

### <a name="7"> </a>How can I link to Groove from my application or website?
Most of the API calls return a "Link" item in the response. That Link is an HTTP link designed to automatically redirect to the most appropriate Groove application on the target platform. For example, if you're adding a link to a website, and the user is on a Windows 8 machine, the click from Internet Explorer will open the Groove Native application on Windows 8 (with a browser redirection)
.
### <a name="8"> </a>Can I deep link to the native Groove app Windows, Windows Phone, and related platforms without going through a browser?
Yes, you can use the deep link provided in the API response in an invisible webview control. This will give you the final music protocol Link. See [examples](https://github.com/Microsoft/Groove-API-documentation/blob/master/Using%20the%20Groove%20RESTful%20Services/Deep%20Link.md).

###<a name="10"> </a> What is the revenue share of the affiliate program?
Details of the affiliate program can be found [here](http://www.microsoftaffiliates.com/).

### <a name="11"> </a>Can I become an affiliate without using the APIs? Can I use the API and not become an affiliate?
Yes, the Groove API and affiliation are independent. The API is free to use for everyone, and gives you access to the features of Groove. There is no need to become an affiliate.  

If you'd like to earn revenue when linking to Groove from your application, then you should register with the Affiliate program.
More details are available [here](http://www.microsoftaffiliates.com/).  

You do not need to use the APIs to become a Microsoft affiliate.

### <a name="12"> </a>Can I put advertising in my application or website if I'm using the data from the API? Can I sell my application?
Please refer to [Guidelines].

###<a name="13"> </a> Can I cache the content retrieved from the API or save it locally?
Please refer to [Guidelines].

###<a name="14"> </a> I want to stream music, but I can't because I need to log in a Groove user. What should I do?
Some features of the APIs require that you authenticate a Groove user.
Please refer to the [User Authentication] documentation.

###<a name="15"> </a> I want to access a Groove user's collection, but I can't because I need to log in a Groove user. What should I do?
Some features of the APIs require that you authenticate a Groove user.
Please refer to the [User Authentication] documentation.

###<a name="16"> </a> I'm coding a game. Can I use the Groove API?
Please refer to [Guidelines].

### <a name="17"> </a>I keep receiving 4xx/5xx HTTP error codes in response to my requests to the API. What am I doing wrong?
Look at the response body. It often contains an [Error](Groove%20service%20REST%20Reference/JSON_Error.md) object with a precise description of the error case.

### <a name="18"> </a>May I download audio files with my application and provide a download feature to my application users?
No, this is not allowed according to the TOUs of the APIs. The audio may only be provided in the form of streams. This applies to all of your users, even premium users.  

Please refer to [Guidelines].

###  <a name="19"> </a>I'm using the Windows Media Library on Windows Phone 8.1 to get details on the user's local files, but I can't find any art. How can I get the the images?
On Windows Phone 8.1, images associated with local files are not available. Instead, call the image service with the MediaID you get from the local library when requesting the image.


    Example:   
    http://musicimage.xboxlive.com/content/music.<MediaIDRetreivedFromLocalLibrary>/image?locale=en-US&w=200&h=200

See also [Windows Media Library](https://msdn.microsoft.com/en-us/library/microsoft.xna.framework.media.medialibrary.aspx).

###  <a name="20"> </a>Where did the Pilot program go?
There is no need for a Pilot program anymore. You can integrate Groove in your application without even notifying us!

[Guidelines]: Using%20the%20Groove%20RESTful%20Services/Guidelines.md
[User Authentication]: Using%20the%20Groove%20RESTful%20Services/User%20Authentication.md
