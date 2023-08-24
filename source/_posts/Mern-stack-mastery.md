---
title: Mern stack mastery
date: 2023-08-19 12:56:41
tags:
---

## Introduction

Mern is an acronym for a set of four popular technology stack used to build web applications, namely MongoDB, Express.js, React and Node.js. The stack is widely adopted to create efficient and high perfomance web applications in commercial enterprises both for small and large fortune 100 companies in the world. MongoDB is NoSQL database while React is a popular JavaScript library used in creating UI components. Node.JS is a server-side JavaScript that serves the backend code while Express.js is its framework. We will discuss these technologies in detail ranging from their actual use in building, integration, to their pros and cons. [Linked here](https://allan.onrender.com/) is the project we will use as an example with exerpts of code.

### ***MongoDB***
Unlike the common relational database, mongoDB uses document oriented database schema where data is stored in JSON like format known as BSON - Binary JavaScript Object Notation. Related documents are organized in collections and can have different structure and fields allowing you to store diverse data in a very dynamic and flexible ways. Below is an example of such a schema.

    const mongoose = require('mongoose')

    const userSchema = new mongoose.Schema({
        username: {
            type: String,
            required: true
        },
        password: {
            type: String,
            required: true
        },
        roles: {
            type: [String],
            default : ["Employee"]
        }
    })

    module.exports = mongoose.model('User', userSchema)

Apart from being an open-source, mongoDB's popularity is anchored partly on its ability to handle large volume of unstructured and semi-structured data and partly on its scalability and flexibility.

***Scalability*** in mongoDB refer to the ability to increase large volume of resources in a single server (vertical scalability) as well as the ability to distribute data across multiple servers(horizontal scalability) efficiently and fast.

![Simple mongoDB data structure](/img/mongoDB_user.jpg 'User data in mongoDM database from the above Schema')

Another feature that supports mongoDB's popularity is its ***powerful Query Language*** that supports queries like sorting and filtering. This is supported by the query language used by mongoDB that has JSON-like syntax.

Apart from the query language used, automatic ***indexing*** in mongoDB makes data retrieval fast and less painful. Each field stored has a unique **'_id'** and other fields can be removed or added as needed.

mongoDB also ensures availability through ***replication*** for example by supporting replica sets by automatic failover. The aggregation framework enables operations such as grouping, sorting or combining data.

One of the main use of mongoDB is content management. MongoDB can store diverse data types like videos, images and texts. Other uses include Internet of Things and building E-commerce. 

### ***Express.js***

Express is a popular node js framework for building server-side applications. It is widely used to provide broad features for building efficient and fast web and mobile applications. It is written in JavaScript. The framework provides a wide set of tools and utilities that simplify the process of creating web servers and handling HTTP requests and responses.

One of the common Express js features that contribute to its popularity is ***Routing***. Express makes it easy and to define routes for handling different HTTP methods that include GET, POST, PUT and DELETE in different URL patterns. The routes are defined using `app.get()`, `app.post()`, `app.patch()` etc in that similar pattern. These patterns are the key determinant to how the app responds to different requests. Below is an example of such routes with imported controller functions.

    const express = require('express')
    const app = express()
    const usersController = require('../controllers/usersController')

        app.get(usersController.getAllUsers)
        app.post(usersController.createNewUser)
        app.patch(usersController.updateUser)

    module.exports = app

***Middlewares*** are functions that are executed sequentially for each incoming request before the final route handler is called. They are core features in applications that require authentication. Middleware functios have access to request-response cycle and can terminate or modify them. 

Express.js can provide abstraction over the built-in Node.js ***request-response*** objects providing them with additional methods and properties to make them easier to work with HTTP requests and responses. Express.js also makes it easy to integrate with ***template*** and template engines like EJS and handlebars  making it possible to generate dynamic content on the server-side.

Express can ***serve static files*** like HTML, CSS, images etc using `express.static()` middleware which is particularly useful for applications that require client-side assets.

    const express = require('express')
    const app = express()
    const path = require('path')

    app.use('/', express.static(path.join(__dirname, 'public')))

Express js simplifies the process of ***error handling*** using middlewares that catch and process errors during the request and response cycle.

To organize your code into manageable units, express encourages the use of ***routing and controllers***. Routes can be modularized into different files in respect to their route handlers and logic.


### ***React***

### ***Node.js***