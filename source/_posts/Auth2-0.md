---
title: Auth2.0
date: 2023-08-14 04:40:24
tags:
---

## Introduction

Auth is the first line of security to all protected routes of a website. The protcted routes have resources that only authorized users are allowed to access. Auth uses two main security features to authenticate and authorize users namely, refresh and access token. Users are welcome in the website's public page. The credentials users provided as username and password are used to authenticate, or make and identification of who they are. In this article we will explore the process user auth using the above named security fetures.


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

