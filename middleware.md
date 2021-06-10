# middleware

-   middleware is just a function take in req, res, next and call next whenever it wants to move to the next form of the

```MIDDLEWARE
A function that is invoked by the Express routing layer before the final request handler, and thus sits in the middle between a raw request and the final intended route. A few fine points of terminology around middleware
    var foo = require('middleware') is called requiring or using a Node.js module. Then the statement var mw = foo() typically returns the middleware.
    app.use(mw) is called adding the middleware to the global processing stack.
    app.get('/foo', mw, function (req, res) { ... }) is called adding the middleware to the “GET /foo” processing stack.
```
