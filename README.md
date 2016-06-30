# SailsJs and Mysql example
Create CRUD with SailsJs and MySql.
## Installs
### Install Node js
Download Node.Js from this url [Node.js](https://nodejs.org/).

![Node](https://github.com/miguelcast/SailsJs-and-Mysql-example/blob/master/20160630-080945_capture.gif)

We check Node.Js, in the command-line tool:

```sh
$ npm -v
```

```sh
$ node -v
```

![Check](https://github.com/miguelcast/SailsJs-and-Mysql-example/blob/master/20160630-083341_capture.gif)

### Install SaislJs

We can see how install Saisl from this url [Saisl.js](http://sailsjs.org/get-started).

To install with the command-line tool:

```sh
$ npm -g install sails
```
Let's check if "Sails" was installed correctly:
```sh
$ sails -v
```
### Create a new Sails app

```sh
$ cd /you/path/project/
$ sails new crudUser
$ cd crudUser
```
Now lift the server and after you visit http://localhost:1337/:
```sh
$ sails lift
```
![serve](https://github.com/miguelcast/SailsJs-and-Mysql-example/blob/master/20160630-091611_capture.gif)

Let's to create model and controller User:
```sh
$ sails generate api user
```
This created two files, api/models/User.js(model) and api/controllers/UserController.js(controller).

### Install Mysql if you don't have installed before

Download Mysql from this url [MySql](http://dev.mysql.com/downloads/mysql/).

You can see the documentation for settings Mysql.


