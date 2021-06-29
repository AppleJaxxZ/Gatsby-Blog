---
title: "Blog Entry Two-Redux ToolKit Tutorial"
date: "06-26-2021"
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

Ok, a lot of new things going on im sure. So lets break it down...all were doing here is creating an object. Inside this object we set up our states name which is `counter` , its initial state...which we decided would be a `value` of `0`, and created our reducers. The first reducer we made passes state into it, takes that state's current value and adds 1 to it. Hence the `state.value += 1`. <br>
Then we moved along to the `decrement` same thing here...but this time it's `state.value -= 1` this reducer function takes 1 away now every time is called. <b.vr>
and lastly we have `incrementByAmount` here were doing something a little different but not much....we took our `state.value += action.payload`. <br>

### Wait, what is this action.payload?

Im going to be explaining action.payload and how we use it in the next redux tutorial post. So for now, Get a fair grasp on what is happening in our reducers at this time. Notice how we set our initial state value and how we create these reducers which tell our state how to change and respond. <br>

If you have ever used react-redux before you'll notice that we didn't have to first spread our state first. That's because redux toolkit uses the "immer library" which detects changes to a "draft state" which produces a new mutable state based off those changes.

### Lastly in our counterSlice.js file at the bottom there is `export const { increment, decrement, incrementByAmount } = slice.actions`

Here we've destructed each reducer name off slice.actions. This export is going to allow us to use our slice reducers in our next file which will enable us to render a state change after the user clicks increment or decrement. <br>
Finally just `export default counterSlice.reducer` at the bottom so we can add our newly created slice to our redux store.

### Now navigate back to our store.js

Go ahead and import our counterReducer ...`import counterReducer from './features/counter/counterSlice.js'` then simply add our state name "counter" and its reducer inside the configureStore . Store.Js should now look like this....<br>
![Add reducer to store](https://i.ibb.co/ZXd4ptL/sliceto-Store.png "imported counterReducer and aded counter: counterReducer to our store.") <br>

### After updating our redux store...we can now use React Redux hooks to let React Components interact with the store. `useSelector` will read data from the store,

`useDispatch` will dispatch the actions.

### Create a nea w file inside of your counter folder inside features. src/features/counter/Counter.js Create functional component called `Counter` and export it at the bottom of the file. Then import it in App.js and render the component inside <App>.

Doing this is going to allow us to see the App begin rendering in real time.<br>
This is what the file will look like when it's done. Ill explain everything inside of our Counter component after you look at the example so you can get a visual of what is happening.

![Counter Feature](https://i.ibb.co/DQ4Q5CF/feature-counter-JS.png "This is how we'll be passing our global state and rendering increments and decrements.") <br>

### OK. Whats all this about??? Lets begin with....

`const count = useSelector((state) => state.counter.value)` and <br> `const dispatch = useDispatch()`<br>
First we set count as our variable equal to useSelector hook which grabs the state from our counterSlice.js file. The state we want to grab is the counter's value. Which we set to start at 0. Now count will represent our state at all times. The value dispatch is set to useDispatch() which allows us to dispatch our reducers into action whenever we tell it to. <br>

`onClick={() => dispatch(increment())}` Look! We used an onClick listener to wait for a button click....on the click it then dispatches the reducer "increment()" to do it's job which was updating our state.value += 1 remember? And below increment you can see decrement doing the same thing! <br>

After you type the rest out like we did above you'll be able to render your state changes immediately in browser window. Go ahead and type `npm start` play with the buttons. Open your react-redux dev tools and watch how each action is dispatching it's reducer's actions to update the state! <br>

Your output should look something like this....<br>

![Output](https://i.ibb.co/55cS8zM/finished-Redux.png "Code finalized and rendered on your browser window..") <br>

### Heres A Link To A CodeSandBox Version

![CodeSandBox](https://codesandbox.io/s/simple-reduxtoolkit-example-forked-3n1s9?file=/src/App.js "CodeSandBox Version") <br>

### Thats it! Before you go, think about how easy it is to pass our state through our app now. Yes there is a little setup but in the long run it saves us a lot of time, debugging, errors, and prop tunneling. With a redux global state you' re free to send your state across your App without complications, intensely thought out state flow planning or slowing your app down by passing state through components that wont even be using that state. <br>

I hope your enjoyed the tutorial and will come back for part 2, using React-redux action.payloads with a new example of how to use it. Thank you!

<!-- <iframe width="560" height="315" src="https://www.youtube.com/embed/DXJO3AraeMQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe> -->
