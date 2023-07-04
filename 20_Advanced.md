### Working with Fragments, Portals & Refs:
1. JSX Limitations & Workarounds
2. Creating a Wrapper component
3. React Fragments
4. Introducing React Portals
5. Working with Portals
6. Working with 'refs'
7. Controlled Vs Uncontrolled Components



#### 1. JSX Limitations & Workarounds:
```js
return(
    <h2>Hi there!</h2>
    <p>This doesn't work :-( </p>
);
```
* If we have adjacent root level JSX elements, we'll get an error
* That means we have two JSX elements next to Java not wrapped by another JSX element, and then we return these side by side JSX elements or we try to store them in variables. We get an error.
* We cant have more than one root JSX element.

```js
// This is also not an valid Javascript
return(
    React.createElement('h2', {}, 'Hi there!')
    React.createElement('p', {}, 'This doesnot work')
)
```

```js
// Workaround
return(
    <div>
        <h2>Hi there!</h2>
        <p>This doesn't work</p>
    </div>
);
// Just wrapping the content inside a div element
```
* It doesn't have to be a `<div>`. Any element will do the trick
```js
return(
    [
        <h2>Hi there!</h2>
        <p>This doesn't work</p>
    ]
);
```
* Here we work with array element, so we get an error that `each child in a list should have a unique 'key' prop`
* We need to add different key values for the elements.
* Wrap them in a `<div>` is ok but not ideal.

#### 2. Creating a Wrapper component:
```js
const Wrapper = props => {
    return props.children;
}
export default Wrapper;
```

#### 3. React Fragments:
* Wrapper component is actually not a component we need to build on our own, instead it comes with react.
* Its the fragment component which we can access on React.Fragment, or we just import Fragment from React
```js
return(
    <React.Fragment>
        <h2>Hi there!</h2>
        <p>This doesn't work</p>
    </React.Fragment>
);
// OR
import React, {useState, Fragment} from 'react';
return(
    <Fragment>
        <h2>Hi there!</h2>
        <p>This doesn't work</p>
    </Fragment>
);
// shortcut
return(
    <>
        <h2>Hi there!</h2>
        <p>This doesn't work</p>
    </>
);
```
* These two syntaxes here render empty wrappers, which dont render any actual HTML element to the DOM.

#### 4. Introducing React Portals:
* Fragments allows us to write cleaner code, to end up with less unnecessary HTML elements.
* React portals are another useful feature, which do something similar, which allows us to write some cleaner code

```js
return(
    <React.Fragment>
        <MyModal />
        <MyInputForm />
    </React.Fragment>
)
// Real DOM
<section>
    <h2>Some other content...</h2>
    <div class="my-modal">
        <h2>A Modal Title!</h2>
    </div>
    <form>
        <label>Username</label>
        <input type="text" />
    </form>
<section>
```
* This is technically fine but it is not ideal
* This modal code which is being rendered here in the Dom will technically work as long as we apply the correct styling.
* Semantically and from a 'clean HTML structure' perspective, having this nested modal is not ideal.
* It is an overlay to the entire page after all (that's similar for side-drawers, other dialogues etc)
* Its a bit like styling a <div> like a <button> and adding an event listener to it: It will work but it's not a good practice.

```js
<div onClick={clickHandler}>Click me, I am a bad button!!</div>
```

```js
// By using portal 
return(
    <React.Fragment>
        <MyModal />
        <MyInputForm />
    </React.Fragment>
)
// Real DOM
<div class="my-modal">
    <h2>A Modal Title!</h2>
</div>
<section>
    <h2>Some other content...</h2>
    <form>
        <label>Username</label>
        <input type="text" />
    </form>
<section>
```

#### 5. Working with Portals:
* Portals need two things
    1. we need a place where we wanna port the component to, 
    2. we need to let the component know that it should have a portal to that place 

```html
<!-- In public folder -->
<!-- index.html -->
<body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="backdrop-root"></div>
    <div id="overlay-root"></div>
    <div id="root"></div>
</body>
```

#### 6. Working with refs:
* Refs are actually quite powerful, but in their most basic form they allow us to get access to other DOM elements and work with them.


### Handling Side Effects, Using Reducers & Using the Context API:
1. Introduction
2. What are "Side Effects" & Introducing useEffect
3. Using the useEffect() Hook
4. useEffect and Dependencies
5. What to add and not to add as Dependencies
6. Using the useEffect cleanup function
7. useEffect Summary
8. Introducing useReducer & reducers in general
9. using the useReducer() Hook
10. useReducer & useEffect
11. Adding Nested Properties As Dependencies To useEffect
12. useReducer vs useState for State Management
13. Introducing React Context (Context API)
14. Using the React Context API
15. Tapping Into Context with the useContext Hook
16. Making Context Dynamic
17. Building & Using a Custom Context Provider Component
18. React Context Limitations
19. Learning the "Rules of Hooks"
20. Refactoring an Input Component
21. Diving into "Forward Refs"

