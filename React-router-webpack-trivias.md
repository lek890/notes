1. how to programatically navigate to another page?

- with react route v4+ rendering the <Redirect to="/somewhere"> is a best practice
- export withRouter(component)
  getting the props
  using history.push('/somewhere')
  also works. but its old fashion now

2. Programatically navigating - url changes but not view?

- 'exact' keyword needs to be added to the path in the router switch.

3. programatically navigating - refesh says page not found

- webpack historyApiFallback: true fixes it.
  good read = https://stackoverflow.com/questions/27928372/react-router-urls-dont-work-when-refreshing-or-writing-manually

4. rendering a div to the center using flex

parent - display flex; and height 100%
child - display: iniline-flex, margin : auto

5. webpack hot reloading
   in webpack config

```
output: {
    path: path.join(__dirname, "dist"),
    publicPath: "/dist/"
  },
```

5. configuring webpack config

can be splitted to 3 - common, dev and prod and can be merged with webpack merge plugin and node script commands can be configured to use applicable config files using cli parameters.

6. generating index.html with the bundles attached to it in dist folder?

`HTMLWebpackPlugin` can be used. which will generate a index html and add the generated script bundle to it.

CleanWebpackPlugin for cleanup

7. webpack - to access site from ip rather than localhost

`--host 0.0.0.0`

8. webpack - give env variable for process

```

plugins: [
    new webpack.DefinePlugin({
      "process.env": {
        BACKEND_URL: JSON.stringify("http://localhost:5000/api")
      }
    })
  ]
```

for non process

```
plugins: [
    new webpack.DefinePlugin({
        BACKEND_URL: JSON.stringify("http://localhost:5000/api")
    })
  ]
```

### to use bit components using yarn

- yarn config set "@bit:registry" "https://node.bit.dev/"
- yarn add <@bit/react-bootstrap.react-bootstrap.na>
- import Nav from "@bit/react-bootstrap.react-bootstrap.nav"; in component
- for typings, add declare module "@bit/react-bootstrap.react-bootstrap.nav"; in types/index.d.ts

### Syntax error :unexpected token <

the index html has `<script type="text/javascript" src="/dist/main.js">`
and when main.js is requested html file is served. so parsing failed.

to fix it make the public path in webpack config to be '/'.

now `<script type="text/javascript" src="/main.js">` is generated and will work properly.


Other links:

Webpack intergation to non create-react-app projects: https://www.pluralsight.com/guides/react-typescript-webpack
