# Quick Set up
```sh 
npx create-react-app my-app
cd my-app
npm start
npx 
```

# Creating a React App… From Scratch
## Setup
> To get started, create a new directory for your React app. Then, initialize your project with **npm init** and open it in an editor of your choice.
It’s also a pretty good time to **git init** as well. In your new project folder, create the following structure:
```sh
.
+-- public
+-- src
```
> Our public directory will handle any static assets, and most importantly houses our index.html file, which react will utilize to render your app.
### Babel
Go ahead and run 
```sh 
npm install --save-dev @babel/core@7.1.x @babel/cli@7.1.x @babel/preset-env@7.1.x @babel/preset-react@7.0.x
```
> **babel-core** is the main babel package — We need this for babel to do any transformations on our code. **babel-cli** allows you to compile files from the command line. **preset-react** and **preset-env** are both presets that transform specific flavors of code — in this case, the **env** preset allows us to transform ES6+ into more traditional javascript and the react preset does the same, but with JSX instead.
In the project root, create a file called **.babelrc**. Here, we’re telling babel that we’re going to use the env and react presets.
```sh
{
  "presets": ["@babel/env", "@babel/preset-react"]
}
```

### Webpack
> Now we need to acquire and configure Webpack. We’ll need a few more packages, and you’ll want to save these as **dev dependencies**: 
```sh
npm install --save-dev webpack@4.19.x webpack-cli@3.1.x webpack-dev-server@3.1.x style-loader@0.23.x css-loader@1.0.x babel-loader@8.0.x  dotenv-webpack@8.0.x
```
### React
> First, we’ll need to get two more packages: ***react@16.5.x*** and ***react-dom@16.5.x*** Go ahead and save those as regular dependencies.
***ReactDOM***.render is the function that tells React what to render and where to render it — In this case, we’re rendering a component called App and it’s being rendered at the DOM element with the ID root.
Now, create another file in src called App.js. If you’ve worked with React using create-react-app this part should be extremely familiar. This file is just a React component.

### Finishing HMR
>If you run the server now, you’ll notice none of your changes actually cause anything to happen in the client. What gives?
Well, HMR needs to know what to actually replace and currently we haven’t given it anything. For that, we’re going to use a package one of the folks on the react team have provided us: ***react-hot-loader@4.3.x**
You can install this as regular dependency — as per the documentation
Note: You can safely install react-hot-loader as a regular dependency instead of a dev dependency as it automatically ensures it is not executed in production and the footprint is minimal.
Now, import react-hot-loader in App.js and mark the exported object as hot-reloaded by modifying to code as follows.
