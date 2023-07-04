### Life Cycle of a Component in ReactJS:
A React Component (Class) can go through four stages of it's life cycle as follows:
1. Initialization 
2. Mounting 
3. Updating 
4. Unmounting

#### 1. Initialization:
* This is the stage where the component is constructed with the given props and state.
* This is done in the Constructor of a component Class.
* The Constructor() method is called before anything else when the component is Initiated, and it is the natural place to setup the Initial state and other Initial values.
* The Constructor() method is called with the props as arguments, and we start by calling the super (props),before anything else

#### 2. Mounting:
* Mounting is the phase of the component lifecycle when the Initialization of the component is completed, and the component is Mounted on the DOM and Rendered for the first time in the Webpage. 

#### 3. Updating:
* Updating is the stage when the State of a Component is updated, and the component will be Rerendered.

#### 4. Unmounting:
* As the Name Suggests Unmounting is the Final Stage of a Component lifecycle where the component is Removed from the Webpage.

![plot](./my-app/src/Lifecycle.png)

* React Library provides pre-defined methods for all these stages as follows:

```js
// App.js
import logo from './logo.svg';
import './App.css';
import Lifecycle from './Lifecycle';
function App() {
  return (
    <div className='App'>
      <Lifecycle></Lifecycle>
    </div>
  ); 
}
export default App;

// Lifecycle.js
import React from "react";
class Lifecycle extends React.Component{
    constructor(){
        super();
        this.state = {counter: 0}
    }
    changeNumber = () => {
        this.setState({counter: this.state.counter + 1})
    }
    componentWillMount = () => {
        console.log('Component will mount');
    }
    componentDidMount = () => {
        console.log('Component did mount');
    }
    shouldComponentUpdate = () => {
        console.log('Should component update');
        return true
        // if return false -> component update stops
        // And there will be no change in count
    }
    componentWillUpdate = () => {
        console.log('Component will update')
    }
    componentDidUpdate = () => {
        console.log('Component did update')
    }
    render(){
        console.log('Component rendered')
        return(
            <div>
                <h1>Welcome to React Component Lifecycle Methods</h1>
                <hr/>
                <h1>{this.state.counter}</h1>
                <button type="button" onClick={this.changeNumber}>Change</button>
            </div>
        )
    }
}
export default Lifecycle
```