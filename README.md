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
- intilaize a node project `npm init -y`
- install express `npm i express`

### write server Biolerplate

server.js
````js
//bring express into our server
const express = require('express')
// actuall use express
const app = express ()



app.listen(3000, function(){
    console.log('listening to port 3000')
})

````

run server with nodemon `nodemon server.js`
<img width="1117" height="1020" alt="image" src="https://github.com/user-attachments/assets/a405a4e3-1f3f-4843-86f1-3567db19fa17" />
