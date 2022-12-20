<!-- .slide: data-background="#330000" -->
# json-server  <!-- .element: class="r-fit-text" -->


<!-- .slide: data-background="#330000" -->
## what is json-server

This is an backend API library which is really handy when we need some mocked data (like when db is not ready yet)


<!-- .slide: data-background="#330033" data-transition="fade-in fade-out" -->
![style](./assets/json-server-fe.webp)


<!-- .slide: data-background="#330000" -->
## installation

It can be installed in frontend project itself or standalone. For a presentation purposes we decided to install it as separate 'application' in a different folder

```bash
npm i json-server
```


<!-- .slide: data-background="#330000" -->
## start

To start json-server it is enough to create database file like _db.json_ with data as array with specific key. Here database has only one key from where we will get data

```json[1,10|2,9|3-8]
{
  "applications": [
    {
      "id": "generated_id",
      "name": "app name",
      "description": "app description",
      "active": false
    }
  ]
}
```


<!-- .slide: data-background="#330000" -->
Start server

```bash
$ json-server db.json
```

this will run by default on 

```bash
localhost:3000/
```


<!-- .slide: data-background="#330000" -->
## get data from api

Getting data from api is as easy as:

```bash[1|2]
GET /:key-what-you-wont-to-get
GET /applications
```

it will return an array of elements


<!-- .slide: data-background="#330000" -->
## get single element from api

```bash[1|2]
GET /:key-what-you-wont-to-get/:id
GET /applications/He110-W0r1D
```


<!-- .slide: data-background="#330000" -->
## pagination

```bash[1|2|4|5]
_limit=:value
_page=:value

GET /:key-what-you-wont-to-get?_limit_=:value&_page=:value
GET /applications?_limit_=3&_page=3
```


<!-- .slide: data-background="#330000" -->
## order

```bash[1|2|4|5]
_sort=:keyName
_order=:asc|desc

GET /:key-what-you-wont-to-get?_sort=:keyName&_order=asc|desc
GET /applications?_sort=name&_order=asc
```


<!-- .slide: data-background="#330000" -->
## Adding new element

```bash[1|2]
POST /:key-what-you-wont-to-post-data
POST /applications
```

JSON object:

```json[1,4|2|3]
{
  "id": "S0mE-Id", // optional
  "name": "new name"
}
```

Response from request will be a new element with "id". If "id" is not provided it will be automatically created by json-server


<!-- .slide: data-background="#330000" -->
## update one

```bash[1|2]
PUT /:key-what-you-wont-to-post-data/:id
PUT /applications/He110-W0r1D
```

and json data - only keys that are needed to be updated

```json[1,3|2]
{
  "name": "updated name"
}
```

updated element will be send as a response


<!-- .slide: data-background="#330000" -->
## delete one

```bash[1|2]
DELETE /:key-what-you-wont-to-post-data/:id
DELETE /applications/He110-W0r1D
```

Empty element will be send as a response


<!-- .slide: data-background="#330000" -->
## routes

To customize routes we need to create a _routes.json_ file
this one will create _/api_ prefix for all routes

```json[1,3|2]
{
  "/api/*": "/$1"
}
```

and add a parameter to starting script

```bash
--routes routes.json
```


<!-- .slide: data-background="#330000" -->
## more routes options

If there is a route for search like this: `/api/applications/search/:phrase`

it is enough just to use this piece of code:

```json[3]
{
  "/api/*": "/$1",
  "/applications/search/:name": "/applications?name_like=:name"
}
```

and we can use as many parameters as we need


<!-- .slide: data-background="#330000" -->
## middleware

Additional functions like setting delays, or checking if token exists - we can do it by creating some middleware methods. We just need to create a middleware file with method, like:

```js[1,5|2,4|3]
module.exports = (req, res, next) => {
  setTimeout(() => {
    next()
  }, 2000)
}
```

and apply it in a starting script

```bash
--middlewares ./middlewares/delay.js
```

we can use more middleware files


<!-- .slide: data-background="#330000" -->
## other params

In this project we are using also some additional parameters

```bash[1|2]
--watch
--port 3005
```

All possible options

```bash
json-serve --help
```


<!-- .slide: data-background="#330000" -->
## questions

?
