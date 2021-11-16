# React

## Start a new project

```bash
npx create-react-app
```

generate starter code  for react application

## Basic File Structure

```
my-app/
  README.md
  node_modules/
  package.json
  public/
    index.html
    favicon.ico
  src/
    App.css
    App.js
    App.test.js
    index.css
    index.js
    logo.svg
```

### node-modules

contains basic node-js project files

### public

contains `index.html` which is main entry point for every app

contains other public usage like icons logos

### src

 `app.css` is the main css styles for the app

`app.js` the main component to render

`index.css` the css for index.js

`index.js` the main js file to link

For the project to build, **these files must exist with exact filenames**:

- `public/index.html` is the page template;
- `src/index.js` is the JavaScript entry point.

recommended not to edit them at all

## JSX

 A syntax extension to JavaScript. to build component that is written like html

### basic usage

```jsx
<h1>Hello, world!</h1>;
```

### embed expressions

```jsx
const name = 'Josh Perez';
const element = <h1>Hello, {name}</h1>;
```

### using conditions

```jsx
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }
  return <h1>Hello, Stranger.</h1>;
}
```

#### conditional rendering

this will only render if the  condition is true

```jsx
(condition && <h1>Hello World</h1>)
```

### loop rendering

```jsx
{
  this.state.movies.map((movie) => (
    <tr key={movie._id}>
      <td>{movie.title}</td>
      <td>{movie.genre.name}</td>
      <td>{movie.numberInStock}</td>
      <td>{movie.dailyRentalRate}</td>
      <td>
        <button
          onClick={() => this.handleDelete(movie)}
          className="btn btn-danger btn-sm"
        >
          Delete
        </button>
      </td>
    </tr>
  ));
}
```

### Fragment

jsx statment should render only one root component use fragment to render more than one component

```jsx
<React.Fragment>
  <h1>Hello</h1>
  <p>hello world</p>
</React.Fragment>
```

### tips

* class is className in jsx

* styles is an object
  
  ```jsx
    <i
      onClick={props.onClick}
      style={{ cursor: "pointer" }}
      className={classes}
      aria-hidden="true"
    />;
  ```

## Component

### Class Component

recommended to use if the component has a state or need to use the life cycle method

```jsx
import { Component } from "react";

class App extends Component {
   render() {
    return <div> </div>
  }
}

export default App;
```

#### Lifecycle Methods

##### Constructor

The constructor for a React component is called before it is mounted.

Typically, in React constructors are only used for two purposes:

- Binding `event handler`methods to an instance.
* assign the initial state to `this.state` directly in the constructor:

```jsx
constructor(props) {
  super(props);
  // Don't call this.setState() here!
  this.state = { counter: 0 };
  this.handleClick = this.handleClick.bind(this);
}
```

##### ComponentDidUpdate

called after the component renders 

* make network calls

* compare the prev props

```jsx
componentDidUpdate(prevProps) {
  // Typical usage (don't forget to compare props):
  if (this.props.userID !== prevProps.userID) {
    this.fetchData(this.props.userID);
  }
}
```

##### componentWillUnmount

called when component to be removed

* used as clean up 

* close connections

```jsx
componentWillUnmount() {
    cleanup();
}
```

### Function

```jsx
import React from "react";
export default function UserItem() {
  return (
    <div className="card text-center">
    </div>
  );
}
```

## Props

used to send parameter down in the components tree

### Sending

sending it as a attribute

```jsx
import React from "react";
export default function Garage() {

  return (
    <div className="card text-center">
        <Car carNum="12345"/>
    </div>
  );
}
```

### Receiving

receiving it in the function component

```jsx
import React from "react";
export default function Car(props) {
  return (
    <div className="card text-center">
        {props.carNum}
    </div>
  );
}

// using object destruction

export default function Car({carNum}) {
  return (
    <div className="card text-center">
        {props.carNum}
    </div>
  );
}
```

in class component

```jsx
class App extends Component {
   render() {
    return (
     <div className="card text-center">
        {this.props.carNum}
    </div>
);
  }
}
```

## Routing

```sh
npm install react-router-dom
```

### BrowserRouter

component add to the root of the components tree to handle routing

```jsx
 <BrowserRouter>
    <App />
  </BrowserRouter>
```

### Switch

match the given url to a route component works as switch case match only the first

recommended to add routes from more specific to general

```jsx
<Switch>
  <Route path="/products/:id" component={ProductDetails} />
  <Route path="/posts/:year?/:month?" component={Posts} />
  <Route path="/admin" component={Dashboard} />
  <Route path="/" exact component={Home} />
  // if no match
  <Redirect to="/not-found" />
</Switch>;
```

### Route

render a component based on the current url

#### simple route

```jsx
  <Route path="/products/" component={ProductDetails} />
```

#### Route with params

```jsx
<Route path="/products/:id" component={ProductDetails} />
// optional params
<Route path="/posts/:year?/:month?" component={Posts} />
```

### nested routers

without using switch all url matches rendered to the screen so nested routes can be done by using router tags without switch

```jsx
// in dash board component in switch above
 <div>
  <h1>Admin Dashboard</h1>
  <SideBar />
  <Route path="/admin/users" component={Users} />
  <Route path="/admin/posts" component={Posts} />
</div>;
```

#### Route with custom porps

```jsx
<Route
   path="/products"
   render={(props) => <Products sortBy="newest" {...props} />}
/>
```

#### default prpos

##### match

contains information about how a Route path matched the URL. match objects contain the following properties:

- `params` - (object) Key/value pairs parsed from the URL corresponding to the dynamic segments of the path
- `isExact` - (boolean) true if the entire URL was matched (no trailing characters)
- `path` - (string) The path pattern used to match. Useful for building nested Routes
- `url` - (string) The matched portion of the URL. Useful for building nested Links

#### history

`history` objects typically have the following properties and methods:

- `length` - (number) The number of entries in the history stack
- `action` - (string) The current action (`PUSH`, `REPLACE`, or `POP`)
- `location` - (object) The current location. May have the following properties:
  - `pathname` - (string) The path of the URL
  - `search` - (string) The URL query string
  - `hash` - (string) The URL hash fragment
  - `state` - (object) location-specific state that was provided to e.g. `push(path, state)` when this location was pushed onto the stack. Only available in browser and memory history.
- `push(path, [state])` - (function) Pushes a new entry onto the history stack
- `replace(path, [state])` - (function) Replaces the current entry on the history stack
- `go(n)` - (function) Moves the pointer in the history stack by `n` entries
- `goBack()` - (function) Equivalent to `go(-1)`
- `goForward()` - (function) Equivalent to `go(1)`
- `block(prompt)` - (function) Prevents navigation

##### location

Locations represent where the app is now, where you want it to go, or even where it was.

- `pathname` the current path '/somewhere',

- `search` the addition search parameters '?some=search-string'

#### Link

  router tag like <a></a> in html but save the state of the app

```jsx
 <Link
 to="/movies/new"
 className="btn btn-primary"
 style={{ marginBottom: 20 }}
 ></Link>;
```

#### Redirect

is route component that redirect to other routes

```jsx
<Redirect from="/messages" to="/posts" />
```

## Hooks

use state and life cycle methods in function component

#### State

```jsx
const [songs, setSongs] = useState([
    { title: 'almost home', id: 1 },
  ]);

  const addSong = (title) => {
    setSongs([...songs, { title, id: 2 }]);
  };
```

#### life cycle

```jsx
// function called on mount and re renders
useEffect(() => {
    console.log('useEffect callback', songs);
  });
```

```jsx
// function called on mount and re renders only if songs change
useEffect(() => {
    console.log('useEffect callback', songs);
  }, [songs]);
```

## Context

used to share state between component using provider pattern

### Define Context

```jsx
const AuthContext = createContext();
```

### Provide context

```jsx
 <AuthContext.Provider value={{...this.state, toggleAuth: this.toggleAuth}}>
</AuthContext.Provider>
```

**export reusable provider**

```jsx
class AuthContextProvider extends Component {
  state = {
    isAuthenticated: false
  }
  toggleAuth = () => {
    this.setState({ isAuthenticated: !this.state.isAuthenticated });
  }
  render() { 
    return (
      <AuthContext.Provider value={{...this.state, toggleAuth: this.toggleAuth}}>
        {this.props.children}
      </AuthContext.Provider>
    );
  }
}

export default AuthContextProvider;
```

### Consume Context

#### Class component

##### using consumer component

```jsx
  <AuthContext.Consumer>
  {(authContext) => (
        // use value
      )}
 </AuthContext.Consumer>
```

##### using context type

```jsx
static contextType = ThemeContext;
const value = this.context;
```

##### using multi context

```jsx
<AuthContext.Consumer>
  {(authContext) => (
    <ThemeContext.Consumer>
      {(themeContext) => {
       }}
    </ThemeContext.Consumer>
  )}
</AuthContext.Consumer>;
```

#### Function Component

#### using hooks

```jsx
const value = useContext(BookContext);
```

## Reducers

pattern to invoke action on the state using single method

#### define reducer

```jsx
export const bookReducer = (state, action) => {
  switch (action.type) {
    case 'ADD_BOOK':
      return [...state, {
        title: action.book.title, 
        author: action.book.author, 
        id: uuid()}
      ]
    case 'REMOVE_BOOK':
      return state.filter(book => book.id !== action.id);
    default:
      return state;
  }
} 
```

#### use reducer

```jsx
const BookContextProvider = (props) => {
  const [books, dispatch] = useReducer(bookReducer, []);
  return (
    <BookContext.Provider value={{ books, dispatch }}>
      {props.children}
    </BookContext.Provider>
  );
}
const { dispatch } = useContext(BookContext);
dispatch({ type: 'ADD_BOOK', book: { title, author }});
```

## Redux

global state managing library using reducer pattern

### components

#### Store

The Redux **store** brings together the state, actions, and reducers that make up your app. The store has several responsibilities:

- Holds the current application state inside
- Allows access to the current state via `store.getState()`
- Allows state to be updated via `store.dispatch(action)`
- Registers listener callbacks via `store.subscribe(listener)`
- Handles unregistering of listeners via the `unsubscribe` function returned by `store.subscribe(listener)`.

```js
const store = createStore(reducer);
export default store;
```

#### Reducers

A reducer is a pure function, which returns the state of the application based on the action dispatched by the store.

```js
export default function reducer(state = [], action) {
  switch (action.type) {
    case 'bugAdded':
      return [
        ...state,
        {
          id: ++lastId,
          description: action.payload.description,
          resolved: false,
        },
      ];
    case 'bugRemoved':
      return state.filter((bug) => bug.id !== action.payload.id);
    default:
      return state;
  }
}
```

#### Action

It is a payload of information that transmits data from an application to a store. They are the sole source of information for the store. One can send them to the store using store. dispatch() .

An action is Redux speaks for a plain object with a property called type. Actions are free-forms things.

```js
store.dispatch({
  type: 'bugRemoved',
  payload: {
    id: 1,
  },
});
```

### Redux Structure

```
my-app/
  src/
    store/
      configureStore.js
      state.js
```

`configureStore` contain the base store action

```js
import { createStore } from 'redux';
import { devToolsEnhancer } from 'redux-devtools-extension';
import reducer from './bugs';

export default function configureStore() {
  const store = createStore(reducer, devToolsEnhancer({ trace: true }));
  return store;
}
```

`state` contain the actions and the reducers functions

```js
// Action Types
const BUG_ADDED = 'bugAdded';
const BUG_REMOVED = 'bugRemoved';
const BUG_RESOLVED = 'bugResolved';

// Action creators
export const bugAdded = (description) => ({
  type: BUG_ADDED,
  payload: {
    description,
  },
});

export const bugRemoved = (id) => ({
  type: BUG_REMOVED,
  payload: {
    id,
  },
});

export const bugResolved = (id) => ({
  type: BUG_RESOLVED,
  payload: {
    id,
  },
});

// Reducer
let lastId = 0;

export default function reducer(state = [], action) {
  switch (action.type) {
    case BUG_ADDED:
      return [
        ...state,
        {
          id: ++lastId,
          description: action.payload.description,
          resolved: false,
        },
      ];
    case BUG_REMOVED:
      return state.filter((bug) => bug.id !== action.payload.id);
    case BUG_RESOLVED:
      return state.map((bug) =>
        bug.id !== action.payload.id ? bug : { ...bug, resolved: true }
      );
    default:
      return state;
  }
}
```

### Redux Toolkit

a cleaner way to wrte redux code

#### store

```js
export default function () {
  return configureStore({ reducer });
}
```

#### reducer & actions

```js
// Action creators
export const bugAdded = createAction('bugAdded');
export const bugRemoved = createAction('bugRemoved');
export const bugResolved = createAction('bugResolved');

// Reducer
let lastId = 0;

export default createReducer([], {
  [bugAdded.type]: (bugs, action) => {
    bugs.push({
      id: ++lastId,
      description: action.payload.description,
      resolved: false,
    });
  },
  [bugResolved.type]: (bugs, action) => {
    const index = bugs.findIndex((bug) => bug.id === action.payload.id);
    bugs[index].resolved = true;
  },
  [bugRemoved.type]: (bugs, action) => {
    bugs.filter((bug) => bug.id !== action.payload.id);
  },
});
```

combine reducer & action into slice

```js
const slice = createSlice({
  name: 'bugs',
  initialState: [],
  reducers: {
    // action => action handler
    bugAdded: (bugs, action) => {
      bugs.push({
        id: ++lastId,        description: action.payload.description,
        resolved: false,
      });
    },
    bugResolved: (bugs, action) => {
      const index = bugs.findIndex((bug) => bug.id === action.payload.id);
      bugs[index].resolved = true;
    },
    bugRemoved: (bugs, action) => {
      return bugs.filter((bug) => bug.id !== action.payload.id);
    },
  },
});

export const { bugAdded, bugResolved, bugRemoved } = slice.actions;
export default slice.reducer;
```

#### using multi reducers

```js
export default combineReducers({
  bugs: bugsReducer,
  projects: projectsReducer,
  users: usersReducer,
});
```

### Middleware

extends  redux functions by providing a middle function that the action pass from before reaching reducer

```js
const logger = (store) => (next) => (action) => {
  console.log('store', store);
  console.log('next', next);
  console.log('action', action);
// required to extucte the action or sending it to next middleware
  next(action);
};
```

#### setup middleware

```js
// using reduxtoolkit
configureStore({
    reducer,
    middleware: [logger],
  });

// using standard redux
const store = createStore(
  todoApp,
  // applyMiddleware() tells createStore() how to handle middleware
  applyMiddleware(logger)
)
```

#### Redux-toolkit default middleware

```js
const middleware = [thunk,
 immutableStateInvariant,
 serializableStateInvariant]
```

`thunk`: process function actions

`immutableStateInvariant`: deeply compares state values for mutations. It can detect mutations in reducers during a dispatch, and also mutations that occur between dispatches

`serializableStateInvarian`:  deeply checks your state tree and your actions for non-serializable values

## Calling API

using middleware to call api requests

### API Middleware

```js
const api = ({ dispatch }) => (next) => async (action) => {
  if (action.type !== actions.apiCallBegan.type) return next(action);

  next(action);
  const { url, method, data, onSuccess, onError } = action.payload;

  try {
    const response = await axios.request({
      baseURL: 'http://localhost:9001/api',
      url,
      method,
      data,
    });
    dispatch(actions.apiCallSuccess(response.data));

    if (onSuccess) dispatch({ type: onSuccess, payload: response.data });
  } catch (error) {
    dispatch(actions.apiCallFailed(error));

    if (onError) dispatch({ type: onError, payload: error });
  }
};
```

### API Actions

```js
// same old action using redux toolkit
export const apiCallBegan = createAction('api/callBegan');
export const apiCallSuccess = createAction('api/callSuccess');
export const apiCallFailed = createAction('api/callFailed');
// in bugs reducer
const url = '/bugs';
export const loadBugs = () =>
  apiCallBegan({
    url,
    onSuccess: bugsReceived.type,
  });
```
