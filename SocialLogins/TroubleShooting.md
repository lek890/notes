Although facebook documentation says it allows usage locally without https when 
the facebook app we registered is in development mode, it didn't work for me.

When I integrated the `facebook-login-react` component, it did work, but the initial `getLoginStatus` call didn't 
get through. It gave me the https only usage error.

So I had to integrate a self signed certificate for that. Which was tricky because I had to edit the way my server
started.

Two steps:
1. Create, sign and add certificates to chrome
2. Change app to incorporate the certificates when it starts


 
