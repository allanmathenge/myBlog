---
title: The actual Auth Process
date: 2023-08-15 05:57:33
tags:
---

## Introduction

While I have written on auth logic, it does not protect the endpoints. In Auth2.0 article we learned how to generate the Access and Refresh tokens, authenticate the user using the tokens and the related the precautions. This article will discuss the jsonwebtoken middleware that protect the endpoints with the Refresh and Access tokens. The middleware verify these endpoints every time we make a request to the protected endpoints. We will use '/user' and '/refresh' protected endpoints using '/auth' route to access the data stored in our database. We will use Postman to test these endpoints. Included in this article are illustrations using the actual code and the requests made on Postman.


## Verify JWT (jsonwebtoken)

JWT middleware verify the valid token, everytime we make a request to a protected endpoint.

### Auth headers

Auth header provides data origin authentication. The header of the request may have authorization or Authorization header ( 'a' or 'A'). There is no requirement or standard way hence we include both in the middleware.

What is required is a starndard way of providing auth header. We will verify the value of the auth header if it starts with "Bearer ". If it does not, we throw an unauthorized response. We call the split(' ')[1] method to access the value of the token that follows the bearer keyword.

    const authHeader = req.headers.authorization || req.headers.Authorization
        if (!authHeader?.startsWith('Bearer ')) {
            return res.status(401).json({ message: 'Unauthorized'})
        }
        const token = authHeader.split(' ')[1]

### Verifying the token

If we have the token we pass the token in jwt.verify and verify using Access Token.

    jwt.verify(
        token,
        process.env.ACCESS_TOKEN_SECRET,
        (err, decoded) => {
            if (err) return res.status(403).json({ message: 'Forbidden'})
            req.user = decoded.UserInfo.username
            next()
        }
    )

When have the token value, we will send it to decoded.UserInfo.username. We call the next() middleware in line.

## Protecting the routes

We will use the middleware above to protect the user routes for GET and POST methods.

    const verifyJWT = require('./verifyJWT')

    router.use(verifyJWT)

    router.route('/')
        .get(userController.getAllUsers)
        .post(userController.createNewUser)

    module.exports = router

NOTE: *The ***userController*** file imported here handles the request logic. The req method has its corresponding request logic from that file. Example in the userController, the POST request corresponds to createNewUser logic in the UserController File.* [Link to that file on GitHub](https://github.com/allanmathenge/mern_stack/tree/main/controllers)

## Using Postman

Make sure your backend code is running on localhost. Make the following settings on postman to ensure no errors while sending requests.

![Postman setup](/img/postman.jpg 'Content-type: Application/json, Authorization: "Bearer "')

I have used '/auth' endpoint as per the Rest api I have written. Click on Body tab the click raw, and send data as shown:

![Access Token](/img/postman_access_token.jpg 'Access Token')

Send and receive have the accessToken as the response. Click on cookies at the top right at the cookie manager and note the cookie.

![Secure Cookie](/img/cookies_access_token.jpg 'Cookie')

Remove the 'secure' because we only have httpOnly cookie in development, in production we leave the cookie with secure value.
Because we now have the cookie we, can navigate to '/auth/refresh'and have another access token because our refresh token was valid.

on the Headers on postman *{see Postman set up}* key: Authorization  value: Bearer (leave space) and paste the access token received before the expiry time. When we send the the '/user' request on Postman we receive the resources stored on our database. On expiry we send a refresh token to get a new access token.

## Conclusion

The process of authentication discussed depends heavily on the authenticity of the tokens received by the endpoints. If the Token is authentic the user is granted access to the protected routes. Otherwise, the user is blocked from having acccess to the protected routes. JWT middleware ensures that happens without failure. In case one of the tokens are missing, expired or tampred with, the user will be blocked from accessing the protected routes. When the auth process is successful, the user is granted access to the routes of the protected resources or data. We can automate this process which eliminates the need for users to authenticate themselves when the access Token expires.

<script async src="https://talk.hyvor.com/embed/embed.js" type="module"></script>
<hyvor-talk-comments website-id="9352" page-id=""></hyvor-talk-comments>