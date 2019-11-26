**JS SDK integration**

Create a developer account using facebook.developers.com. Now add an app > select web (www) and then enter a site url, 
`https://localhost` would suffice.
Now copy the snipped from the next step and replace the app id and add it next to the start of body tag.

`
<script>
    window.fbAsyncInit = function () {
      FB.init({
        appId: '1813842465324998',
        autoLogAppEvents: true,
        xfbml: true,
        version: 'v2.11'
      });

      // Broadcast an event when FB object is ready
      var fbInitEvent = new Event('FBObjectReady');
      document.dispatchEvent(fbInitEvent);
    };

    (function (d, s, id) {
      var js, fjs = d.getElementsByTagName(s)[0];
      if (d.getElementById(id)) { return; }
      js = d.createElement(s); js.id = id;
      js.src = "https://connect.facebook.net/en_US/sdk.js";
      fjs.parentNode.insertBefore(js, fjs);
    }(document, 'script', 'facebook-jssdk'));
  </script>
`


Now I have a component called SocialLogins which holds the social login status. So once the component is mounted, 
i will check for login status.

``
  React.useEffect(() => {
    if (isBrowser()) {
      const FB = (window as any).FB;

      FB.getLoginStatus(function(response: any) {
        console.log('TCL: SocialLogin -> status', response.status);
        if (response.status == 'connected') {
          setIsLoggedIn(true);
          FB.api('/me', { fields: 'name,email' }, (userData: ReactFacebookLoginInfo) => {
            setName(userData.name);
            setEmail(userData.email);
          });
        }
      });
    }
  }, []);
``

So, once I have the FB object I will call the `getLoginStatus` API and get the reponse. 'connected' means user is authentica
cated already. unknown means user is logged out now. In the above code, I am calling the Facebook Graph API to get the 
name and email. 
