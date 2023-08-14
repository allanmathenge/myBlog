---
title: Auth2.0
date: 2023-08-14 04:40:24
tags:
---

## Introduction

Auth is the first line of security to all protected routes of a website. The protcted routes have resources that only authorized users are allowed to access. Auth uses two main security features to authenticate and authorize users namely, refresh and access token. Users are welcome in the website's public page. The credentials users provided as username and password are used to authenticate, or make and identification of who they are. In this article we will explore the process user authorization using the above named security fetures.


### JSON web token

TWT - JSON web token is a reference form of user identification. The token is issued by the app user after the initial user login to confirm authentication. Before running the following commands on terminal make sure you have Node.js installed and an IDE of your choice. I am using Visual Studio code.

``` bash
    $ npm install jsonwebtoken
```

After installation process is successful and complete, open the terminal and type.

    ```bash
        $ require('crypto').randomBytes(64).toString('hex')
    ```
Press enter and we get a secret key. The token looks like this:

    ```
    d0ab0916deb78735acc1c839f082e8e4f04414f410e2d450138bd76d65608a16f09c2c1fb595ad06438c2c37b7773877c4724897ebe9d203e181c477b55ee75d
    ```

Copy and paste it as your ACCESS_TOKEN_SECRET on your .env file. Press an up arrow(^) + enter and get another token and name it REFRESH_TOKEN_SECRET


## Refresh and Access Tokens

After login and complete authentification of the user, rest API will issue an access token and a refresh token.

### Access Token

The received access token is given a short time before it expires, for example 5 to 15 minutes. Rest api send and receive access token in form of JSON.

    const accessToken = jwt.sign(
        {
            "UserInfo": {
                "username": foundUser.username,
                "roles": foundUser.roles
            }
        },
        process.env.ACCESS_TOKEN_SECRET,
        { expiresIn: '10s'}
    )
    res.json({ accessToken })

Access token is stored in application's state or memory. It should NOT be stored in Local storage as hackers can access or retrieve and use it to gain indefinite access to our protected routes. Access token is lost when the app is closed.

### Refresh Token

Refresh token is issued after authentification and takes a longer time duration of several hours or day(s) before it expires. In my code below it will take a week before expiring. 

    // Create secure cookie with refresh token. 'jwt' is its key name to be used below in refresh token below.

    res.cookie('jwt', refreshToken, {
        httpOnly: true, // accessible only by web server
        secure: true, // https
        sameSite: 'None', // cross-site cookie
        maxAge: 7 * 24 * 60 * 60 * 1000 // cookie expiry set to match refreshToken (1 week)
    })

    // Send accessToken containing username and roles
    res.json({ accessToken })

It is sent as httpOnly cookie. httpOnly cookie is not accessible via JavaScript and must be allowed to expire.

Refresh token must not be allowed to issue access token as that will grant indefinite access.

### Refresh Token with middleware

The user (client) uses the Access Token until it expires. It is verified with a middleware and new access token is issued at refresh request.

<code>
    const refresh = (req, res) => {
        const cookies = req.cookies

        if (!cookies?.jwt) return res.status(401).json({ message: 'Unauthorized!'})

        const refreshToken = cookies.jwt

        jwt.verify(
            refreshToken,
            process.env.REFRESH_TOKEN_SECRET,
            async (error, decoded) => {

                if (error) return res.status(403).json({ message: 'Forbidden'})

                const user = await User.findOne({ username: decoded.username}) // find the user with the provided credentials

                if (!user) return res.status(401).json({ message: 'Unauthorized!'})

                const accessToken = jwt.sign(
                    {
                        "UserInfo": {
                            "username": user.username,
                        }
                    },
                    process.env.ACCESS_TOKEN_SECRET,
                    { expiresIn: '10s'}
                )
                res.json({ accessToken })
            }
        )
    }
</code>

If the access token is valid new Access Token is issued to the users application. 

Note: When the Access Token expires, the user application will not need to send refresh token to the Rest API refresh endpoint to be granted new access.

## Conclusion

The user authentication and authorization above is effectively handled by JWT. Caution has to be taken to prevent an unauthorized parties from accessing the resources in our application. Only authorized users (depending on their assigned roles) are allowed. Refresh token is used to issue new Access Token using a middleware because it is shortlived and has to be reissued after expiry. Every time the Access Token is issued, the expired Access token and Refresh Token have to be verified, if error occurs(in case its tampered with) the user is unauthorized. Refresh and Access token discussed above must be set correctly, in terms of expiry or on how they are allowed to issue resources access. 


<script async src="https://talk.hyvor.com/embed/embed.js" type="module"></script>
<hyvor-talk-comments website-id="9346" page-id=""></hyvor-talk-comments>