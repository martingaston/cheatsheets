# Express Cheatsheet

- ### Don't forget [the official docs for 4.x](https://expressjs.com/en/4x/api.html).

### Basic Usage

```javascript
app.get("/", (req, res) => {
  res.render("home");
});
```

### Redirect

```javascript
app.get("/login", (req, res) => {
  res.redirect("/signup");
});
```

### Serve a view with no layout

```javascript
app.get("/profile", (req, res) => {
  res.render("profile", { layout: null });
});
```

### Serve a view with a custom layout

```javascript
app.get("/blog", (req, res) => {
  res.render("profile", { layout: "blog" });
});
```

### Pass an object to a view

```javascript
app.get("/user", (req, res) => {
  res.render("user", {
    userid: req.cookie.userid
  });
});
```

### Serve a static file

```javascript
app.get("/status", (req, res) => {
  res.sendFile("path/to/status.html");
});
```

### Serve a static route

```javascript
// this uses express' in-built static middleware
// gleefully serves up all files in the specified directory
app.use(express.static(path.join(__dirname, "public")));
```

### Use route parameters

```javascript
// more (such as regexp) @ https://expressjs.com/en/guide/routing.html
app.get("/api/v1/pokemon/:pokedexNumber", function(req, res) {
  res.render("pokemon", { id: req.params.pokedexNumber });
});
```

### Basic form processing

```javascript
app.post("/signup", (req, res) => {
  console.log(`Information recieved: ${req.body}`); // process that form :D
  res.redirect("/login");
});
```

### JSON response

```javascript
app.get("/api/v1/locations", (req, res) => {
  // this would likely be a db query in production :)
  const locations = [{ id: 1, name: "Brockwell Park", doggos: "plenty" }];
  res.json(locations);
});
```

### 404 Handler

```javascript
// notice 'app.use' and no path (note: you *could* use a path)
// this should go at the end of our routes
app.use((req, res) => {
  res.status(404).render("404");
});
```

### 500 Error

```javascript
// notice 'err' is first argument
// include 'next' even if not needed for express to register as error handler
// more @ expressjs.com/en/guide/error-handling.html
app.use((err, req, res, next) => {
  console.log(err);
  res.status(500).render("error");
});
```

### Use a router object

From the [Express documentation](https://expressjs.com/en/4x/api.html#router):

> A router object is an isolated instance of middleware and routes. You can think of it as a “mini-application,” capable only of performing middleware and routing functions. Every Express application has a built-in app router.
>
> A router behaves like middleware itself, so you can use it as an argument to app.use() or as the argument to another router’s use() method.

```javascript
const express = require("express");
const router = express.router();
const app = express();

// invoked for any requests passed to this router
router.get("/plants", (req, res) => {
  res.render("plants");
});

// pass the router back to the app
app.use(router);
```

### Spin up your server

```javascript
// notice the use of 'set' & 'get'
// app.listen returns a node http.Server object
app.set("port", process.env.PORT || 3000);
app.listen(app.get("port"), () => {
  console.log(`App running on port: ${app.get("port")}`);
});
```
