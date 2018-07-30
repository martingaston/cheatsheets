# Heroku Cheatsheet

### Heroku's [getting started](https://devcenter.heroku.com/articles/getting-started-with-nodejs) resource is generally pretty fantastic

### Install CLI (Ubuntu) and Login

```bash
$ sudo snap install heroku --classic
$ heroku login
```

### Create an app in a git repository

```bash
$ heroku create # pass a parameter to declare your own app name
$ git push heroku master
```

### Spin up a dyno

```bash
$ heroku ps:scale web=1
```

### Set a few node.js variables

```javascript
const http = require("http");
const router = require("./router");
// process.env.HOSTNAME and PORT are useful here - Heroku can throw an error w/o
const hostname = process.env.HOSTNAME || "localhost";
const port = process.env.PORT || 4000;
```

### Run in Browser

```bash
$ heroku open
```

### View Logs

```bash
$ heroku logs
$ heroku logs --tail
```

### Set Environment Variables

```bash
$ heroku config
$ heroku config:set KEY=VALUE
$ heroku config:unset KEY
```

### Bash

```bash
$ heroku run bash
```

### Restart

```
$ heroku restart
```
