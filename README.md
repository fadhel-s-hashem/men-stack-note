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

## Rendring ejs

- install ejs wit `npm i ejs`
- creat a `views` directory (folder)
- creat an `.ejs` file like title `home.ejs`
- add html boilerplate with `i + tab`

 home.ejs example
````html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Home</title>
</head>
<body>
    <h1> this is ejs page! 👾</h1>

</body>
</html>
 ````
-render `.ejs` page using a controller like this one:
````js
app.get('/', function(req,res){
    res.render('home.ejs')
})
````
<img width="425" height="202" alt="image" src="https://github.com/user-attachments/assets/c9f3104c-e6df-46e3-be40-e831e244d947" />

### ejs syntax

To use javascript and ejs filre, need a script tag
````ejs
<% let user ='fadhel' %>
````
To display javascript ehs file < tou need an outpot tag :
````ejs
<% let user ='fadhel' %>
<%= user %>
````

### pass data from controller

Use the locals object inside the render method:
````js
res.render('home.ejs', {
        title: 'Home page',
        })
````
now I can us the `title` varible in my `home.ejs` file.
````
<h1> <%= title %> this is ejs page! 👾</h1>
````
<img width="597" height="102" alt="image" src="https://github.com/user-attachments/assets/d079aab5-dbda-49af-bfde-f420242a9768" />


### using foeEach for an arrey in ejs

````ejs
ul>
<% inventory.forEach(function(item){ %>
   <li> <%= item.name%> </li>
<%})%>
</ul>   
````

### creating dynamic links to a `show` page
`item.name` is dynamic showing up. The Link is also dynamic changing with the item (see `forEach` above)

````ejs
<a href="/ <%= item.id %>"><&= item.name %></a>
````
we should see the URL changes

### Reusable nav bar with partials
-creat a folder called `partials` inside of `views`
-creat a file `nav.ejs` inside `partials`
````nav.ejs
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inventory app</title>
    <link rel="stylesheet" href="/stylesheets/style.css">
</head>
<body>
    <nav>
        <a href="/">Home</a>
    </nav>
````
Include `nav` in other files with this statment
````
<%- include('./partials/nav') %>
````

### add CSS image with `public`

###CSS
- creat `public` folder outside 
- in side `public` make `stylesheets` folder  with `style.CSS` inside
- After that add `<link rel="stylesheet" href="/stylesheets/style.css">` in `nav.ejs` file

config our server to look inside of the `public ` folder for static file:
````sever.js
// requre a path from nide at the top
const path = require('path')

// and this before the morgan
app.use(express.static(path.join(__dirname, "public")))
````

- Link the stylesheet in the head of our `html` files (inside `nav` if we using `partiels` )
  ````nav.ejs
  <link rel="stylesheet" href="/stylesheets/style.css">
  ````

### image
- creat `images` folder inside of the `public` folder
- Link to images like normal : `<img src="/images/family.jpg" alt="A happy family">`



