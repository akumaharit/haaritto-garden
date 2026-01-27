---
{"dg-publish":true,"permalink":"/2-areas/programming/web/node-js-and-express-basics/","tags":["nodejs","express"],"created":"2025-12-14T11:43:06.648+07:00","updated":"2026-01-18T17:29:23.200+07:00"}
---

Server is used for **listening incoming request** and response back on what it should be
It is used for communication (let users access our app) and it is a trusted environment for our code.
(because something cannot be trusted on client-side)

Node.js is a popular JavaScript environment. It is not just creating server.
It can be used to do **computer'ish** things which is differ from the Web Browser which only do web browser'ish things


`node -v`
use `ctrl+c` to exit or type `.exit` to exit 
in vs code use `ctrl + ~` to open terminal in vscode
`node test.js` to run javascript via node

To create default `package.json` use `npm init -y`

### Creating Server
```js
let http = require("http");
//http functionaility will be imported into http
//http is part of the node, but we need to import it to use it.
let ourApp = http.createServer(function(req, res){
    console.log(req.url) //this will get the url of the req

    if (req.url == "/"){
        res.end("Hello, and welcome to our website.") //end the response by returning ___
    }

    else if (req.url == "/about"){ //end this response if /about was visited.
        res.end("Thank you for the interest in our company") 
    }
    else{
        res.end("We cannot find the page you are looking for.")
    }


});
//we have to pass the port to listen to
ourApp.listen(3000);
```

### Installing Express
`npm install express`
Running the command, the system will check in that directory it is running first, if the executable does not exist, it will then check the system PATH
If successfully, NPM will create the file, the folder and the package will be downloaded in the directory it is running the command.
GET request, is a standard type of `request`
POST request, is to send a request

```js
let express = require("express") //require will look for node_modules folder for the package.
let ourApp = express() //this will create an express application

// This allow the user's input to be accesssible (in the line 20)
ourApp.use(express.urlencoded({extended: false})) 


ourApp.get('/', function(req, res){ //use backtick to break to multiple line
    res.send(` 
        <form action = "/answer" method="POST">
            <p>What color is the sky on a clear and sunny day?</p>
            <input name = "skyColor" autocomplete="off">
            <button>Submit Action</button>
        </form>
        `) //the res.send is the method of express not the HTTP module (the default one)
}) //the url to lookout for, the function to run

//to tell what to do if it receive a post request.
ourApp.post('/answer', function(req, res){
    if (req.body.skyColor.toUpperCase() == "BLUE") { //Looking for a skyColor property in body object. However, for this to work, you have to configurate the express. //Add toUpperCase to make it NOT case sensitive!
        res.send(`
            <p>Congrats, that is the correct answers!</p>
            <a href ="/"> Back to the homepage </a>
            `)
    } else {
        res.send(`
            <p>Sorry, that is incorrect answer</p>
            <a href ="/"> Back to the homepage </a>
            `)
    }
}) 

//if you explictly access /answer, it will show this one, because it is a GET request.
ourApp.get('/answer', function(req, res){
    res.send("Are you lost? There is nothing to see here.")
}) 
ourApp.listen(3000) //will listen for the request in the port 3000
```

Port 3000 is commonly used for local/dev
These port is the port of [[2 Areas/Programming/Web/Internet#^0733a9\|Transport Layer]] which is where the TCP header are being stripped and checked if the port matched.
If it match, it will then hand the payload to the application / server.


### Automatically restart node.js when the app is updated.
`npm install nodemon`
In the `package.json` Add `"watch": "nodemon server",` in `watch` section 
(Use `npm init -y` to generate the `package.json` file)
Then launch the app with `npm run watch` it will then run the "watch" script as we defined in the `package.json`

If you install globally, you can just `nodemon server.js` however, installing globally sometimes cause problem.

### Connecting node.js to [[2 Areas/Programming/Web/MongoDB\|MongoDB]]
Install package `npm install mongodb`

Importing the package
`let mongodb = require('mongodb').MongoClient` (If you do this, you will only have access to the `MongoClient` Class)
`let {MongoClient, a, b ..... } = require('mongodb')` (Most people use **destructuring assignment** to import multiple class from the module.)
You can give a customized variable name with `let {MongoClient: Client} = require('mongodb')`

```js
async function go(){
	let clinet = new MongoClient('COPY THIS FROM MONGODB')
	await client.connect() //we need to wait this one to finish first
	db = client.db()
	app.listen(3000)
}

go()
```

use `await` keyboard inside a function that is asynchronous (start with `async`.
another line will not run, until the line with `await` finished running.
```js
app.post('/create-item', async function(req,res){
    await db.collection('items').insertOne({text: req.body.item})
    res.send("Thank you for submitting the form.")
})
```

On the MongoDB side, whitelist connection ip with `0.0.0.0/0` to allow connection from any ip address

### Example of the Project: [[2 Areas/Programming/Web/Project - Building Todo Application\|Project - Building Todo Application]]

### Reading Data from MongoDB, Assembling HTML before sending a GET response
```js
app.get('/', async function(req,res){
  const items = await db.collection("items").find().toArray()
    res.send(`
        <!DOCTYPE html>
		<html>
		<head>
		  <meta charset="UTF-8">
		  <meta name="viewport" content="width=device-width, initial-scale=1.0">
		  <title>Simple To-Do App</title>
		  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.2.1/css/bootstrap.min.css" integrity="sha384-GJzZqFGwb1QTTN6wy59ffF1BuGJpLSa9DkKMp0DgiMDm4iYMj70gZWKYbI706tWS" crossorigin="anonymous">
		</head>
		<body>
		  <div class="container">
		    <h1 class="display-4 text-center py-1">To-Do App</h1>
		    
		    <div class="jumbotron p-3 shadow-sm">
		      <form action = "/create-item" method="POST">
		        <div class="d-flex align-items-center">
		          <input name = "item" autofocus autocomplete="off" class="form-control mr-3" type="text" style="flex: 1;">
		          <button class="btn btn-primary">Add New Item</button>
		        </div>
		      </form>
		    </div>
		    
		    <ul class="list-group pb-5">
		      ${items.map(function(item){
		        return `<li class="list-group-item list-group-item-action d-flex align-items-center justify-content-between">
		        <span class="item-text">${item.text}</span>
		        <div>
		          <button class="edit-me btn btn-secondary btn-sm mr-1">Edit</button>
		          <button class="delete-me btn btn-danger btn-sm">Delete</button>
		        </div>
		      </li>`}).join('')}
		    </ul>
		    
		  </div>
		  
		</body>
		</html>
        `)
})
```