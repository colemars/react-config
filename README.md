# React Application Configuration

#### By **Phil Mass**

## Description

_This is a configuration setup for a React application. In this setup, I use the latest versions of all of the npm packages and the latest recommended setup from the package readmes to be as future-proof as possible_

_You can see the deployed app [here](https://philrmass.github.io/react-config/)._

## Setup And Installation

* Git clone the repository at https://github.com/philrmass/react-config.git to a local directory
* Add your own project code

## Steps to Recreate this Configuration
* Create the directory, init git and npm (you can accept the defaults, creates package.json)
```console
mkdir react-config
cd react-config
git init
npm init
```
* Create `./.gitignore` with the content:
```text
# npm and build, allow index.html
node_modules/
dist/*
!dist/index.html

# mac
.DS_STORE/

# vim
*.swp
```
* Install react and react-dom
```console
npm install --save react react-dom
```
* Install webpack and the cli and dev-server(webpack recommends local-only installation)
```console
npm install --save-dev webpack webpack-cli webpack-dev-server
```
* Add a build script using webpack in `./package.json`
```text
  "scripts": {
    "build": "webpack --mode production"
  },
```
* Add a webpack configuration file at `./webpack.config.js` with the content:
* _Note: this includes content for babel, hot-module-loader, and eslint that we haven't installed yet_
```text
const webpack = require('webpack');
const path = require('path');

module.exports = {
  entry: './src/index.jsx',
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        exclude: /node_modules/,
        use: ['babel-loader']
      }
    ]
  },
  resolve: {
    extensions: ['*', '.js', '.jsx']
  },
  output: {
    publicPath: '/',
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js'
  },
  plugins: [
    new webpack.HotModuleReplacementPlugin()
  ],
  devServer: {
    contentBase: './dist',
    hot: true
  }
};
```
* Create the `./dist` directory and content file at `.dist/index.html` with the content:
```html
<!DOCTYPE html>
<html>
  <head>
    <title>React Application</title>
  </head>
  <body>
    <div id="app"></div>
    <script src="./bundle.js"></script>
  </body>
</html>
```
* Create the `./src` directory and entry point file at `./src/index.js` with the content:
```javascript
console.log("Minimal react setup");
```
* Install the babel packages for transpiling back to javascript
```console
npm install --save-dev @babel/core @babel/preset-env @babel/preset-react babel-loader
```
* Create a babel configuration file at `./.babelrc` with the content:
```text
{
  "presets": [
    "@babel/preset-env",
    "@babel/preset-react"
  ]
}
```
* Install the hot module replacement
```console
npm install --save-dev react-hot-loader
```


## Known Bugs

_None_

## Support and Contact Details

If you have any issues or questions, please email me at philrmass@gmail.com

## Legal

Copyright (c) 2018 Phil Mass

This software is licensed under the MIT License


