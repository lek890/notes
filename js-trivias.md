### fetch - to set cookies

`credentials: "include",`

### fetch boilerplate

```
fetch(`${BACKEND_URL}${SIGNIN}`, {
      method: "POST",
      body: JSON.stringify({
        username,
        password
      }),
      credentials: "include",
      headers: {
        "Content-Type": "application/json"
      }
    })
```

### express - serve static files - boilerplate

```
var path = require("path");
var express = require("express");

const PORT = 9000;
const DIST_DIR = path.join(__dirname, "dist");
var app = express();
app.use(express.static(DIST_DIR));

app.get("*", (req, res) => {
  res.sendFile(path.join(DIST_DIR, "index.html"));
});

app.listen(PORT);
```

## BehaviourSubject.getValue()

A Subject or Observable doesn't have a current value. When a value is emitted, it is passed to subscribers and the Observable is done with it.

If you want to have a current value, use BehaviorSubject which is designed for exactly that purpose. BehaviorSubject keeps the last emitted value and emits it immediately to new subscribers.

It also has a method getValue() to get the current value.

### Object.entries

1. Object.entries => gives each entry of object as an array.
2. to update a key in an object using a variable

obj = {[variable]: value}

3. to import default export using alias

import {default as something} from somewhere
