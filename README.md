# MERN_Web_Stack

The MERN web stack is a popular set of technologies used for building modern web applications. MERN stands for MongoDB, Express.js, React.js, and Node.js. Each component of the stack plays a crucial role in the development process:

#### MongoDB:
Type: NoSQL database

Role: Stores data in a flexible, JSON-like format (BSON), making it easy to pass data between client and server.

Benefits: Scalability, flexibility, and ease of use with JavaScript.



#### Express.js:

Type: Web application framework for Node.js

Role: Simplifies the process of building robust APIs and handling HTTP requests.

Benefits: Minimalist, unopinionated framework, offering powerful features through middleware.

#### React.js:


Type: Front-end JavaScript library

Role: Builds dynamic user interfaces using a component-based architecture.

Benefits: Efficient rendering with a virtual DOM, reusable components, and a strong ecosystem.


#### Node.js:

Type: JavaScript runtime environment

Role: Executes JavaScript code on the server side, enabling full-stack JavaScript development.

Benefits: Non-blocking, event-driven architecture, which is ideal for I/O-heavy applications.


## How the MERN Stack Works Together

#### Front-End (React.js):
The user interacts with the web application through a React.js-based front end. React components manage the UI and handle user inputs.

#### Back-End (Express.js and Node.js):
React components make API requests to the Express.js server, which runs on Node.js. The server handles the business logic and routes requests appropriately.

#### Database (MongoDB):
The Express.js server interacts with MongoDB to store, retrieve, and manage data. MongoDB's schema-less design allows for quick iteration and flexibility in data modeling.

#### Example Workflow
A user interacts with the React front end, perhaps submitting a form.
React sends an HTTP request to an Express.js API endpoint.
Express.js processes the request, performs any necessary logic, and interacts with the MongoDB database.
MongoDB returns the required data, which Express.js sends back to the React front end.
React updates the UI based on the response from the server.

## Advantages of Using the MERN Stack

Single Language: Full-stack development using JavaScript on both the client and server sides.

Community and Ecosystem: Strong community support and a rich ecosystem of libraries and tools.

Scalability: Each component of the stack can be scaled independently, providing flexibility in handling large-scale applications.

Performance: Non-blocking architecture of Node.js, efficient front-end updates with React's virtual DOM, and the powerful, flexible data management capabilities of MongoDB.

## Getting Started

## Step1- Backend Configuration:
### Update and upgrade Ubuntu
```
sudo apt update
sudo apt upgarde
```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/955aeb23-fb19-4e8f-973f-c34a50d2d02e)

Get the location of Node.js software from Ubuntu repositories:
```
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/564e2e1f-d8a5-4e80-8e4c-7a461e0b3f2e)

### Install Node.js 
```
sudo apt-get install -y node.js
```
The command above installs both node.js and npm. NPM is a package manager for Node.
Verify the installation with the command below:
```
node -v
```
OR
```
npm -v
```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/214d17fe-21b5-47ee-a792-4e2c515198d9)

### Application Code Setup
Created a new directory for my TO-DO app:
```
mkdir Todo
```
verify with:
```
ls
```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/0ea3aeff-39c8-439a-9b43-0e344a3e9108)

Change directory into the new directory and use `npm init` to initialise your project so that a new file named package.json will be created:  
```
cd Todo
```
then
```
npm init
```
verify the the package.json file was created.
```
ls
```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/bf2ef105-250a-4941-92a9-f6e36ab2f9d6)

## Step2- Install ExpressJS
ExpressJS is a framework for nodeJS. Therefore it simplifies developemt and abstracts a lot of low level details.

### install using npm:
```
npm install express
```
then create a file "index.js" use `ls` to verify:
```
touch index.js
ls
```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/845cebfa-7702-46e3-87fe-7e0b5f0fa9c3)

### Install dotenv module
```
npm install dotenv
```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/e201a3fe-552e-4087-95f4-33939b879cc7)

### Type the following code into the index.js 
```
vim index.js
```
type
```
const express = require('express');
require('dotenv').config();

const app = express();

const port = process.env.PORT || 5000;

app.use((req, res, next) => {
  res.header("Access-Control-Allow-Origin", "*");
  res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
  next();
});

app.use((req, res, next) => {
  res.send('Welcome to Express');
});

app.listen(port, () => {
  console.log(`Server running on port ${port}`);
});


```
you can use cat to check inside a file without opening it:
```
cat index.js
```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/5cf45f64-31ae-486e-bfa2-5f84c9f262ef)

### Start the server
```
node index.js
```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/c75f3502-81a8-4412-8867-5130222a17e3)

### Configure your ec2 instance to accept traffic over port 5000;
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/7a199b9a-4b0d-4bff-be6b-f52a8c53980a)

Then open your brower and try http://18.234.210.235:5000
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/1a05619a-da7b-4606-8252-e57fe80f0f5a)

## Routes
The To-Do app should be able to 
1. Create a new task
2. Display list of all tasks
3. Delete a completed task
For each task we need to create a route that will define various endpoints that the To-Do app will depend on.

### create a folder "routes":
```
mkdir routes
```
change directory to routes folder
```
cd routes
```
Create a file api.js
```
touch api.js
```
open the file:
```
vim api.js
```
copy and paste:
```
const express = require('express');
const router = express.Router();

router.get('/todos', (req, res, next) => {
  // Add your GET /todos logic here
  res.send('GET todos');
});

router.post('/todos', (req, res, next) => {
  // Add your POST /todos logic here
  res.send('POST todos');
});

router.delete('/todos/:id', (req, res, next) => {
  // Add your DELETE /todos/:id logic here
  res.send(`DELETE todo with id ${req.params.id}`);
});

module.exports = router;

```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/e17f29c6-639a-4642-af70-cf86e6f7cdcd)

## Models
A model is at the heart of javascript based applications and it is what makes it interactive.
The model is also used to define the database schema(blueprint)
To install a schema and a model `mongoose` is to be installed first, which is a Node.js package that makes working with mongodb easier.

change dir back to Todo folder and install Mongoose
```
cd ..
``
```
```
npm install mongoose
```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/a5b1c625-543c-417e-b237-69aed2650e13)

create a new folder `mkdir models`
change directory into the new folder `cd models`
Create a new file ` touch todo.js`
open the todo.js file and paste this:
```
const mongoose = require('mongoose');
const Schema = mongoose.Schema;

// Create schema for todo
const TodoSchema = new Schema({
  action: {
    type: String,
    required: [true, 'The todo text field is required']
  }
});

// Create model for todo
const Todo = mongoose.model('Todo', TodoSchema);

module.exports = Todo;


```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/4a2dea94-fde9-4483-abd5-0f9baf54c601)

Then we need to update our routes from the `api.js` file in the routes directory

open the file `api.js` and edit to this:
```
const express = require('express');
const router = express.Router();
const Todo = require('../models/todo');

// Middleware to parse JSON request body
router.use(express.json());

router.get('/todos', (req, res, next) => {
  // This will return all the data, exposing only the id and action field to the client
  Todo.find({}, 'action')
    .then(data => res.json(data))
    .catch(next);
});

router.post('/todos', (req, res, next) => {
  if (req.body.action) {
    Todo.create(req.body)
      .then(data => res.json(data))
      .catch(next);
  } else {
    res.status(400).json({
      error: "The input field is empty"
    });
  }
});

router.delete('/todos/:id', (req, res, next) => {
  Todo.findOneAndDelete({ "_id": req.params.id })
    .then(data => res.json(data))
    .catch(next);
});

module.exports = router;

```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/3ca8b230-f23e-42ec-90e3-e72b0aa7ef09)


## MongoDB 

MongoDB is a leading NoSQL database known for its flexibility, scalability, and high performance. Unlike traditional relational databases that use tables and rows, MongoDB stores data in JSON-like documents, which allows for a more flexible and dynamic data model. This schema-less design enables the storage of different types of data structures within the same collection.

Key features of MongoDB include its ability to handle large volumes of data, support for horizontal scaling through sharding, and built-in replication for high availability. It also offers a rich query language, making it easier to perform complex data retrieval and manipulation operations.

mLab is a popular cloud database service that provided managed MongoDB hosting. It is known for its ease of use, robust features, and support for developers looking to deploy and manage MongoDB databases without worrying about the underlying infrastructure. However, mLab was acquired by MongoDB Inc., and its services were integrated into MongoDB Atlas. we will sign up an account.

![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/8a823db1-83e2-4e3d-b33a-82b5aff76ea7)

### Create a cluster
### allow access to the MongoDB from anywhere
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/15cce2e7-9fb0-487d-a0f8-009286be882a)

Create a MonGo database and collection inside mLab:
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/d442f104-331c-4096-a624-f1b461f42b24)

### Create a file in your todo dir .env and open it :
```
touch .env
vim .env
```
### Add connection string to connect to MongoDB database
```
DB = ‘mongodb+srv://<username>:<password>@<network-address>/<dbname>?retryWrites=true&w=majority’
```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/79ae51ba-ec3b-4244-85f7-3c81d631f789)

### Update the index.js to reflect the use of .env so that Node.js can connect to the database.
edit to this instead
```
const express = require('express');
const bodyParser = require('body-parser');
const mongoose = require('mongoose');
const routes = require('./routes/api');
const path = require('path');
require('dotenv').config();

const app = express();

const port = process.env.PORT || 5000;

// Connect to the database
mongoose.connect(process.env.DB, { useNewUrlParser: true, useUnifiedTopology: true })
  .then(() => console.log(`Database connected successfully`))
  .catch(err => console.log(err));

// Since mongoose promise is deprecated, we override it with Node's promise
mongoose.Promise = global.Promise;

app.use((req, res, next) => {
  res.header("Access-Control-Allow-Origin", "*");
  res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
  next();
});

app.use(bodyParser.json());

app.use('/api', routes);

app.use((err, req, res, next) => {
  console.log(err);
  next();
});

app.listen(port, () => {
  console.log(`Server running on port ${port}`);
});

```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/d8d53928-2c5a-4f14-acf9-8819ea951cc3)

### start your sever 
```
node index.js
```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/61cfa2da-353e-4d60-9531-b4b2081261b5)


## Testing Backend Code without Frontent using RESTful API
In this project will would use POSTMAN to test our API,
### Create a Postman account 
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/0b86f4ec-3f15-438f-bd5e-9fd703076f05)

### Create a POST request
with hhtp://<publicIP>:5000/api/Todos
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/780de840-60d2-4046-b7e3-0af09d203c45)


and a GET request
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/99ac6803-ddad-4eb0-85f3-42405d8c67c3)


## Frontend creation:
in the same root directory as your backend code, which is the Todo directory run:
```
npx create-react-app client
```
This will creat a new folder in `Todo` directory
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/fc0e91b3-ff27-4c88-8cac-b0e6c3467a08)


### Runing a React app 
Before testing the some dependencies are needed 
concurrentlty
```
npm install concurrently --save-dev
```
nodemon:
```
npm install nodemon --save-dev
```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/7de49893-5240-460e-8598-6e24dc3e774c)

in `Todo` folder open `package.json` file and modify it replacing the `scripts part with:
```
 "scripts": {
    "start": "node index.js",
    "start-watch": "nodemon.js",
    "dev": "concurrently \"npm run start_watch\" \"cd client && npm start\""
  },
```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/fd5375ef-81b6-4f38-8ec6-c0a2c3c0bb8f)

### confingure Proxy in `package.json` 
change dir to client:
```
cd client
```
open `packeage file`
```
vim package.json
```
Add the key value pair in the package.json 
```
"proxy": "http://localhost:5000".
```
change directory back to the root directory and run 
```
npm run dev
```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/029b2cc0-1020-4e12-b324-1f57596e5a9f)


## Creating React components
for this todo app, there would be two stateful components and one stateless component.
from Todo dir go to client dir 
move to `src` 
```
cd src
```
inside your `src` dir create another dir called `components` and  move into it 
```
mkdir components
cd components
```
inside `components` dir create 3 files 
```
touch Input.js ListTodo.js Todo.js
```

Open `Input.js` file:
```
vim Input.js
```
write in the following 
```
import React, { Component } from 'react';
import axios from 'axios';

class Input extends Component {
  state = {
    action: ""
  }

  handleChange = (event) => {
    this.setState({ action: event.target.value });
  }

  addTodo = () => {
    const task = { action: this.state.action };

    if (task.action && task.action.length > 0) {
      axios.post('/api/todos', task)
        .then(res => {
          if (res.data) {
            this.props.getTodos();
            this.setState({ action: "" });
          }
        })
        .catch(err => console.log(err));
    } else {
      console.log('Input field required');
    }
  }

  render() {
    let { action } = this.state;
    return (
      <div>
        <input type="text" onChange={this.handleChange} value={action} />
        <button onClick={this.addTodo}>add todo</button>
      </div>
    );
  }
}

export default Input;
```
To use `Axios` you need to cd into your client from your terminal and run `yarn add axios` or `npm install axios`

in the client dir run:
```
npm install axios
```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/69799dc2-eaca-4641-863f-18a767742865)

Go to components dir
```
cd src/components
```
Open your ListTodo and copy and paste this 
```
import React from 'react';

const ListTodo = ({ todos, deleteTodo }) => {
  return (
    <ul>
      {
        todos && todos.length > 0 ? (
          todos.map(todo => {
            return (
              <li key={todo._id} onClick={() => deleteTodo(todo._id)}>
                {todo.action}
              </li>
            );
          })
        ) : (
          <li>No todo(s) left</li>
        )
      }
    </ul>
  );
}

export default ListTodo;
```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/e0c42f95-6a75-4261-bd2d-01c5b01782f7)

Then open Todo.js and cpoy and paste this:
```


import React, { Component } from 'react';
import axios from 'axios';

import Input from './Input';
import ListTodo from './ListTodo';

class Todo extends Component {
  state = {
    todos: []
  }

  componentDidMount() {
    this.getTodos();
  }

  getTodos = () => {
    axios.get('/api/todos')
      .then(res => {
        if (res.data) {
          this.setState({
            todos: res.data
          });
        }
      })
      .catch(err => console.log(err));
  }

  deleteTodo = (id) => {
    axios.delete(`/api/todos/${id}`)
      .then(res => {
        if (res.data) {
          this.getTodos();
        }
      })
      .catch(err => console.log(err));
  }

  render() {
    let { todos } = this.state;
    return (
      <div>
        <h1>My Todo(s)</h1>
        <Input getTodos={this.getTodos} />
        <ListTodo todos={todos} deleteTodo={this.deleteTodo} />
      </div>
    );
  }
}

export default Todo;

```
we need to make adjust ment to our react code Delete logo and adjust App.js 
```
cd ..
```
```
vim App.js
```
Copy and paste 
```
import React from 'react';
import Todo from './components/Todo';
import './App.css';

const App = () => {
  return (
    <div className="App">
      <Todo />
    </div>
  );
}

export default App;

```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/44111958-4519-418c-8123-c7705504fca9)

Then Open the App.css and paste this 

```
vim App.css
```
```
.App {
  text-align: center;
  font-size: calc(10px + 2vmin);
  width: 60%;
  margin-left: auto;
  margin-right: auto;
}

input {
  height: 40px;
  width: 50%;
  border: none;
  border-bottom: 2px #101113 solid;
  background: none;
  font-size: 1.5rem;
  color: #787a80;
}

input:focus {
  outline: none;
}

button {
  width: 25%;
  height: 45px;
  border: none;
  margin-left: 10px;
  font-size: 25px;
  background: #101113;
  border-radius: 5px;
  color: #787a80;
  cursor: pointer;
}

button:focus {
  outline: none;
}

ul {
  list-style: none;
  text-align: left;
  padding: 15px;
  background: #171a1f;
  border-radius: 5px;
}

li {
  padding: 15px;
  font-size: 1.5rem;
  margin-bottom: 15px;
  background: #282c34;
  border-radius: 5px;
  overflow-wrap: break-word;
  cursor: pointer;
}

@media only screen and (min-width: 300px) {
  .App {
    width: 80%;
  }

  input {
    width: 100%;
  }

  button {
    width: 100%;
    margin-top: 15px;
    margin-left: 0;
  }
}

@media only screen and (min-width: 640px) {
  .App {
    width: 60%;
  }

  input {
    width: 50%;
  }

  button {
    width: 30%;
    margin-left: 10px;
    margin-top: 0;
  }
}
```
![image](https://github.com/OlavicDev/MERN_Web_Stack/assets/124717753/e4f689d6-f711-44d4-8dbf-a92fafd261eb)

Exit 
In the same `src` dir
```
vim index.css
```
paste 
```
body {
  margin: 0;
  padding: 0;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto", "Oxygen", "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  box-sizing: border-box;
  background-color: #282c34;
  color: #787a80;
}

code {
  font-family: source-code-pro, Menlo, Monaco, Consolas, "Courier New", monospace;
}
```
Goto the Todo dir 
then run
```
npm run dev
```



