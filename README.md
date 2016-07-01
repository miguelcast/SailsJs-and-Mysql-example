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

```sql
CREATE DATABASE test;
```
Create table of users:
```sql
CREATE TABLE `test`.`users` (
  `id` INTEGER UNSIGNED NOT NULL AUTO_INCREMENT,
  `firstName` VARCHAR(45) NOT NULL DEFAULT '',
  `lastName` VARCHAR(45) NOT NULL DEFAULT '',
  `email` VARCHAR(100) NOT NULL DEFAULT '',
  `phone` VARCHAR(30) NOT NULL DEFAULT '',
  `address` VARCHAR(80) NOT NULL DEFAULT '',
  `createdData` DATETIME NOT NULL DEFAULT 0,
  `updateDate` TIMESTAMP NOT NULL DEFAULT 0,
  PRIMARY KEY(`id`)
)
ENGINE = InnoDB
CHARACTER SET utf8;
```
### Let's Integrate Sails and Mysql

MySQL adapter for the Sails framework and Waterline ORM. Install from npm sails-mysql:
```sh
$ npm install --save sails-mysql
```
setting MySql on SailsJs, add the next code into config/connections.js:
```js
  mysqlTest: {
    adapter: 'sails-mysql',
    host: 'localhost',
    user: 'root', //optional
    password: 'root', //optional
    database: 'test' //optional
  }
```
and change settings on config/models.js:
```js
  connection: 'mysqlTest',
  migrate: 'safe',
  schema: true
```
Now, modify api/models/User.js:
```js
module.exports = {
  // Name table in database
  tableName: 'users',

  // attributes: types, validations ans defaults values
  attributes: {
    id: {
      type: 'integer',
      autoIncrement: true,
      primaryKey: true
    },
    firstName: {
      type: 'string',
      required: true,
      size: 45
    },
    lastName: {
      type: 'string',
      required: true,
      size: 45
    },
    email: {
      type: 'email',
      unique: true,
      required: true,
      size: 100
    },
    phone: {
      type: 'string',
      required: true
    },
    address: {
      type: 'string',
      required: true,
      size: 30
    },
    createdData: {
      type: 'datetime'
    },
    updateDate: {
      type: 'datetime',
      defaultsTo: function () {
        return new Date();
      }
    }
  },
  // before execute function createsss
  beforeCreate: function (values, cb) {
    values.createdData = new Date();
    cb();
  }
};
```
