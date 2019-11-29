Fastify vs Express - Fastify is 20% faster
https://medium.com/@onufrienkos/express-vs-fastify-performance-4dd5d73e08e2

but in support express > fastify
https://www.npmtrends.com/express-vs-fastify-vs-restify

Fastify + server side auth = bad. 
Can i use passport in fastify, like i use it in express? #1350
https://github.com/fastify/fastify/issues/1350
There are no ready made strategies available but fastify-auth ( This module does not provide an authentication strategy,
but it provides a very fast utility to handle authentication (also multiple strategies) in 
your routes, without adding overhead. ) is available.

and this guy is https://github.com/fastify/fastify-oauth2 for the old style social login where the user is redirected to
the facebook age and comes back to our page. not that fancy.

So to get the advantage of fastness of fastify, we could write our own validation logic of userToken at our server for now.
If someday we start to support so many social logins, fastify might have more auth strategy verification at the backend
or we could switch to express at the expense of the speed of the services. But since the server side auth can be done is a 
REST api call, i think its good to do it this way, since we get the advantage of speed.
