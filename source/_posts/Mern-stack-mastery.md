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

To use express you need to install in NodeJS as a dependency using npm (Node Package Manager).

    $ npm install express

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

With its routing capabilities, express is commonly used to create ***RESTful APIs***. Express makes the process of defining routes that map into different CRUD operations ( Create, Read, Updata and DELETE ) on API endpoints easy.

Express.js provides a foundational block for building web applications ranging from simple static websites to complex RESTful APIs. It's flexibility and diverse use of middlewares and plugins contribute greatly to its popularity in the Node.js commmunity.

### ***React***

React, developed by Meta (formerly Facebook) is an open-source JavaSript library used for building reusable user interface components in web applications. The components use virtual DOM (lightweight copy of the actual DOM in memory), that automatically update when data changes improving perfomance. React uses a declarative syntax where developers describe the components and react handles updates promptly. Let's get you started.

    npx create-react-app myApp

React simplifies the process of building by use of ***declarative syntax*** to mean the developer describes the UI state and react handles how to update it. This is a move from the traditional way of manually updating the DOM thanks to react.

When the state of a component change, react re-renders that component and its children. This allows the component to have a local state where data can change in real time. This is ***state management*** and it's the core to creation of dynamic and interactive UI.

***Props*** are inputs that allow components to receive data fro their parent components. They are used to pass down the component hierarchy making the components reusable. In the code below, we pass down the user prop to EditUserForm component.

    import EditUserForm from "./EditUserForm"
    import { useGetUsersQuery } from "./usersApiSlice"
    import PulseLoader from "react-spinners/PulseLoader"

    const EditUser = () => {
        const { id } = useParams()
        const { user } = useGetUsersQuery("usersList", {
            selectFromResult: ({ data }) => ({
            user: data?.entities[id]
            }),
        })
        if (!user) return <PulseLoader color={"#FFF"} />
        const content = <EditUserForm user={user} />

        return content
    }

    export default EditUser

As from the above exerpt, the user data flows from the parent to the child component, what is referred to as ***unidirectional data flow***. This makes it easier to track changes and understand applications behaviour.

Introduced in react 16.8, ***hooks*** are functions that allow developers to use states in fuctional instead of class components. Hooks make it easier to manage states. Below is an example of a hook used to create title.

    import { useEffect } from "react"
    const useTitle = (title) => {
        useEffect(() => {
            const prevTitle = document.title
            document.title = title

            return () => document.title = prevTitle
        }, [title])
    }

    export default useTitle

There are cases where you do not want to pass down props or states along the component tree. ***Context API*** allows you to share these props and states without needing to drill them down the component tree. This is very useful in managing global states.

To improve performance and SEO, react uses ***Server Side Rendering (SSR)*** where where the initial rendering occurs on the server intead of the client side. In addition, react supports ***Static Site Generation (SSG)***, where web pages are rendered at build time.

Evidently, react provide ideal tools and features for building dynamic web applications ranging from Single Page Applications (SPAs) to Progressive Web Page Applications (PWAs). Apart from web, React Native is widely adopted to build mobile applications. On top, dynamic interactive dashboards built using react are foundational block for building e-commerce platforms.

### ***Node.js***

Node.js is an open-source cross-platform runtime evironment that is built on V8 Javascript engine. It allows execution of javaScript code on the server, outside of the web browser, making it possible to build diverse applications.

Node.js uses ***asynchronous non-blocking*** I/O model to mean it executes the operations concurrently without waiting for one task to complete before moving on to the next. This is principally crucial for applications that necessitate handling of many operations simultaneously.

    const User = require('../models/User')

    const getAllUsers = async (req, res) => {
        const users = await User.find().select('-password').lean()
        if (!users?.length) {
            return res.status(400).json({ message: 'No users found!'})
        }
        res.json(users)
    }

That brings us to the Node.js ***event driven architecture*** that is allows execution of certain functions when certain events occur. Example from the above code, if we receive users data, we can proceed and process them using another callback function.

`getAllUsers` function above is ***single-threaded*** but uses an underlying asynchronous thread pool to handle I/O operations, enabling concurrency.

Reusable components are organized into ***modules*** depending on their functionality. These files can be imported easily to other parts of the code thanks to modular system in Node.js.

***Node Package Manager (npm)*** provide a wide ecosystem of open-source libraries and modules that can be installed and integrated into Node.js making development of web applications faster and easier.

Node.js heavily emphasize on the use of common.js modules that allows developers to structure their code into separate files and efficiently manage the dependencies. The `require` function is used to import modules while `module.exports` used to export data from the module.

The non-blocking architecture in Node.js allows it to handle a large volume of concurrent operations. This makes Node.js highly ***scalable*** and ideal for building real time applications and services.

Node.js has a wide applications ranging from web servers, APIs, Microservices to building real-time applications.

In conlusion, the mern stack's popularity is a total contribution of all for technologies. Developers are able to create efficient and fast web applications on both the client-side and server-side all in JavaScript. The mern stack's popularity is a projection of the desirability of the stack in building web applications that respond to users needs, effortlessly, fast and in real time. Ranging from UI to API, the mern stack has made it significantly possible to create scalable web applications with diverse use ranging from e-commerce, microservices to command line tools. My hope is all the communities that support MongoDB, Express.js, React and Node.js will continue to grow in support of mern stack.


<script async src="https://talk.hyvor.com/embed/embed.js" type="module"></script>
<hyvor-talk-comments website-id="9406" page-id=""></hyvor-talk-comments>