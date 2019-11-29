How to watch the files on changes are rerun?

We usually have 

``
  "scripts": {
    "dev": "node ./src/index.js"
  }
``

to run the app

Change it to 

``
  "scripts": {
    "dev": "nodemon --config ./config/nodemon.json ./src/index.js"
  }

``

and add a nodemon.config file

``
{
  "verbose": true,
  "watch": ["src/**/*.js"]
}

``

Voila
