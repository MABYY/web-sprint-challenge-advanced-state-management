# Advanced State Management Sprint Challenge

**Read these instructions carefully. Understand exactly what is expected _before_ starting this Sprint Challenge.**

This challenge allows you to practice the concepts and techniques learned over the past sprint and apply them in a concrete project. This sprint explored **advanced state management**. During this sprint, you studied **the reducer pattern, and redux**. 

This is an individual assessment. All work must be your own. Your challenge score is a measure of your ability to work independently using the material covered through this sprint. You need to demonstrate proficiency in the concepts and objectives introduced and practiced in preceding days.

This is an individual assessment. All work must be your own. All projects will be submitted to codegrade for automated review. You will also be given feedback by code reviewers the Monday after challenge submissions. For more information on the review process [click here.](https://www.notion.so/lambdaschool/How-to-View-Feedback-in-CodeGrade-c5147cee220c4044a25de28bcb6bb54a)

You are not allowed to collaborate during the sprint challenge. 

## Introduction

In this challenge, you are to build a Smurfs village database utilizing Redux as your state management system. Build this challenge from the ground up using what you have learned about state management.

## Project Setup
* [ ] Run npm install to install your dependencies.
* [ ] Run npm start to run your frontend and backend code automatically.
* [ ] Note your backend code will run automatically when your run npm start. There is no need to seperately run a server.js file and no means to test the server through postman or the browser. Feel free to ignore any messages related to MSW or mock service workers.

## Project Instructions

In this project, you will build the reducer, actions and basic redux connects nessiary to display smurf data. You will be implementing both thunk and traditional redux actions.

 
## Project Requirements

#### Complete reducers/index.js
  Add in the needed state and reducer cases to hold and modify smurf error messages, loading status and smurf data. **If at all possible, add in action cases one at a time, instead of all at once. Test your state connects and reducer cases as nessisary.**

  * [ ] Adds the following state values into the initialState:
      - an array of smurfs
      - a boolean indicating if the app is loading
      - a string indicating a possible error message

  * [ ] Add in the arguments needed to complete a standard reducer function.
  * [ ] Add in a reducer case to accommodate the start of a smurf fetch.
  * [ ] Add in a reducer case to accommodate the successful smurf api fetch.
  * [ ] Add in a reducer cases to accommodate an error.
  * [ ] Add in a reducer case to accommodate adding a smurf (including the name, nickname, position, description and an internally generated id) into your smurf list.
  * [ ] Add in a reducer case that adds in a value to the error message.

### Complete index.js
  Connect your application to reducer through redux with the thunk and logger middleware packages attached.

### Complete actions/index.js
  Add in the action creators and action constants needed to add a smurf to state and fetch smurfs from the server. **If at all possible, add in action cases one at a time, instead of all at once. Test your state connects and reducer cases as nessisary.**

  * [ ] Add a thunk action called fetchSmurfs that triggers a loading status display in our application, performs an axios call to retreive all smurfs from the api. Save the result of to our state and show an error if one is made.
  * [ ] Add a standard action that allows us to add new smurf (including the name, nickname, position, summary).
  * [ ] Add a standard action that allows us to set the value of the error message slice of state.
  
### Complete App.js
  Connect component to the fetchSmurfs action.
  
  * [ ] Connect the fetchSmurfs actions to the App component.
  * [ ] Call the fetchSmurfs action when the component first loads.

### Complete components/SmurfList.js
  Connect this component to your smurfs and loading screen state slices.
  
  * [ ] Connect the smurfs and loading state values to the SmurfList component.
  * [ ] Replace the single Smurf component instance with a map return a Smurf component for each entry in the smurfs list.
  * [ ] Replace the static isLoading variable with the state loading variable.

### Complete components/AddForm.js
  Connect this component to the error state slice, setError and addSmurf actions. Complete the form handling code.

  * [ ] Connect your error state slice, setError and addSmurf actions to the AddForm component.
  * [ ] Replace all instances of the errorMessage static variable with your error message state slice. 
  * [ ] Within the handleSubmit function, replace the static assignment to errorMessage with a call to the setError action. Test that an error is displayed when validation code fails.
  * [ ] Within the handleSubmit function, call your addSmurf action with the smurf name, position, nickname and summury passed as arguments. Test that a smurf is correctly added to when the form is submitted.

## Important Notes:

* Again, unlike other projects, the local server used here can not be accessed through the browser. For this and the rest of your sprint challenges, test the functioning of the server directly through your axios calls.
* Note that a test file `codegrade.test.js` is include with some simple, baseline tests for your submission. Please make sure they pass before considering your project complete.
* You are welcome to create additional files but **do not move or rename existing files** or folders.
* Do not alter your `package.json` file except to install extra libraries.
* In your solution, it is essential that you follow best practices and produce clean and professional results.
* Schedule time to review, refine, and assess your work and perform basic professional polishing including spell-checking and grammar-checking on your work.

## API documentation 

#### API Documentation
* **[GET]** to `http://localhost:3333/smurfs`: returns the list of all smurfs objects.
* **[POST]** to `http://localhost:3333/smurfs`: creates a new smurf object. Pass smurf data through the `body` of the request.

* **Smurf Object Structure** 
```js
[
  {
    id:"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9",
    name:'Poppa Smurf',
    position:'Village Leader',
    nickname: 'Pops',
    description: 'Papa is the practical village leader and the father figure of 100 or so young Smurfs. He is easily identified by his red Smurf hat, pants, and a shortly-trimmed white beard and moustache.'
  }
];
```

## Submission format
* [ ] Submit via Codegrade by commiting and pushing any new changes to **your main branch.**
* [ ] Check Codegrade before the deadline to compare its results against your local tests.
* [ ] Check Codegrade on the days following the Sprint Challenge for reviewer feedback. For more information on how to access and read your feedback, check [here](https://www.notion.so/lambdaschool/How-to-View-Feedback-in-CodeGrade-c5147cee220c4044a25de28bcb6bb54a)
* [ ] New commits will be evaluated by Codegrade if pushed before the sprint challenge deadline.

## Interview Questions

Be prepared to demonstrate your understanding of this week's concepts by answering questions on the following topics. Add your answers to the questions within `interview_answers.md` file. These will not be counted as a part of your sprint score but will be helpful for preparing you for your endorsement interview, and enhancing overall understanding.

1. What problem does the context API help solve?

Context API is a more organized and neat way to pass data through intermediate components. However, the user should bear in mind tge caveat that context API makes components harder to reuse.

2. In your own words, describe `actions`, `reducers` and the `store` and their role in Redux. What does each piece do? Why is the store known as a 'single source of truth' in a redux application?

Mutable objects are objects whose state is allowed to change over time. An immutable value is the exact opposite. When we enforce immutability, we can keep our application architecture and mental model simple, which makes it easier to reason about the application. 

Immutability makes it really easy to see if anything has changed. For example when we change the state in Redux, our components props will update. We can check our previous props against our new props to know what change occurred, and know how to handle those changes.
Redux has a single immutable state tree (referred to as the store) where all state changes are explicitly handled by dispatching actions. 

Dispatched actions are processed by a reducer that accepts the previous state and the action and returns the next state of your application. It is easy to predict how the state tree is going to change based on actions that are dispatched. It is also easy to predict which action will be dispatched based on some event or interaction. This all leads to very predictable state management.

Reducer functions take two arguments – the current state and action – and return a new, updated state object based on both arguments.Reducer functions are the perfect fit for managing changes in state while maintaining the immutability we want in our components.The action, represented by an object, contains properties related to some action that happens in our apps. Every action object is required to have a type property, which will "inform" the reducer actions happening in the app. The type allows the reducer to know what part of the state needs to change.

The useReducer hook is an alternative to useState (useState actually uses useReducer hook under the hood). It is preferable when you have complex logic that you have to deal with in a component, or when you find yourself with a lot of state properties (more than 3) in a single component. useReducer, takes in a reducer function (that we build), as well as a value for the initialState. Then it returns both the current state and a dispatch method in an array, just like useState does.

const [state, dispatch] = useReducer(reducer, initialState);

The dispatch method is a significant addition to our arsenal here. It will "dispatch" an action to our reducer when specific events occur in our application. The dispatch allows us to powerfully combine the reducer function from our previous section, with the ability to maintain our state at the level of the component.

The useReducer hook has all the functionality we love from the useState hook and combines it with the power of the reducers we are building ourselves. In doing so, it provides access to both the state and a function that dispatch actions to our reducer.


3. What does `redux-thunk` allow us to do? How does it change our `action-creators`?

Redux is a predictable state management library for JavaScript applications and is the most popular State container for React applications
The core concepts/principles of Redux are 3 fold:

1-The Store: Everything that changes within your application is represented
by a single JavaScript Object known as the store. The store
contains our state for our application.

2- Application state is Immutable: When the application state changes, we clone the state object, modify the clone, and replace the original state with the new copy. We never mutate the original object, and we never write to our store object.

3- Pure functions change our state: Given the same input, a pure function returns the same output every time. All functions (reducers) in Redux must be pure functions. Meaning they take in some state and a description of what changes took place and return a copy of our state. We can do so using the connect function, within the components themselves. We can also build a helper function within the component files to tell the connect function what pieces of state we want to access. This function is usually named mapStateToProps, and it will map pieces of our Redux state to the props of our component.

- The first step we're going to take to enable Redux within a React application is to install it.

- createStore will take in a single reducer that represents the state (data) of our application globally. We need to create a store variable, and use createStore to create the Redux store.

Now that we have a store, we want to make our application aware of it. The way this works is that react-redux gives us a <Provider></Provider> component that wraps around our entire application. Then, all we need to do is wrap our <App/> with the <Provider> component and pass a store prop set equal to the store we created. This will look like this:

Now that we have built a store to manage our state, we need to connect our components to that store. 

Actions in Redux are packets of information that contain an action type and associated data. In code, an action is simply an object with up to two properties - a type property and an optional payload property. Each action MUST have a type property. The type property is a string that explains what interaction just happened. Actions are "dispatched" to our reducer. When our reducer recieves an action, it will update the state according to the type and payload on the action.

Actions should not be confused with action creators. Action creators are a middle step between events/interactions and the dispatch process. They make it possible to write reusable functions that can create actions on the fly, rather than us hard coding actions into our components. 

Redux reducers must not contain side effects, but real applications require logic that has side effects. Some of that may live inside components, but some may need to live outside the UI layer. Thunks (and other Redux middleware) give us a place to put those side effects.

Redux Thunk middleware allows you to write action creators that return a function instead of an action. The thunk can be used to delay the dispatch of an action, or to dispatch only if a certain condition is met.
Thunks allow us to write additional Redux-related logic separate from a UI layer. This logic can include side effects, such as async requests or generating random values, as well as logic that requires dispatching multiple actions or access to the Redux store state.


4. What is your favorite state management system you've learned and this sprint? Please explain why!

