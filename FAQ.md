#FAQ
- [I signed up to Azure Datamarket, but my Customer ID and my Primary Account Key do not work on the Groove API. What am I doing wrong?] (#1)
- I have my application Client ID and Secret but the authentication fails. What am I doing wrong?
- Can I use the same Client ID and Secret for more than one application?
- How long does the API access token last? 
- Why do I get an error when trying to use the Azure Datamarket Explorer and tools?
- Should I actually keep the application Secret secret?
- How can I link to Groove from my application or website?
- Can I deep link to the native Groove app Windows, Windows Phone, and related platforms without going through a browser?
- I'd like to become an affiliate but the documentation asks me to register on an external site called "Linkshare" that doesn't look like Microsoft. Can I trust that site?
- What is the revenue share of the affiliate program?
- Can I become an affiliate without using the APIs? Can I use the API and not become an affiliate?
- Can I put advertising in my application or website if I'm using the data from the API? Can I sell my application?
- Can I cache the content retrieved from the API or save it locally?
- What's the Groove API Pilot?
- I want to stream music, but I can't because I need to log in a Groove user. What should I do?
- I want to access a Groove user's collection, but I can't because I need to log in a Groove user. What should I do?
- I'm coding a game. Can I use the Groove API?
- I keep receiving 4xx/5xx HTTP error codes in response to my requests to the API. What am I doing wrong?
- I'm part of the Pilot. May I distribute my application publicly?
- May I download audio files with my application and provide a download feature to my application users?
- I'm using the Windows Media Library on Windows Phone 8.1 to get details on the user's local files, but I can't find any art. How can I get the the images?

### <a name="1"> </a> I signed up to Azure Datamarket, but my Customer ID and my Primary Account Key do not work on the Groove API. What am I doing wrong?
The Customer ID and Primary Account Key are your Azure Datamarket main account credentials. They cannot be used to authenticate on the Groove API.
To get access to the Groove API, you must first register your application in Azure Datamarket. Make sure you provide accurate information about your application. Once registered, your application will be assigned a Client ID and a Client Secret. These credentials are the ones you should use to get a token and authenticate on the Groove API.
Finally, make sure that you subscribed to the Groove API on Datamarket here.  

### I have my application Client ID and Secret but the authentication fails. What am I doing wrong?  

Subscribe to the Groove API on Azure Datamarket here. Also make sure that all parameter values in your authentication POST request are properly encoded.  

###Can I use the same Client ID and Secret for more than one application?
No, you should register an application in Azure Datamarket for every application or website that will use the Groove API. Every application should use its assigned Client ID and Secret. Also, make sure the details of your application are accurate.
###How long does the API access token last? 
It lasts for 10 minutes, so you will need to refresh it before it expires. This can be done asynchronously for better performance within your app or server-side code. The expiration time is given in the response along with the token. 
### Why do I get an error when trying to use the Azure Datamarket Explorer and tools?
The Groove API doesn't make use of the Azure Datamarket explorer and tools. You must use Azure Datamarket only to get the API authentication token. This token should then be used directly on the Groove API endpoint https://music.xboxlive.com.
### Should I actually keep the application Secret secret?
Yes, the Secret provided by the Azure Datamarket portal should be kept secret. If you're running a website, the recommended implementation is to run the authentication code server side to prevent the secret from being visible in client-side code or on the network.
### How can I link to Groove from my application or website?
Most of the API calls return a "Link" item in the response. That Link is an HTTP link designed to automatically redirect to the most appropriate Groove application on the target platform. For example, if you're adding a link to a website, and the user is on a Windows 8 machine, the click from Internet Explorer will open the Groove Native application on Windows 8 (with a browser redirection).
### Can I deep link to the native Groove app Windows, Windows Phone, and related platforms without going through a browser?
Yes, you can use the deep link provided in the API response in an invisible webview control. This will give you the final music protocol Link. See examples.
### I'd like to become an affiliate but the documentation asks me to register on an external site called "Linkshare" that doesn't look like Microsoft. Can I trust that site?
Yes, Linkshare is the Affiliation platform that Groove is partnering with to provide its affiliation program. Linkshare runs affiliation programs for many companies. The Groove affiliation program will be listed in the Linkshare portal after you register. You can apply to it from there.
### What is the revenue share of the affiliate program?
This is described in the Groove program presentation page on Linkshare.
### Can I become an affiliate without using the APIs? Can I use the API and not become an affiliate?
Yes, the Groove API and affiliation are independent. The API is free to use for everyone, and gives you access to the features of Groove. There is no need to become an affiliate.
If you'd like to earn revenue when linking to Groove from your application, then you should register with the Affiliate program. To start earning revenue, you'll need to tweak the Link to Groove with your Linkshare affiliate Id. There are more details available here.
You do not need to use the APIs to become an affiliate. You can use the links and promotional resources provided on Linkshare or even build your own links.
### Can I put advertising in my application or website if I'm using the data from the API? Can I sell my application?
Please refer to Guidelines.
### Can I cache the content retrieved from the API or save it locally?
Please refer to Guidelines.
### What's the Groove API Pilot?
The Pilot is a program that we're running with selected partners. It gives developer access to an extended set of Features. The Pilot was presented at the 2014 //Build conference. You can watch the talk and get more details here.
If you want to be part of the pilot, please visit this link.
### I want to stream music, but I can't because I need to log in a Groove user. What should I do?
Some features of the APIs require that you authenticate a Groove user. For the moment, this is restricted to partners that are part of the pilot. To apply follow the process explained here.
### I want to access a Groove user's collection, but I can't because I need to log in a Groove user. What should I do?
Some features of the APIs require that you authenticate a Groove user. For the moment, this is restricted to partners that are part of the pilot. To apply follow the process explained here.
### I'm coding a game. Can I use the Groove API?
Please refer to Guidelines.
### I keep receiving 4xx/5xx HTTP error codes in response to my requests to the API. What am I doing wrong?
Look at the response body. It often contains an Error object with a precise description of the error case.
### I'm part of the Pilot. May I distribute my application publicly?
Yes. You may deploy and distribute your application as long as you comply with the TOUs and agreement signed with Microsoft. However, you may not distribute or publish the source code of your application.
### May I download audio files with my application and provide a download feature to my application users?
No, this is not allowed according to the TOUs of the APIs. The audio may only be provided in the form of streams. This applies to all of your users, even premium users.
Please refer to Guidelines.
### I'm using the Windows Media Library on Windows Phone 8.1 to get details on the user's local files, but I can't find any art. How can I get the the images?
On Windows Phone 8.1, images associated with local files are not available. Instead, call the image service with the MediaID you get from the local library when requesting the image.


    Example: http://musicimage.xboxlive.com/content/music.<MediaIDRetreivedFromLocalLibrary>/image?locale=en-US&w=200&h=200 

See also [Windows Media Library](https://msdn.microsoft.com/en-us/library/microsoft.xna.framework.media.medialibrary.aspx).
