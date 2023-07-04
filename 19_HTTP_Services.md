### HTTP Services in ReactJS:
#### What is HTTP Calls in ReactJS?
* HTTP: Hyper Text Transfer Protocol
* Used to transfer text from browser to server & server to browser.

###### React
* React is a library used to built UserInterfaces. So there is no way connecting point between React and HTTP.
* It doesn't have any particular way to fetch data from server or send data to the server. It doesn't have any relation with Server.
* It doesn't know that Application contain Server.
* React Components simply Read props and states and Renders the UI.
* We have HTTP Libraries, axios,Fetch API(Default API Provided by React)

#### HTTP GetRequest in React:
##### Step 1:
* We need a API to Get Data from that API.
* jsonplaceholder.typicode.com - website

##### Step 2:
* We need Someone to send this HTTP  GetRequest call to server.
* axios Library

##### Step 3:
* Create a Component

```js
// Getrequest.js
import React from "react";
import axios from "axios";
class Getrequest extends React.Component{
    constructor(){
        super();
        this.state = {
            posts: [],
        }
    }
    getData = () => {
        axios.get("https://jsonplaceholder.typicode.com/posts")
        .then((response)=>{
            console.log(response.data)
            this.setState({posts:response.data})
        })
        .catch((error) => {
            console.log(error)
        })
    }
    render(){
        const {posts} = this.state
        return(
            <div>
                <h2>Welcome to React HTTP Get Request</h2>
                <button type="button" onClick={this.getData}>Get Data</button><br/><br/>
                List of Posts{
                    posts.map(post =>
                        <div key={post.id}>{post.title}</div>
                    )
                }
            </div>
        )
    }
}
export default Getrequest;  
```

#### HTTP Post Request in React:
```js
// Postrequest.js
import axios from "axios";
import React from "react";
class Postrequest extends React.Component{
    constructor(){
        super();
        this.state = {
            userId: "",
            title: "",
            body: "",
        }
    }
    stateHandler = (e) => {
        this.setState({[e.target.name]:[e.target.value]})
    }
    handleData = (event) => {
        event.preventDefault();
        axios.post("https://jsonplaceholder.typicode.com/posts")
        .then((response)=>{
            console.log(response)
        })
        .catch((error)=>{
            console.log(error)
        })
    }
    render(){
        const {userId, title, body} = this.state
        return(
            <div>
                <h2>Welcome to HTTP Post Request</h2>
                <form>
                    <div align="center">
                        <label>Enter UserId:</label>
                        <input type="text" name="userId" value={userId} onChange={this.stateHandler}></input>
                    </div><br/><br/>
                    <div align="center">
                        <label>Enter Title:</label>
                        <input type="text" name="title" value={title} onChange={this.stateHandler}></input>
                    </div><br/><br/><div align="center">
                        <label>Enter Body:</label>
                        <input type="text" name="body" value={body} onChange={this.stateHandler}></input>
                    </div><br/><br/>
                    <button type="button" onClick={this.handleData}>Submit</button>
                </form>
            </div>
        )
    }
}
export default Postrequest;
```

#### Http Get Calls with function Component:
```js
// Getdata.js
import React,{useEffect,useState} from "react";
import axios from "axios";

const GetData = () =>{
    const [data,setData] = useState([]);
    useEffect(()=>{
        axios.get("https://jsonplaceholder.typicode.com/posts")
        .then((response)=>{
           console.log(response)
           setData(response.data) 
        })
        .catch((error)=>{
            console.log(error)
        })
    })
    return(
        <div>
            <h1>Welcome to Http GetData with Function Component</h1>
            <h3>
                {
                   data.map(item => <li key={item.id}>{item.title}</li>)
                }
            </h3>
        </div>
    )
}
export default GetData;
```