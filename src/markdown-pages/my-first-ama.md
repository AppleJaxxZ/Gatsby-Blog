---
title: "Blog Entry Two"
date: "06/26/2021"
description: "Redux Tutorial"
---

### Welcome back! Lets dive into React-Redux Toolkit! For those of you who are just learning to use Redux, Redux is designed to enable the use of a global state. The use of global state makes state flow much easier. Instead of passing state through props and "prop tunneling" (which is mainly passing state down through components that wont even be using the state in order to reach it's desired component) we now have a way to access state directly. This creates easily understood code, prevents errors and bugs, and allows our apps to preform better.

> Redux Toolkit is an excellent package for an easier, cleaner, faster way to learn about Redux without all of the verbose boilerplate configuration code. Lets keep it simple and go over Redux toolkit, specifically designed to include everything we need in our Redux project.

I have made this tutorial in a code sandbox which I will link at the end for you to see the final project.
Lets begin by opening a new React-App in your favorite IDE or code sandbox.<br>
open your command line<br>
cd into your project's root folder<br>
then type in the command line<br>
`npm install @reduxjs/toolkit react-redux`<br>
Boom. Wait, thats all we need? YEP! No need to have to install reselect by it's self anymore or any of the other packages you'd normally be installing after the basic react-redux package. It's so convenient right? Awesome! Ok, lets continue! <br>
(If your using code sandbox, just create a new react app template, on the bottom left side of your screen go to dependencies and type in react-redux, hit enter, then also type in @redux-toolkit)<br>

![Dependencies](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Dependencies Added To Our Project") <br>

### Ok, now lets set up our redux store.

In your root folder, (the same folder that holds app.js and index.js) create a new file called "store.js" Store holds the reducers we'll be making and distributes them to our app. <br>
At the top of store.js type `import { configureStore } from '@reduxjs/toolkit'`<br>

### Next under the configureStore type<br>

`export default configureStore({reducer:{ }})`<br>
({configureStore} automatically configures Redux DevTools extension so you can inspect the store while developing AND creates our redux store which will store each reducer.)<br><br>

### Ok, store is created. Lets make the store available to our React components by putting a React Redux `<Provider>` around our application in our index.js file. <br>

So open up index.js.. import our store now by `import store from './app/store'`<br>
under that, type `import { Provider } from 'react-redux'`<br>
Then wrap your `<App />` component with the `<Provider store={store}>` component while passing store equals store as a prop. This just added our Redux store into our app. We will now have the ability to pass out reducers state around our application. <br>

Your index.js file should now look alot like this.....<br>
![Set up for Store And Provider](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "imported store and provider and set up provider and store.") <br>

<!-- <iframe width="560" height="315" src="https://www.youtube.com/embed/DXJO3AraeMQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe> -->
