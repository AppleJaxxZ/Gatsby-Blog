---
title: "Blog Entry Two"
date: "06/26/2021"
description: "Redux Tutorial"
---

### Welcome back! Lets dive into React-Redux Toolkit! For those of you who are just learning to use Redux, Redux is designed to enable the use of a global state. The use of global state makes state flow much easier. Instead of passing state through props and "prop tunneling" (which is mainly passing state down through components that wont even be using the state in order to reach it's desired component) we now have a way to access state directly. This creates easily understood code, prevents errors and bugs, and allows our apps to preform better.

> Redux Toolkit is an excellent package for an easier, cleaner, faster way to learn about Redux without all of the verbose boilerplate configuration code. Lets keep it simple and go over Redux toolkit, specifically designed to include everything we need in our Redux project.

### Today we're making a simple increment/decrement counter app.

I have made this tutorial in a code sandbox which I will link at the end for you to see the final project.
Lets begin by opening a new React-App in your favorite IDE or code sandbox.<br>
open your command line<br>
cd into your project's root folder<br>
then type in the command line<br>
`npm install @reduxjs/toolkit react-redux`<br>
Boom. Wait, thats all we need? YEP! No need to have to install reselect by it's self anymore or any of the other packages you'd normally be installing after the basic react-redux package. It's so convenient right? Awesome! Ok, lets continue! <br>
(If your using code sandbox, just create a new react app template, on the bottom left side of your screen go to dependencies and type in react-redux, hit enter, then also type in @redux-toolkit)<br>

![Dependencies](https://i.ibb.co/W0WynJ5/dependecies.png "Dependencies Added To Our Project") <br>

### Ok, now lets set up our redux store.

https://i.ibb.co/3BtC6Fq/create-Slice.png

https://i.ibb.co/DQ4Q5CF/feature-counter-JS.png
https://i.ibb.co/55cS8zM/finished-Redux.png

In your root folder, (the same folder that holds app.js and index.js) create a new file called "store.js" Store holds the reducers we'll be making and distributes them to our app. <br>
At the top of store.js type `import { configureStore } from '@reduxjs/toolkit'`<br>

### Next under the configureStore type<br>

`export default configureStore({reducer:{ }})`<br>
({configureStore} automatically configures Redux DevTools extension so you can inspect the store while developing AND creates our redux store which will store each reducer.)<br><br>

### Ok, store is created. Lets make the store available to our React components by putting a React Redux `<Provider>` around our application in our index.js file. <br>

So open up index.js.. import our store now by `import store from './app/store'`<br>
under that, type `import { Provider } from 'react-redux'`<br>
Then wrap your `<App />` component with the `<Provider store={store}>` component while passing store equals store as a prop. This just added our Redux store into our app. We will now have the ability to pass out reducers state around our application. <br>

Your index.js file should now look a lot like this.....<br>
![Set up for Store And Provider](https://i.ibb.co/1vQ0Sfm/Provider.png "imported store and provider and set up provider and store.") <br>

### Moving forward... Lets create our "Slice" and dig in.

Create a new folder called "features" inside your src folder. Inside the "features" folder create a folder called "counter" inside the "counter folder create a FILE called `counterSlice.js`...What we are doing in this file is importing the createSlice API from redux toolkit. Essentially what we want to accomplish here is creating a name to identify our state, setting it's initial state, telling our reducers what we want to do with that state and creating some actions to be called on to make these changes to the state. <br>
A few key points to remember are `createSlice` is just taking a bunch of ingredients and putting them together. <br>
`name` is just the name of our state. <br>
`initialState` is just the state value we are beginning with. So if were making a counter, we're likely going to want our counter to start at the number 0 right? Unless there is some reason we would need to start at another number but in this case were just counting how many times we hit the increment button. So we need to start at 0. <br>
`reducers` are basically the actions that are going to be updating the state in some way. example...one of our reducers is called "increment". Im sure you can guess what that reducer is going to do to our state huh? Yep, you got it, it will increment our state depending on how much we tell it to. <br>
`actions` they are just the names of each of the reducers we made. Simple as that.

### Lets start this file out by tying `import { createSlice } from '@reduxjs/toolkit'`

Next we want to create our counterSlice variable and counterSlice.actions. Ill show you what it looks like first, then ill explain whats going on. <br>
![createSlice](https://i.ibb.co/3BtC6Fq/create-Slice.png "imported createSlice and set up our state, reducers and actions..") <br>

<!-- <iframe width="560" height="315" src="https://www.youtube.com/embed/DXJO3AraeMQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe> -->
