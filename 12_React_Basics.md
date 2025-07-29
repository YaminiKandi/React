### React Project Structure:

#### node_modules:
* We can think of this folder as a repository
* The node modules folder is automatically added when we install a specific npm package
* Developers use packages when they want to add a piece of functionality that someone else coded and made available to other developers via the npm ecosystem.

#### public:
* It contains the assets that will be displayed to the user in our app.
* For example, image files for logos, the favicon, which displays an icon in the browser tab, and the robots.txt file, which is used for search engine optimization.
* Also, there is a manifest.json file, which is used to provide some metadata to a device when you're React powered web app is installed on it. 

#### index.html:
* A React app gets injected into the specific elements inside the body of the index HTML file.
* Based on changes happening inside our React app, it injects those updates in that same div of index HTML

#### src:
* This contains all the essential component files required to ensure that a React app functions. 
* Notice that there are some files and were automatically created when we use the npm command Create React app to build a starter React app. 
* As a React developer, we probably spend most of your time within this folder.
* `index.js` and `app.js` - render the root components
* `App.test.js`, `setupTests.js`, and `reportsWebVitals.js` - app's performance and testing. 
* `logo.svg` - displayed on the start page of the default app
* `.gitignore` - using version control and used to specify what files and folders must be excluded from a project.  
* `README.md` - a markdown file that gives some basic information. Developers use this when they want to share the project's code on sites like GitHub. 
* `package.json` - lists information pertaining to my app, which allows npm to run several scripts and perform various tasks in the app itself.
* `package-loc.json` - holds the list of all dependencies with a specific versions. 
* `package.json` - helps npm rebuild the app on another machine. Or if we delete the node modules folder with all the files that our project needs to run, the package-loc.json file has all the information for npm to be able to rebuild those files reliably. This file is there to ensure the npm tracks all the modules installations properly.

### Contents:
1. React
2. Components 

#### React:
* React is a javascript library for building user interfaces.
* HTML, CSS and JS are about building user interfaces as well.
* React makes building complex, interactive and reactive user interfaces simpler.
* React is all about 'Components'.
* Because all user interfaces in the end are made up of components.

#### Components:
* Components are reusable building blocks in our user interface.
* They are combination of HTML code, CSS code for styling and JS code for logic.

##### Why Components?
1. Reusability (Don't repeat ourselves)
2. Separation of Concerns (Don't do too many things in one and the same place (function))

#### How is a Component built?
* React allows us to create re-usable and reactive components consisting HTML and JavaScript (and CSS)
* React uses a declarative approach for building these components
* Define the desired target state and let React figure out the actual JavaScript DOM Instructions.
* With React, we build a component tree with one root component that's mounted into a DOM node.

```js
import './App.css';
function App() {
  const para = document.createElement('p');
  para.textContent = 'This is also Visible!';
  document.getElementById('root').append(para);
//   this is how do u in a regular javascript
  return (
    <div className="App">
      <h2>Lets get started!</h2>
      <p>This is also visible</p>
    </div>
    // this is how reacts deals with the elements
  );
}
export default App;
```
* The above is following an imperative approach.
* Because, we are giving clear step by step instructions, what javascript and browser should be doing.

---

#### JSX
Its a special, non standard syntax which is enabled in React projects

---

```js
return React.createElement(
    'div',
    {},
    React.createElement('h2',{},"Let's get started!"),
    React.createElement(Expenses, {items: expenses})
  )
// OR
return (
  <div>
    <h2>Let's get started!</h2>
    <Expenses items={expenses} />
  </div>
);
```

#### Creating ReactJS app:
* command prompt commands
```
npx create-react-app my-app
cd my-app
npm start
```

* Changing directory from C to D: `C:\>cd /d D:\`

#### Editing React App:
```js
// Original Content
import logo from './logo.svg';
import './App.css';
function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
      </header>
    </div>
  );
}
export default App;
```
```js
<div className="App">
  <header className="App-header">
    <img src={logo} className="App-logo" alt="logo" />
    <p>
      Welcome to ReactJS Sessions
    </p>
    <a
      className="App-link"
      href="https://reactjs.org"
      target="_blank"
      rel="noopener noreferrer"
    >
      Yamini Kandi
    </a>
  </header>
</div>
```

##### .gitignore & README.md:
* These files are reload to GIT integration, if we want to move our ReactJS Application to Central Repository by using GIT at that time we use these files.

##### package.json:
* One of the most important file in our project.
* Whenever we try to create application, at that time ReactJS engine downloads some libraries, to download those libraries it will create Package.json.
* In simple, if we need any library in our project that library for our application it must be placed in package.json.
* This file contains dependencies and scripts required for our project. We can see which type React version we are using.

##### package-lock.json:
* They maintain all Installed Dependencies Information.

##### node_modules:
* whenever we add any new library into our application and when we try to install that library it must be in node_modules.
* It is generated when we run "create react app".

##### public:
1. favicon.ico 
2. index.html 
3. logo192.png 
4. logo512.png 
5. manifest.json 
6. robots.txt

##### index.html:
* It is Most Important and Only html file in our entire application. We are building single page application and this is that single page.
* The view may be dynamically changed in browser but this is the file that provides VIEW.
* Maximum we dont add any code in this file, may be some changes in head section but not in body tag.
* we are not responsible to control the UI that is taken care by ReactJS. For that purpose we have one DIV Tag with `id="root"`.
* At runtime React Application take over this div tag and it ultimately Responsible for the UI.

#### src:
In this folder we place all the Heart of our Application, we place complete code in this folder.
| files | Description |
| :---: | :---------: |
| index.js | This is the Javascript entry point or Starting point for our React Application, whenever we give npm start, it starts from Here... |
| App.js | This is the App Component, represents the `View` that we have seen on Browser |
| App.test.js | This is for simple Test cases |
| App.css | This file is for Styling. The css file contain class which are applied to app component |
| index.css | we also have index.css file which apply styles for body tag |
| logo.svg | which is referred in app component |


##### Explanation:
* `Class First extends React.Component{}`
  1. Class - Keyword
  2. First - Component Name
  3. extends - Keyword
  4. React - Library
  5. Component - Library Class

* render method is used for creating a Class component
* render is not available direct reactly but is available in Component Class in react
* render is nothing but display
* render method should not be empty, it always expects to return atleast one element.
* We need to import libraries to make them work.

##### First.js:
```js
import React from "react"; // Used to create Libraries
class First extends React.Component{
    render(){
        return <h1>Welcome to React First Program</h1>
    }
}
export default First;
```

##### App.js:
```js
import logo from './logo.svg';
import './App.css';
import First from "./First";

function App() {
  return (
    <div className="App">
      <First></First>
    </div>
  );
}
export default App;
```

##### Returning Morethan One Element:
```js
import React from "react";
class First extends React.Component{
  render(){
    return(
      <div>
        <h1>Hii Welcome to ReactJS Sessions</h1>
        <h2>Hire, Train & Deploy</h2>
        <h3>Hyderabad</h3>
      </div>
    )
  }
}
export default First;
```

### What is JSX in ReactJS?
* JSX Stands for Javascript XML.
* It is a syntax Extension to Javascript.
* It is used with ReactJS to generate the User Interface.
* By using JSX, we can write the HTML code within the Javascript.

##### Syntax:
```js
const name = <h1>Yamini Kandi</h1>;
```
Javascript + HTML ----> JSX

##### Example:
```js
// Example 1
// App.js
import logo from './logo.svg';
import './App.css';
import First from './First';
function App() {
  const name = <h1>Yamini kandi</h1>
  return (
    <div className='App'>
      {name}
    </div>
  );
}
export default App;
```
```js
// Example 2
const name = <h1>{200+300}</h1>
```

* By using JSX, we can directly create HTML elements in Javascript.
* We can convert JSX elements into normal HTML elements, for this we need a compiler named 'Babel Compiler'.
* 'Babel' is a compiler which converts our code into browser understandable language.

```js
import logo from './logo.svg';
import './App.css';
import First from './First';

function App() {
  let button = <button style={{align:"center", color:"white", background:"teal"}}>Click</button>
  return (
    <div className='App'>
      {button}
    </div>
  );
}
export default App;
```

#### Is JSX Mandatory?
* It is recommended to use JSX for ReactJS Apps.
* It is not mandatory, we can use "Babel Syntax" instead of JSX.

##### JSX Syntax:
```js
let button = <button>Click</button>
```
##### Equivalent Babel Syntax:
```js
import React from "react";
let button = React.createElement("button","null","Click")
```
```js
// Example
import logo from './logo.svg';
import './App.css';
import First from './First';
import React from 'react';

function App() {
  let button = <button style={{align:"center", color:"white", background:"teal"}}>Click</button>
  let button2 = React.createElement("button","null","Click Me")
  return (
    <div className='App'>
      {button}
      {button2}
    </div>
  );
}
export default App;
```

* Visit Website `babeljs.io`, where we can write JSX code and it generates equivalent babel syntax

### Virtual DOM:
* A Javascript Object that is a "Virtual" Representation of "Real DOM"
* React will update DOM.
* By Updating DOM, it will reconstruct the entire DOM.
* By Updating Vitual DOM, it will not reconstruct the entire page rather than it update only updated parts.
* So,Finally What React Do,
  - Maintaining The Virtual DOM 
  - Update the Virtual DOM 
  - Replace it with Original DOM

#### Components in ReactJS:
* React is Developed around reusable Components.
* React have an idea of gathering small components together to make bigger components.

* React Application consists
  1. React DOM
  2. render()
  3. components
  4. Browser Output 

#### React DOM:
* By Using React DOM, we bind newly created user interface elements with Html DOM Tree.

#### React Library:
* If we want to create React Components, we need React Library

#### render():
* In React Library we have render() method, by using this method we can create the React Components.
* Simply we can say components are the Building Blocks of UI.
* Everything that is displayed on browser i.e., a component.
* Every component have a render() method.

### Component Definition:
* A Component is a Function or Class that produces HTML to show the user and handles the Events or Actions from the User.

#### coding point of view:
* Component is nothing but group of code which is a combination of both Data and it's functionality (Html, Css, Javascript) into single unit.
* They Receive some sort of Input or Attributes which we call "Props" and returns Output.

`Component = Html + Css + Javascript + Data`

* In React we have Two Types of Components 
  1. Functional Component 
  2. Class Component

#### Class Component in ReactJS:
* Class Components are ES-6 Classes or Stateful Components.
* They are more complex than Functional Components because it includes Constructors, Life-Cycle Methods, render() function and State Data Management.
* Class Components use the Props to transfer data from one component to another component.
* Class Components maintains it's own data by using State Object.
* render() which returns a React Element(JSX).

##### First.js:
```js
import React from "react";
class First extends React.Component{
  render(){
    return <h1>This is my Class Component</h1>
  }
}
export default MyComponent;
```
##### App.js:
```js
import logo from './logo.svg';
import './App.css';
import MyComponent from './MyComponent';

function App() {
  return (
    <div className="App">
       <MyComponent></MyComponent>
    </div>
  );
}
export default App;
``` 

#### Reusablity of Components:
```js
// MyComponent.js
import React from "react";
class MyComponent extends React.Component{
    render(){
        return <h1>This is my Class Component</h1>
    }
}
export default MyComponent

// MyComponent2.js
import React from "react";
import MyComponent from "./MyComponent";
class MyComponent2 extends React.Component{
    render(){
        return(
            <div>
                <MyComponent></MyComponent>
                <h1>This is my 2nd Class Component</h1>
            </div>
        )
    }
}
export default MyComponent2

// App.js
import logo from './logo.svg';
import './App.css';
import MyComponent2 from './MyComponent2';

function App() {
  return (
    <div className='App'>
      <MyComponent2></MyComponent2>
    </div>
  ); 
}
export default App;
```

#### Functional Component in ReactJS:
* Functional Components are Nothing but of Javascript Functions.
* It accepts props as an argument and returns valid JSX.
* The key that makes this component differ from a class component is the "Lack of State" and "Life Cycle Methods".

```js
// Courses.js
function Courses(){
    return(
        <h1>JavaScript, ReactJs, JQuery</h1>
    )
}
export default Courses

// App.js
import logo from './logo.svg';
import './App.css';
import Courses from './Courses';
function App() {
  return (
    <div className='App'>
      <Courses></Courses>
    </div>
  ); 
}
export default App;
```

* Functional Components are much easier to Read and Test.
* We end up with less code.
* They help us to use for Best Practices.
* The React team mentioned that they may have a performance boost for Functional Components in Future React Versions.


#### Functional Component:
* They are Just like a plain Javascript function that accepts props as an argument and returns a valid JSX.
* There is no render() in it.
* Stateless Components or Dumb.
* It doesn't have any Lifecycle Methods.

#### Class Component:
* These  requires to extend from React.Component and uses a render() in it to return a valid JSX.
* It must have render() to return a HTML Element with Logic (JSX)  
* Stateful Components or Smart.
* It has some Lifecycle Methods.

### What is ReactJS Props?
* ReactJS is Component based. We divide the Complex UI into basic components.
* React Controls the Dataflow in the Components with "props" and "state".
* Props standsfor "Properties".
* Props is an Object which "Stores" the Value of attribute of a Tag and work similar to the Html Attributes.
* Props gives a way to "Pass data from one Component to another component".
* It is similar to Function Arguments, props are passed to the component in the same way as Arguments passed in a Function.
* The Data in States and Props are used to render the component with Dynamic Data. 
* props are Basically a Kind of Global Variable or Object.
* props are Immutable.Because these are developed around the concept of pure functions, in pure functions we cannot change the data of parametres,so also we cannot change the data of a prop in ReactJS.
* In ReactJS we use props to send data to components.
* props are Arguments we can pass props to any component.  
* ReactJS props are like Function Arguments in Javascript and Attributes in HTML.

##### Syntax:
```js
// HTML Syntax
<Component name="Yamini Kandi"></Component>

// Javascript Syntax
function function_name(parameter1,parameter2,......){
  //code to be executed
}

<ComponentName propname="propvalue"></ComponentName>
// Syntax to access props
this.props.propname
```

```js
// App.js

import logo from './logo.svg';
import './App.css';
import First from './First';
function App() {
  return (
    <div className="App">
       <First name="Yamini Kandi"></First>
    </div>
  );
}
export default App;

// First.js:

import React from "react";
class First extends React.Component{
    render(){
       return(
         <div>
            <h1>Welcome to React Props</h1>
            <h1>Hello.... {this.props.name}</h1>
         </div>
       ) 
    }
}
export default First;
```

#### Default Props:
```js
// First.js
import React from "react";
class First extends React.Component{
    render(){
       return(
         <div>
            <h1>Welcome to {this.props.name}</h1>
         </div>
       ) 
    }
} 
First.defaultProps = {
   name : "Default Props",
}
export default First;

// App.js
import logo from './logo.svg';
import './App.css';
import First from './First';
function App() {
  return (
    <div className="App">
       <First></First>
    </div>
  );
}
export default App;
```

#### Passing props to Functional Component:
##### default props to a Functional Component:
```js
// Courses.js
function Courses(props){
    return <h1>{props.coursesName}</h1>
}
Courses.defaultProps = {
    coursesName : "Html, Css, Javascript",
}
export default Courses;

// App.js
import logo from './logo.svg';
import './App.css';
import Courses from './Courses';
function App() {
  return (
    <div className="App">
       <Courses></Courses>
    </div>
  );
}
export default App;
```

```js
// App.js
import logo from './logo.svg';
import './App.css';
import Courses from './Courses';
function App() {
  return (
    <div className="App">
       <Courses names="ReactJS,jQuery"></Courses>
    </div>
  );
}
export default App;

// Courses.js
function Courses(props){
    return <h1>{props.names}</h1>
}
export default Courses;
```

```js
// App.js
import logo from './logo.svg';
import './App.css';
import Courses from './Courses';
import img from './ReactLogo.png';
function App() {
  return (
    <div className='App'>
      <Courses 
        names="ReactJS, Javascript"
        image={img}
        platform="Front-end"
      >
      </Courses>
    </div>
  ); 
}
export default App;

// Courses.js
import "./styles.css"
function Courses(props){
    return(
        <div class="effects">
            <h1>{props.names}</h1>
            <img src={props.image} width="200"></img><br></br>
            <b>{props.platform}</b>
        </div>
    )
}
export default Courses
```
```css
/* styles.css */
.effects{
    width: 300px;
    height: 350px;
    padding-top: 25px;
    border: 5px solid black;
    border-radius: 10px;
    box-shadow: 5px 5px 5px teal;
    margin: 20px;
}
```

### State in ReactJS:
* The state of a component is an object that holds some data that may change dynamically over the lifetime of the component.
* The change in state over the lifetime can happen as a response to user action or system events.
* This allows component to create and manage their own data.

| props | state |
| :---: | :---: |
| Immutable | Mutable |

* When the state object changes the component Re-renders
* State of a component should change or updated throughout the life time of that component, thus it must have an initial state, So we should define the state in Constructor of a component class.

* To define a state of any class we use,

```js
class ComponentName extends React.component{
  constructor(props){
    super(props); // takes arguments
    this.state = {property: value}
  }
  render(){
    return <h1>JSX Data</h1>
  }
}
```
* The state of a component should be initialized in the constructor.
* The state component should have as many as properties as we want.

```js
// App.js
import logo from './logo.svg';
import './App.css';
import Locations from './Location';
function App() {
  return (
    <div className='App'>
      <Locations></Locations>
    </div>
  ); 
}
export default App;

// Location.js
import React from "react";
class Locations extends React.Component{
    constructor(){
        super();
        this.state = {Agra:"TajMahal", Hyderabad:"Charminar"}
        console.log(this)
    }
    render(){
        return(
            <div>
                <h1>{this.state.Agra}</h1>
                <h1>{this.state.Hyderabad}</h1>
            </div>
        )
    }
}
export default Locations
```

#### How we update Component's State?
* State should not be modified directly, but it can be modified with a special method called "setState()".
* Use setState() to change the State of a React Component.
* whenever state changes the React will Re-render the Component.

##### Syntax:
```js
this.setState({
  id : "100"
})
```

#### What happens when a state changes:
* A Change in the state happens based on user-input,triggering an event, and so on.
* React components are rendered based on the data in the state.
* State holds some initial data.
* This is one of the reason why React is fast.
* The setState() triggers the Re-rendering process for the updated parts.
* React gets informed, knows which part(s) to change and does it quickly without Re-rendering the Whole DOM.

###### Number Increment
```js
// App.js
import logo from './logo.svg';
import './App.css';
import Counter from './Counter';
function App() {
  return (
    <div className='App'>
      <Counter></Counter>
    </div>
  ); 
}
export default App;

// Counter.js
import React from "react";
class Counter extends React.Component{
    constructor(){
        super();
        this.state = {counter: 0}
    }
    // Arrow function
    doIncrement = () => {
        this.setState({counter: this.state.counter + 1})
    }
    render(){
        return(
            <div>
                <h2>{this.state.counter}</h2>
                <button type="button" onClick={this.doIncrement}>Click Me</button>
            </div>
        )
    }
}
export default Counter;
```

###### Changing Name:
```js
// App.js
import logo from './logo.svg';
import './App.css';
import Names from './Names';
function App() {
  return (
    <div className='App'>
      <Names></Names>
    </div>
  ); 
}
export default App;

// Names.js
import React from "react";
class Names extends React.Component{
    constructor(){
        super();
        this.state = {
            Names: ['David','John','Raj','Ram'],
            Index: 0
        }
    }
    changeName = () => {
        this.setState({Index: this.state.Index+1})
    }
    render(){
        return(
            <div>
                <h1>{this.state.Names[this.state.Index]}</h1>
                <button type="button" onClick={this.changeName}>Change</button>
            </div>
        )
    }
}
export default Names;
```

#### prevState in ReactJS:
* React won't delete the previous state of an object, So we can get that value.
* we cannot capture prevState value in webpage, it captures only in console.

```js
// App.js
import logo from './logo.svg';
import './App.css';
import Counter from './Counter';
function App() {
  return (
    <div className='App'>
      <Counter></Counter>
    </div>
  ); 
}
export default App;

// Counter.js
import React from "react";
class Counter extends React.Component{
    constructor(){
        super();
        this.state = {counter: 0}
    }
    // Arrow function
    doIncrement = () => {
        // callback function
        this.setState( (prevState) => {
            console.log("Previous Value: ", prevState)
            return{counter: prevState.counter+1}
        })
    }
    render(){
        console.log("Present Value: ", this.state.counter)
        return(
            <div>
                <h2>{this.state.counter}</h2>
                <button type="button" onClick={this.doIncrement}>Click Me</button>
            </div>
        )
    }
}
export default Counter;
```

### React Hooks:
1. useState()
2. useEffect()
3. useContext(), etc..

#### Object Destructuring:
```js
// App.js
import logo from './logo.svg';
import './App.css';
import Destructuring from './Destructure';
function App() {
  return (
    <div className='App'>
      <Destructuring></Destructuring>
    </div>
  ); 
}
export default App;

// Destructure.js
// general format (lengthy code)
// Object Destructuring
function Destructuring() {
    let user = {userName: "Yamini", userAge: 21};
    let userName = user.userName;
    let userAge = user.userAge;
    console.log(userName);
    console.log(userAge);
    return <h1>Welcome to object Destructuring</h1>
}
export default Destructuring;

// Object Destructuring
function Destructuring() {
    let user = {userName: "Yamini", userAge: 21, getName(){
        return "Jackie"
    }};
    let {userName, userAge, getName} = user;
    console.log(userName);
    console.log(userAge);
    console.log(getName());
    return <h1>Welcome to object Destructuring</h1>
}
export default Destructuring;

// Array Destructuring
function Destructuring() {
    let user = ["Yamini", 22, function getData(){
        return "Welcome...!!!"
    }]
    let [userName, userAge, getData] = user;
    console.log(userName);
    console.log(userAge);
    console.log(getData());
    return <h1>Welcome to Array Destructuring</h1>
}
export default Destructuring;
```

###### useState:
```js
// App.js
import logo from './logo.svg';
import './App.css';
import UpdateName from './Usestate';
function App() {
  return (
    <div className='App'>
      <UpdateName></UpdateName>
    </div>
  ); 
}
export default App;

// Usestate.js
import React, {useState} from "react";
function UpdateName(){
    let [name, setName] = useState('Jackie');
    return (
        <div>
            <h1>{name}</h1>
            <button type="button" onClick={ () => {setName('Yamini')}}>Change</button>
        </div>
    )
}
export default UpdateName;

// Increase in count
import React, {useState} from "react";
function UpdateName(){
    let [count, setCount] = useState(0);
    return (
        <div>
            <h1>{count}</h1>
            <button type="button" onClick={ () => {setCount(count+1)}}>Change</button>
        </div>
    )
}
export default UpdateName;
```
