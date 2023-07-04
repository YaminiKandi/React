### Context API in ReactJS:
* When we want to send data from top level component to lower level component.

### Context API Implementation Process:
1. Create Context API 
* By using the function "createContext" we can create Context API for our application.
```js
let Mycontext = React.createContext(defaultValue);
```

2. Create Provider 
* Data place in Context API : Providers
```js
<Mycontext.Provider  value={somevalue}>
</Mycontext.Provider>
```

3. Create consumer 
* Data Access from context API
* Now we can consume data from any component to any component by using context object
```js
<Mycontext.Consumer>  
    {
        () =>{
            return rendered data
        }
    }
</Mycontext.Consumer>
```

#### Without Context API:
* Here we need to create some components: Grandparent, Parent, Child

```js
// App.js
import logo from './logo.svg';
import './App.css';
import Grandparent from './Grandparent';
function App() {
  return (
    <div className='App'>
      <Grandparent></Grandparent>
    </div>
  ); 
}
export default App;

// Grandparent.js
import React from 'react';
import Grandpa from './Grandpa.jpg'
import './styles.css'
import Parent from './Parent';
class Grandparent extends React.Component{
    constructor(){
        super();
        this.state = {
            Building: 'Hyderabad',
        }
    }
    render(){
        return(
            <div className='Grandpa'>
                <h2>Hi.... I am Grandparent!!!</h2>
                <h3>{this.state.Building}</h3>
                <img src={Grandpa} width='150' height='150'/>
                {/* Passing prop */}
                <Parent property={this.state.Building}></Parent>
            </div>
        )
    }
}
export default Grandparent;

// Parent.js
import React from 'react';
import Child from './Child';
import parent from './Parent.jpg'
import './styles.css'

class Parent extends React.Component{
    render(){
        return(
            <div className='Parent'>
                <h2>Hi.... I am Parent!!!</h2>
                {/* Accessing prop */}
                <h3>{this.props.property}</h3>
                <img src={parent} width='150' height='150'/>
                <Child cproperty={this.props.property}></Child>
            </div>
        )
    }
}
export default Parent;

// Child.js
import React from 'react';
import './styles.css';
import Childpic from './Child.jpg'

class Child extends React.Component{
    render(){
        return(
            <div className='Child'>
                <h2>Hi.... I am Child!!!</h2>
                <h3>{this.props.cproperty}</h3>
                <img src={Childpic} width='150' height='150'/>
            </div>
        )
    }
}
export default Child;
```
```css
/* styles.css */
.Grandpa{
    border: 5px solid red;
    border-radius: 30px;
}
.Parent{
    border: 5px solid black;
    border-radius: 30px;
}
.Child{
    border: 5px solid blueviolet;
    border-radius: 30px;
}
```

#### With Context API:
* Producer - Grandparent, Consumer - Child
```js
// App.js
import logo from './logo.svg';
import './App.css';
import Grandparent from './Grandparent';
function App() {
  return (
    <div className='App'>
      <Grandparent></Grandparent>
    </div>
  ); 
}
export default App;

// Grandparent.js
import React from 'react';
import Child from './Child';
import Grandpa from './Grandpa.jpg'
import './styles.css'

export const Mycontext = React.createContext();

class Grandparent extends React.Component{
    constructor(){
        super();
        this.state = {
            Building: 'Hyderabad',
            Address: {
                Hno: 123,
                Area: 'Banugudi',
            }
        }
    }
    render(){
        return(
            <div className='Grandpa'>
                <h2>Hi.... I am Grandparent!!!</h2>
                <h2>{this.state.Address.Hno}</h2>
                <h2>{this.state.Address.Area}</h2>
                <img src={Grandpa} width='150' height='150'/>
                <Mycontext.Provider value={this.state.Address}>
                    <Child></Child>
                </Mycontext.Provider>
            </div>
        )
    }
}
export default Grandparent;

// Child.js
import React from 'react';
import './styles.css';
import Childpic from './Child.jpg'
import { Mycontext } from './Grandparent';

class Child extends React.Component{
    render(){
        return(
            <div className='Child'>
                <h2>Hi.... I am Child!!!</h2>
                <Mycontext.Consumer>
                    {
                        (data) => {
                            return(
                                <div>
                                    <h2>{data.Hno}</h2>
                                    <h2>{data.Area}</h2>
                                </div>
                            )
                        }
                    }
                </Mycontext.Consumer>
                <img src={Childpic} width='150' height='150'/>
            </div>
        )
    }
}
export default Child;
```