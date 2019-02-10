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
* Install react and react-dom
```console
npm install --save react react-dom
```
* Install webpack, webpack-cli, and webpack-dev-server (webpack recommends a local-only installation)
```console
npm install --save-dev webpack webpack-cli webpack-dev-server
```
* Install the babel packages for transpiling jsx to javascript
```console
npm install --save-dev @babel/core @babel/preset-env @babel/preset-react babel-loader
```
* Install the hot module replacement
```console
npm install --save-dev react-hot-loader
```
* Add scripts to `./package.json` by adding the content:
```text
  "scripts": {
    "dev": "webpack --mode development",
    "build": "webpack --mode production",
    "start": "webpack-dev-server --mode production"
  },
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
* Add the webpack configuration file `./webpack.config.js` with the content:
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
* Create a babel configuration file at `./.babelrc` with the content:
```text
{
  "presets": [
    "@babel/preset-env",
    "@babel/preset-react"
  ]
}
```
* Create a `./dist` directory and base file `.dist/index.html` with the content:
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
* Create a `./src` directory and entry point file `./src/index.js` with the content:
```javascript
import React from 'react';
import ReactDOM from 'react-dom';

const title = 'My Minimal React Webpack Babel Setup';

ReactDOM.render(
  <div>{title}</div>,
  document.getElementById('app')
);

module.hot.accept();
```

## Known Bugs

_None_

## Support and Contact Details

If you have any issues or questions, please email me at philrmass@gmail.com

## Legal

Copyright (c) 2018 Phil Mass

This software is licensed under the MIT License


