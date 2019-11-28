Using web tokens in Node.js

One of the challenges when providing an API is authentication. In traditional web applications, the server responds to 
a successful authentication request by doing two things. First, it creates a session using some storage mechanism. Each 
session has its own identifier – usually a long, semi-random string – which is used to retrieve information about 
the session on future requests. Secondly, that information is sent to the client by way of headers instructing it 
to set a cookie. The browser automatically attaches the session ID cookie to all subsequent requests, allowing the 
server to identify the user by retrieving the appropriate session from storage. This is how traditional web applications
get around the fact that HTTP is stateless.

Securing APIs?

One is to use HTTP Basic Authentication. Defined in the official HTTP specification, this essentially involves setting
a header on the server response which indicates authentication is required. The client must respond by attaching their 
credentials, including their password, to every subsequent request. If the credentials match, the user information is
made available to the server application as as variable.

The second approach is very similar, but using the application’s own authentication mechanism. This usually involves
checking the supplied credentials against those in storage. As with HTTP Basic Authentication, this requires that the
user’s credentials are supplied with each and every call.

The third approach is OAuth (or OAuth2). Designed to a large extent for authenticating against third-party services, 
it can be rather challenging to implement, at least on the server-side.

A fourth approach is using tokens. That’s what we’re going to look at in this article. We’ll look at an 
implementation that utilizes JavaScript on both the front and back ends.

https://www.sitepoint.com/using-json-web-tokens-node-js/
