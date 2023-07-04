### Form Handling in ReactJS:
* We need to Capture data from text fields.
* Displaying that captured data into UI.
* Importantly all Input Elements in form Handle "ReactJS" Only.
* Who's values are controlled by React are known as "Controlled Components".

##### Syntax:
```js
// Step 1:
<input type="text" value={this.state.name} onChange={this.handleNameChange}/>
// Step 2:
this.state={name:""}
// Step 3:
handleNameChange = (event) => {
    this.setState({name:event.target.value})
}
```

```js
// App.js
import logo from './logo.svg';
import './App.css';
import Form from './Form';
function App() {
  return (
    <div className='App'>
      <Form></Form>
    </div>
  ); 
}
export default App;
// Form.js
import React from 'react';
class Form extends React.Component{
    constructor(){
        super();
        this.state = {
            name: '',
            email: '',
            password: '',
            city: '',
            msg: ''
        }
    }
    handleNameChange = (event) => {
        this.setState({name: event.target.value})
    }
    handleEmailChange = (event) => {
        this.setState({email: event.target.value})
    }
    handlePasswordChange = (event) => {
        this.setState({password: event.target.value})
    }
    handleCityChange = (event) => {
        this.setState({city: event.target.value})
    }
    handleMsgChange = (event) => {
        this.setState({msg: event.target.value})
    }
    handleSubmitData = (event) => {
        alert(`
            Name: ${this.state.name} 
            Email: ${this.state.email}
            Password: ${this.state.password}
            City: ${this.state.city}
            Msg: ${this.state.msg}
        `)
        event.preventDefault();
    }
    render(){
        const {name, email, password, city, msg} = this.state;
        return(
            <div>
                <form onSubmit={this.handleSubmitData}>
                    <div align="center">
                        <label>Enter your name: </label>
                        <input type="text" value={name} onChange={this.handleNameChange}></input>
                    </div><br/>
                    <div align="center">
                        <label>Enter your email: </label>
                        <input type="email" value={email} onChange={this.handleEmailChange}></input>
                    </div><br/>
                    <div align="center">
                        <label>Enter your password: </label>
                        <input type="password" value={password} onChange={this.handlePasswordChange}></input>
                    </div><br/>
                    <div align="center">
                        <label>Select your city: </label>
                        <select value={city} onChange={this.handleCityChange}>
                            <option>Choose your city</option>
                            <option>Hyderabad</option>
                            <option>Vijayawada</option>
                            <option>Kakinada</option>
                            <option>Guntur</option>
                        </select>
                    </div><br/>
                    <div align="center">
                        <label>Leave a message: </label>
                        <input type="text" value={msg} onChange={this.handleMsgChange}></input>
                    </div><br/>
                    <div>
                        <button type='submit'>Submit</button>
                    </div>
                </form>
            </div>
        )
    }
}
export default Form;
```

Radio Buttons:
```js
import logo from './logo.svg';
import './App.css';
import React, {useState} from 'react';
function App() {
  const [gender, setGender] = useState();
  return (
    <div className='App'>
      <label>Select your gender: </label>
      <input type="radio" name="gender" value="Male" onChange={(e) => {setGender(e.target.value)}}/>Male
      <input type="radio" name="gender" value="Female" onChange={(e) => {setGender(e.target.value)}}/>Female
      <input type="radio" name="gender" value="Others" onChange={(e) => {setGender(e.target.value)}}/>Others <br></br>
      <h2>{gender}</h2>
    </div>
  ); 
}
export default App;
```