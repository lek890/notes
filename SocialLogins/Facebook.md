FB login is a fast way to create accounts for users and give them access to you app. Its available for most platforms.

Facebook login enables two scenarios:
1. Authentication
2. Asking for permission to access data

One could use Facebook Login for both or either one of the above.

Use cases:
1. Account creation - This is an easy way with wich people could quickly create an account in your app without having 
to remember an username and password separately. Once account is created, you could reach out the user at his email address
easily
2. Personalization - Access data for personalization and give a personalized experience
3. Social - for shared in app experiences, where people could connect to their friends.

Facebook login for the web using


**Authentication vs Data access**
https://developers.facebook.com/docs/facebook-login/auth-vs-data

Authentication enables people to login in to your app and create an accound using their facebook credentials. They dont 
need to create or remember a new password.

Expiration?
When facebook authentication happens, the app recieves a user access token. if you use one of facebooks sdks, the token
lasts for about 60 days. it gets renewed on every usage, so the tokens expire after 60 days of last usage. If you do not 
use facebook sdk, then you need to do it yourself using the login flow.

Data Access
Facebooks enables to ask for permission when people login to your app. If you ask for non public info, you need to go through an app review on facebook. Name, photo and email can be used without any reviews.

Expiration?
90 days from the last active date. After this 90 days, even when authenticated, you cannot access any data without the 
permission being re-authorized.

To ask for reathorization in js SDK use, 
``
FB.login(function(response) {
  // Original FB.login code
}, { auth_type: 'reauthorize' })
``

**Access tockens**
An access token identifies an app or user to make graph API calls. So once an user authenticates and gets necessary 
permissions, the app receives an access tocken that provides temporaty access to Facebook Api's.

There are 4 types of tockens
1. User access token - to read and write a persons fb data
2. App access token - modify and read app settings
3. Page access token - similar to user access token except that it is for a fb page. To get this, first you should get a user token and then ask for this tocken
4. Client token - token that is embedded into apps for identification fo your app.

We will tak more about User access token here
User access token - long term and short term
Short term tokens has a lifetime of an hour or two. Long lived has about 60 days. This may vary and is not gaurenteed.
Tokens generated via web login are short lived. You could convert them into long lived using a server side api call.
Mobile apps get long lived tokens by default.

Portable - so you can pass the user acess token to backend  or vice versa over https.

``
FB.getLoginStatus(function(response) {
  if (response.status === 'connected') {
    var accessToken = response.authResponse.accessToken;
  } 
} );

``


