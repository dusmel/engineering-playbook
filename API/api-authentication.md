Whether you prefer Postman, Paw or simply curl, it's important to be able to view Andela's API to explore and verify it's in working order. Here are the basic steps:

1. In your browser go to `http://api-prod.andela.com/login?redirect_url={INSERT ANDELA URL} `

i.e.
```
http://api-prod.andela.com/login?redirect_url=https://pulse.andela.com
```

2. Click your GSuite account of choice and on the redirect page, open up the dev console and pull the token from the cookie `jwt-token`.
3. When creating a request to the API. Use your token in a header like so:

```
Authorization: Bearer YOUR_TOKEN
```
# Resources
https://medium.com/technology-learning/how-we-solved-authentication-and-authorization-in-our-microservice-architecture-994539d1b6e6