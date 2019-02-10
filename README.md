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
node_modules
build
.DS_STORE
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
```text
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    publicPath: '/',
    path: path.resolve(__dirname, 'dist')
    filename: 'bundle.js'
  }
};
```
* Create the src directory and entry point file at `./src/index.js` with the content:
```javascript
console.log("Minimal react setup");
```

## Known Bugs

_None_

## Support and Contact Details

If you have any issues or questions, please email me at philrmass@gmail.com

## Legal

Copyright (c) 2018 Phil Mass

This software is licensed under the MIT License


