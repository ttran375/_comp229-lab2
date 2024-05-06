# Lab Session 2 Developing Node.js Web Application and Connect Module

This document provides the necessary instructions for completing the
Week 2 lab session exercises.

## Exercise 1: Develop Node.js Web Application

Open VS Code. Open a new folder (File/Open folder...). Name the folder
**lab-session-2**.

Open a new Terminal window (Terminal menu, select new).

To create the **package.json** file, type **npm init or yarn init** in
the terminal window and accept defaults as below:

``` sh
yarn init
```

In your working folder, create a file named **server.js** that contains
the following code snippet:

``` js
const http = require('http');
http.createServer((req, res) => {
   res.writeHead(200, {
   'Content-Type': 'text/plain'
   });
   res.end('Hello World');
}).listen(3000);
console.log('Server running at http://localhost:3000/');
```
run the server.js file as follows:

``` sh
node server
```

## Exercise 2: Connect Middleware

revise the previous example to include your first middleware. Change
your **server.js** file to look like the following code snippet:

``` js
const connect = require('connect');
const app = connect();
function helloWorld(req, res, next) {
   res.setHeader('Content-Type', 'text/plain');
   res.end('Hello World');
};
app.use(helloWorld);
app.listen(3000);
console.log('Server running at http://localhost:3000/');

```

run the server.js file as follows:

``` sh
node server
```

## Exercise 3: Mounting Connect Middleware

Modify your server.js file to look like the following code snippet:

``` js
const connect = require('connect');
const app = connect();

function logger(req, res, next) {
    console.log(req.method, req.url);
    next();
}

function helloWorld(req, res, next) {
    res.setHeader('Content-Type', 'text/plain');
    res.end('Hello World');
}

function goodbyeWorld(req, res, next) {
    res.setHeader('Content-Type', 'text/plain');
    res.end('Goodbye World');
}

app.use(logger);
app.use('/hello', helloWorld);
app.use('/goodbye', goodbyeWorld);

app.listen(3000);
console.log('Server running at http://localhost:3000/');

```

run the server.js file as follows:

``` sh
node server
```

Go to the browser and mount the path

Ask for assistance if you encounter any issues during the lab session.

Happy coding!

**References**

Week1 slides

<https://nodejs.org/en/>

<https://code.visualstudio.com/>
