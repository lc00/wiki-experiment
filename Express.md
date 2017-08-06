## Express

### Middleware

* A function that has a `(request, response, next)` signature
* No return value, just calls `next()`
* Can make an anonymous function as middleware
* Middleware is executed in order
* Middleware processes until `next()` isn’t called, or an error is generated
* If you call `next(error)` with an argument, it will look for error handling middleware
* Error handling middleware has 4 arguments `(error, request, response, next)`
* If you need to pass values in, your middleware will be a factory that returns a function with the middleware signature

### Express Middleware

* Used with `app.use();`
* `app.use()` will match all methods for all routes.
* Express methods are all chainable.

### Useful Express middleware

* `body-parser`
* `serve-static`
* `compression`
* `cookie-parser`
* `cookie-session`
* `express-session`
* `errorhandler`
* `passport`
* `morgan`
* `winston`
* `csurf`
* `serve-favicon`
* `method-override`
* `vhost`

### Using a templating engine

```js
app.set(“views”, “templates”) // Template Folder
app.set(“view engine”, “jade”) // Engine you want to use

response.render(“template-name”, dataObject);
```

