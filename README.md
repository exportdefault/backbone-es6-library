# backbone-es6-library

A small demo project that shows how to use webpack + backbone for client-side development in ES6 and sync data with server (nodejs + mongodb). This project is written in ES6-code with the using backbone.

## Installation

* Install [nodejs](https://nodejs.org)
* Install [mongodb](https://www.mongodb.com/) ([for ubuntu 14.04](https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-ubuntu-14-04))
* Run follow code in terminal:

```
cd backbone-es6-library
npm install
npm install -g webpack
cd public && bower install
```

## Usage

Before start, you have to check MongoDB. You can check this by running the following command. If MongoDB is running, you'll see an output like this (with a different process ID).
```
service mongod status
mongod start/running, process 1058
```

* Build once scss and js(es6) files you can use: `npm run build`.
* If you want that *watch files* continuously, rebuild incrementally whenever one of them changes, you can use: `npm run watch`.

**For start server use: `node server.js`.**

### Some $.ajax example for check mondodb from browser's devtool:


* Get all books `GET api/books/`.
```
$.get('/api/books/', function(data, textStatus, jqXHR) {
 console.log(JSON.stringify(data));
});
```
* Get book by id `GET api/books/:id`.
```
$.get('/api/books/57a1ed1ffc2063d02b0c7e2c', function(data, textStatus, jqXHR) {
 console.log(JSON.stringify(data));
});
```
* Add new book `POST api/books/`.
```
$.post('/api/books', {
 'title': 'Secrets of the JavaScript Ninja',
 'author': 'John Resig',
 'releaseDate': new Date( 2008, 3, 12 ).getTime(),
 'keywords':[
   { 'keyword': 'JavaScript' },
   { 'keyword': 'Reference' }
 ]
}, function(data, textStatus, jqXHR) {
 console.log(JSON.stringify(data));
});
```
* Update the book `PUT api/books/:id`.
```
$.ajax({
 url: '/api/books/57a1ec64f64b5f082b464aa9',
 type: 'PUT',
 data: {
 'title': 'JavaScript The good parts',
 'author': 'The Legendary Douglas Crockford',
 'releaseDate': new Date( 2008, 4, 1 ).getTime()
 },
 success: function( data, textStatus, jqXHR ) {
   console.log(JSON.stringify(data));
 }
});
```
* Delete the book `DELETE api/books/:id`.
```
$.ajax({
 url: '/api/books/57a1ec64f64b5f082b464aa9',
 type: 'DELETE',
 success: function(data, textStatus, jqXHR) {
   console.log(JSON.stringify(data));
 }
});
```
