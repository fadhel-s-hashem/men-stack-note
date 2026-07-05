# men stack node

| CRUD Action | RESTful Action | HTTP Method | Definition |
| ----------- | -------------- | ----------- | ------------------------ |
|  | `new` | `GET` | Show a form to create a new item |
| Create | `create` | `POST` | Add a new item to the database |
| Read | `index` | `GET` | Show all items |
| Read | `show` | `GET` | Show one specific item |
| | `edit` | `GET` | Show a form to edit an existing item |
| Update | `update` | `PUT` | Save changes to an existing item |
| Delete | `delete` | `DELETE` | Remove an item from the database |

## setup

- creat a directory
- creat server file `touch server.js`
- creat `.gitignore` file
- intilaize a node project `npm init -y`
- install express and morgan `npm i express morgan`

 ### Add (node_modules) to (gitignore)

.gitignore
````bash
node_modules
````

### write server Biolerplate

server.js
````js
//bring express into our server
const express = require('express')
const morgan = require('morgan')

// actuall use express
const app = express ()

app.use(morgan('dev'))

app.listen(3000, function(){
    console.log('listening to port 3000')
})
````

run server with nodemon `nodemon server.js`
<img width="1117" height="1020" alt="image" src="https://github.com/user-attachments/assets/a405a4e3-1f3f-4843-86f1-3567db19fa17" />

navigate to `http://localhost:3000` to view our server

use `Ctrl + C` tp stop sever in the terminal when needed

### Creating a test route
````js
app.get('/test', function(req,res){
    res.send('<h1>TEST HERE</h1>')
})
````
<img width="826" height="627" alt="image" src="https://github.com/user-attachments/assets/0828b248-1a47-4e2c-b45f-7908934e5d59" />

navigate to `http://localhost:3000/test`

### usuing request parameters (params)

````js
app.get('/greet/:name', function(req,res){
    res.send(`<h1>Hello:${req.params.name} </h1>`)
    console.log(req.params.name)
})
````
navigate to `http://localhost:3000/greet/fadhel`
<img width="365" height="167" alt="image" src="https://github.com/user-attachments/assets/4d83a9fe-924b-4c47-94a5-d76477be261d" />




