---
title: Get started with the Groove SDK| Groove Services
description:  Learn how to subscribe to the Groove API and get started developing with Groove.
keywords: groove music, groove api, groove sdk
author: sakley
ms.assetid: bb08eb18-7a26-44a6-7181-ee673b0b04c2
---

# Getting Started with the Groove SDK
## Subscribe to the Groove API on Microsoft Developer Center
The following are the minimal steps you need to complete to start experimenting with the API (for more detailed instructions, visit [Obtaining a Developer Access Token](Using-the-Groove-RESTful-Services/Obtaining-a-Developer-Access-Token.md)).

[Dev Center Signin]: site-images/dev-center-signin.png
[Dev Center Signin Account]: site-images/dev-center-signin-account.png
[Groove Dev Center]: site-images/groove-dev-center.png
[Groove signup]: site-images/groove-signup.png
[Register your app]: site-images/register-your-app.png

1. Visit <https://developer.microsoft.com/groove>. Click on sign-in. ![Dev Center Signin]
2. Sign in with your Microsoft account or create a Microsoft account if you don't already have one.![Dev Center Signin Account]
3. On <https://developer.microsoft.com/groove>, click the **Sign up** link ![Groove Dev Center] or visit <https://developer.microsoft.com/dashboard/groove>.
4. Fill in the correct details about you carefully - we'll need your valid email address to contact you. ![Groove signup] 
5. Read the [Terms Of Use](groove-api-terms-of-use.md) and accept them. Then click on **Subscribe to Groove Music API Program**.

You are now a member of the Groove Music API Program!
You will now need to associate Applications to your account.

## Register and associate a Microsoft Account application
### Create an application 

To register your app to connect with Groove, you'll need a Microsoft account.

1. Go to the [Microsoft Application Registration Portal](https://account.live.com/developers/applications)
2. When prompted, sign in with your Microsoft account credentials.
3. Find My applications and click Add an app.
4. Enter your app's name and click Create application.
5. Scroll to the bottom of the page and check the Live SDK support box.

After you've completed these steps, an application ID and application secret are created for your app and displayed on your new app's properties page.

**Important** Treat the value of client secret the same as you would a user's password. The secret represents the key to your application and, if made available, can be used to impersonate your application.

Under the Platforms header, configure details about your app. By default a new app is created as a web app and needs one or more redirect URIs. To enable native client flows for your app as well, click the Add Platform button and choose Mobile.

### Allow this application to access Groove Music API

1. When signed-in to the developer center, on <https://developer.microsoft.com/groove>, click the **Sign up** link or visit <https://developer.microsoft.com/dashboard/groove>.
2. Follow the instructions on the page. You'll need to obtain an authentication token (see below) ![Register your app]
3. Enter the obtained authentication token in the field and click on Register.
**TODO: include sample**
4. You can register up to xx apps. You can manage them on this page. 
**TODO: include screenshot with dashboard rempli**

#### Getting an authentication token
The request consists of a form encoded POST call to
https://login.live.com/accesstoken.srf with parameters:

| Parameter name  | Value  | Description                                                                              |
|:---------------:|:------:|:-----------------------------------------------------------------------------------------|
| *grant_type*    | string | Use "client" as value for application token authentication. |
| *client_id*     | string | Your Application ID as displayed on your application page on the [Microsoft Application Registration Portal](https://account.live.com/developers/applications) |
| *client_secret* | string | Your Application Secret as displayed on your application page on the [Microsoft Application Registration Portal](https://account.live.com/developers/applications). The value needs to be URL encoded. |
| *scope*         | string | The scope your application requires. For application access to the Groove API the scope is "app.music.xboxlive.com" |

```
POST https://login.live.com/accesstoken.srf HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.live.com
Content-Length: 123

grant_type=client_credentials&client_id={APP ID HERE...}&client_secret={CLIENT SECRET HERE...}&scope=app.music.xboxlive.com
```

If the application id and secret values are correct, the service will
reply with a JSON object containing the token type, the access token's
value and an expiry delay.

```
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 524

{"token_type":"bearer","access_token":"Eg...==","expires_in":86400}
```

The resulting application access token can then be used in application
calls using the OAuth 2.0 bearer authorization method.

Note that tokens expire. Applications should take token expiry into
account and reauthenticate before access token expiry.

**Important:** Treat the value of `access_token` in this response as
securely as you would a user's password.


#####Using Powershell on Windows:#####

```powershell
> Invoke-WebRequest -Uri https://login.live.com/accesstoken.srf -Method Post -Body "grant
_type=client_credentials&client_id={APP ID HERE...}&client_secret={CLIENT SECRET HERE...}&scope=app.music.xboxlive.com"|ConvertFrom-Json|Format-List

token_type   : bearer
access_token : Eg...
expires_in   : 86400
```

#####Using curl:#####

```
% curl https://login.live.com/accesstoken.srf -d "grant_type=client_credentials&client_id={APP ID HERE...}&client_secret={CLIENT SECRET HERE...}&scope=app.music.xboxlive.com"
{"token_type":"bearer","access_token":"Eg...","expires_in":86400}
```

#####Using wget:#####

```
% wget https://login.live.com/accesstoken.srf --post-data "grant_type=client_credentials&client_id={APP ID HERE...}&client_secret={CLIENT SECRET HERE...}&scope=app.music.xboxlive.com" -q -O -
{"token_type":"bearer","access_token":"Eg...","expires_in":86400}
```
  
## Start using our API
 
 You can now copy and paste your preferred sample code from below (C#, Windows Runtime or PHP) to start querying the API for Music data.

####For example:####

```
GET https://music.xboxlive.com/1/content/music/search?q=hello HTTP/1.1
Accept: application/json
Authorization: Bearer Eg...==
Host: music.xboxlive.com
```

TODO: update code samples
### Windows
```csharp
 //datamarket authentication endpoint, must be https
string service = "https://datamarket.accesscontrol.windows.net/v2/OAuth2-13";

 //the clientId from step 5
string clientId = "myClient";

 //the secret from step 5
string clientSecret = "REDACTED";
string clientSecretEnc = System.Uri.EscapeDataString(clientSecret);

 //will be used to store the authentication token
string token = null;
string tokenEnc = null;
HttpWebRequest request = null;
HttpWebResponse response = null;

 // scope used for authentication. NOTE: http. not https here!
string scope = "http://music.xboxlive.com";
string scopeEnc = System.Uri.EscapeDataString(scope);

string grantType = "client_credentials";

 //preparing the data for authentication
string postData = "client_id=" + clientId + "&client_secret=" + clientSecretEnc + "&scope=" + scopeEnc + "&grant_type=" + grantType;

  static string SendRequest(string method, string service, string postData)
  {

      string responseString = null;
      HttpWebRequest request = (HttpWebRequest)WebRequest.Create(service);

      UTF8Encoding encoding = new UTF8Encoding();
      byte[] data = encoding.GetBytes(postData);

      request.Method = method;
      request.ContentType = "application/x-www-form-urlencoded";
      request.ContentLength = data.Length;

      using (Stream stream = request.GetRequestStream())
      {
          stream.Write(data, 0, data.Length);
      }

      using (HttpWebResponse response = (HttpWebResponse)request.GetResponse())
      {
          responseString = new StreamReader(response.GetResponseStream()).ReadToEnd();
      }

      return responseString;
  }

 //send the authentication request
string responseString = SendRequest("POST", service, postData);

static string ExtractTokenFromJson(string json)
  {
      string token = null;
      Match match = Regex.Match(json, ".*\"access_token\":\"(?<token>.*?)\".*", RegexOptions.IgnoreCase);
      if (match.Success)
      {
          token = match.Groups["token"].Value;
      }
      return token;
  }

 //token to use to authenticate aginst the Groove API
token = ExtractTokenFromJson(responseString);

 //token will be used in the REST call, it hsould be encoded
tokenEnc = HttpUtility.UrlEncode(token);

 //and the request to the API (Note: the API endpoint is https)
  request = (HttpWebRequest)WebRequest.Create("https://music.xboxlive.com/1/content/music/search?q=daft+punk&accessToken=Bearer+" + tokenEnc);
  request.Method = WebRequestMethods.Http.Get;
  request.Accept = "application/json";
  using (response = (HttpWebResponse)request.GetResponse())
  {
      using (var sr = new StreamReader(response.GetResponseStream()))
      {
          responseString = sr.ReadToEnd();
      }
  }
Console.WriteLine(responseString);
```

### Windows Runtime
```csharp
    using System;
    using System.Net;
    using System.Text.RegularExpressions;
    using System.Collections.Generic;
    using System.Diagnostics;
    using Windows.Web.Http;

    namespace RestTest
    {
      public class Test
      {
          public static async void Go()
          {
              var client = new HttpClient();

              // Define the data needed to request an authorization token.
              var service = "https://datamarket.accesscontrol.windows.net/v2/OAuth2-13";
              var clientId = "myClient";
              var clientSecret = "REDACTED";
              var scope = "http://music.xboxlive.com";
              var grantType = "client_credentials";

              // Create the request data.
              var requestData = new Dictionary<string, string>();
              requestData["client_id"] = clientId;
              requestData["client_secret"] = clientSecret;
              requestData["scope"] = scope;
              requestData["grant_type"] = grantType;

              // Post the request and retrieve the response.
              var response = await client.PostAsync(new Uri(service), new HttpFormUrlEncodedContent(requestData));
              var responseString = await response.Content.ReadAsStringAsync();
              var token = Regex.Match(responseString, ".*\"access_token\":\"(.*?)\".*", RegexOptions.IgnoreCase).Groups[1].Value;

              // Use the token in a new request.
              service = "https://music.xboxlive.com/1/content/music/search?q=daft+punk&accessToken=Bearer+";
              response = await client.GetAsync(new Uri(service + WebUtility.UrlEncode(token)));
              responseString = await response.Content.ReadAsStringAsync();
              Debug.WriteLine(responseString);
          }
       }
    }
```

### PHP
```php
class GrooveMusic {
      var $serviceauth = "https://datamarket.accesscontrol.windows.net/v2/OAuth2-13";
      var $serviceapi = "https://music.xboxlive.com/1/content";
      var $clientId = "yourclientID";
      var $clientSecret = "yourapplicationclientsecret";
      var $scope = "http://music.xboxlive.com";
      var $grantType = "client_credentials";

      public function auth() {
          $requestData = array("client_id" => $this->clientId, "client_secret" => $this->clientSecret, "scope" => $this->scope, "grant_type" => $this->grantType);
          $options = array(
              'http' => array(
                  'header'  => "Content-type: application/x-www-form-urlencoded\r\n",
                  'method'  => 'POST',
                  'content' => http_build_query($requestData),
              ),
          );
          $context  = stream_context_create($options);
          $response = json_decode(@file_get_contents($this->serviceauth, false, $context),true);
          $token = $response['access_token'];
          return $token;
      }

      public function search($string,$token) {
          $url = $this->serviceapi.'/music/search?q='.urlencode($string).'&accessToken=Bearer+'.urlencode($token);
          $response = @file_get_contents($url);
          return $response;
      }

      public function lookup($ids_array,$token, $extras = '') {
          $string = '';
          foreach($ids_array as $value) {
              $string .= $value.'+';
          }
          $string = rtrim($string, '+');
          if(!empty($extras)) $url = $this->serviceapi.'/'.$string.'/lookup?accessToken=Bearer+'.urlencode($token).'&extras='.$extras;
          else $url = $this->serviceapi.'/'.$string.'/lookup?accessToken=Bearer+'.urlencode($token);
          $response = @file_get_contents($url,true);
          return $response;
      }

  }

//using the class
$MusicAPI = new GrooveMusic;
$token = $MusicAPI->auth();
$json_response = $MusicAPI->search("madonna", $token);
```
