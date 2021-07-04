---
title: "Blog Entry Three-Redux ToolKit Tutorial: Part 2 (Action.PayLoad)"
date: "2021-07-03"
description: "Redux Tutorial 2"
---

### Hello everybody, this is the 2nd part of the redux toolkit where we are incorporating the action.payload. A "Payload" is set with an action. There are many different ways you can use a payload and set a payload but we are going to stick with our beginners example so everyone can grasp a basic understanding of what the payload is doing.

![Counter-Slice](https://i.ibb.co/4Nck9F1/counter-Slicepayload.png "counterSlice.js file")

> Going back into our counterSlice.js our slice has a few reducer actions running inside it. We set increment and decrement to to only update the state by adding 1. IncrementByAmount on the other hand wants to update our state by the "action.payload". The payload is pulled off the action that is happening which right now is the IncrementByAmount. We haven't set our payload though yet. All we know is that whatever the payload has in it is going to be whats updating out state.

As you can see that not only is state passed into IncrementByAmount but the action argument is also. This is how were able to use action.payload in our reducer. <br>

Going back in our feature folder to counter.js we can see that the last button we have made is incrementByAmount which was also passed in with our increment and decrement. After adding the rest of our code and attempting to click our incrementByAmount button...nothing will happen. The reason is we haven't given incrementByAmount a payload yet. Add any number into our reducer function call. ` <button aria-label="increment by amount" onClick={() =>dispatch(incrementByAmount(10))}>Increment By Amount</button>` I added a 10. Now click our incrementByAmount button. Our state
will now be changing by 10 as it increments because we gave our action.payload an actual PAYLOAD.

![counter.js](https://i.ibb.co/QMgNYGm/counter-PAYLOAD.png "A look at the action.payload dispatched.")

![counter.js RESULTS](https://i.ibb.co/xhKg2nw/counter-RESULT.png "Check out the result increasing by 10.")

Experiment with your reducers functionality and try adding different payloads. Try to see how else you can change your state and make updates. Our next redux tutorial we'll be taking a much deeper look at reducers, actions, action types, dispatching, and other functionality redux includes.

Again, Thank you for reading!
