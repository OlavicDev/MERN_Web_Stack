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

