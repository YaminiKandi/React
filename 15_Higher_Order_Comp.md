### Higher Order Components in ReactJS:
* It is the Advanced Technique in ReactJS for reusing a Component logic into another Component.
* By using Props we can send data from one component to another component.
* A Higher Order component transforms a component into another component.

#### Higher Order Component Implementation Process:

##### Step 1:
* A Higher Order Component is a function that takes a component and returns a new component.

```js
let Myhoc = function(ButtonComponent){
class NewComponent extends React.Component{
}
return NewComponent;
}
```
##### Step 2:
* Writing commonly used logic in Higher Order Component.
* Logic : IncrementCounter

##### Step 3:
* Binding the Higher Order Component with `NewComponent` which requires logic commonly.
`<Button IncrementCounter></Button>`

##### Step 4:
* Return `NewComponent` with added logic.
```js
return(){
    <Button></Button>
}
```

##### Example 1:
```js
// App.js
import logo from './logo.svg';
import './App.css';
import Button from './Button';
function App() {
  return (
    <div className='App'>
      <Button></Button>
    </div>
  ); 
}
export default App;

// Mycounter.js
import React from "react";

let MyCounter = function(Button){
    class NewComponent extends React.Component{
        constructor(){
            super();
            this.state = {counter: 0}
        }
        IncrementCounter = () => {
            this.setState({counter: this.state.counter + 1})
        }
        render(){
            return(
                <div>
                    <Button cnt={this.state.counter} inccnt={this.IncrementCounter}></Button>
                </div>
            )
        }
    }
    return NewComponent;
}
export default MyCounter;

// Button.js
import React from "react";
import MyCounter from "./Mycounter";

class Button extends React.Component{
    render(){
        return(
            <div>
                <h2>Welcome to Higher Order Component</h2>
                <button onClick={this.props.inccnt}>Click Me!!</button>
                <h2>{this.props.cnt}</h2>
            </div>
        )
    }
}
export default MyCounter(Button);
```

##### Example 2:
```js
//App.js
import logo from './logo.svg';
import './App.css';
import Mouseover from './Mouseover';
function App() {
  return (
    <div className='App'>
      <Mouseover></Mouseover>
    </div>
  ); 
}
export default App;

// Mycounter.js
import React from "react";

let MyCounter = function(Mouseover){
    class NewComponent extends React.Component{
        constructor(){
            super();
            this.state = {counter: 0}
        }

        IncrementCounter = () => {
            this.setState({counter: this.state.counter + 1})
        }

        render(){
            return(
                <div>
                    <Mouseover mocnt={this.state.counter} moinccnt={this.IncrementCounter}></Mouseover>
                </div>
            )
        }
    }
    return NewComponent;
}
export default MyCounter;

// Mouseover.js
import React from "react";
import MyCounter from "./Mycounter";

class Mouseover extends React.Component{
    render(){
        return(
            <div>
                <h1>Welcome to Mouseover Component</h1>
                <h1>{this.props.mocnt}</h1>
                <button onMouseOver={this.props.moinccnt}>Mouseover Me</button>
            </div>
        )
    }
}
export default MyCounter(Mouseover);
```