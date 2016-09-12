# cordova-oauth
Polymer component for oauth-signin in cordova apps. It will work out of a cordova app but it is not recommended.

You will need InAppBrowser plugin correctly configured.

As described in https://developers.google.com/identity/protocols/OAuth2InstalledApp your secret key is not supposed to be secret for installed apps. Be sure to generate a clientid for installed apps (other than web). If you create a web client id (not recommended) you will need to grant permissions to redirect to localhost. 

Example for google and imgur signin.

```html
 <cordova-oauth
    id="imgursignin" 
    client_id="your-client-id"
    client_secret= "your-secret-key"
    "oauth_token_url": "https://api.imgur.com/oauth2/token",
    "oauth_authorization_url": "https://api.imgur.com/oauth2/authorize",
    acces_token="{{oauth_access_token_returned}}">
</cordova-oauth>
<cordova-oauth
    id="googlesignin" 
    scopes="profile"
    client_id="your-client-id"
    client_secret= "your-secret-key"
    "oauth_token_url": "https://accounts.google.com/o/oauth2/token",
    "oauth_authorization_url": "https://accounts.google.com/o/oauth2/auth",
    acces_token="{{oauth_access_token_returned}}"
    id_token="{{oauth_id_token_returned}}">
 </cordova-oauth>
  <script type="text/javascript">
	document.addEventListener("deviceready", onDeviceReady, false);
	function onDeviceReady() {	    
	    window.open = cordova.InAppBrowser.open;
	    document.querySelector("#cordovasignin").signIn();
	}
  </script>
```