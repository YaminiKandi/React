##### To install react Router:
npm install react-router-dom@5.3.3

```js
// App.js
import logo from './logo.svg';
import './App.css';
import RoutingApplication from './RoutingApplication';
function App() {
  return (
    <div className='App'>
      <RoutingApplication></RoutingApplication>
    </div>
  ); 
}
export default App;

// Home.js
import React from "react";
import './styles.css'
const Home = function () {
    return(
        <div class="home">
            <h2>Welcome to Home Component</h2>
        </div>
    )
}
export default Home;

// About.js
import React from "react";

const About = function() {
    return(
        <div class="about">
            <h2>Welcome to About Component</h2>
        </div>
    )
}
export default About;

// styles.css
.home{
    background-color: teal;
    color: black;
    padding: 5px;
}
.about{
    background-color:goldenrod;
    color: black;
    padding: 5px;
}
ul{
    list-style-type: none;
    background-color: black;
    overflow: hidden;
}
li{
    float: left;
    font-size:large;
}
li a{
    display: block;
    color:white;
    padding: 15px;
    text-decoration: none;
}

// Routing Application
import React from "react";
import {BrowserRouter, Switch, Route} from 'react-router-dom';
import About from "./About";
import Home from "./Home";

function RoutingApplication() {
    return(
        <div>
            <h1>Welcome to React Routing Application</h1>
            <BrowserRouter>
                <Switch>
                    <Route path="/about">
                        <About></About>
                    </Route>
                    <Route path="/">
                        <Home></Home>
                    </Route>
                </Switch>
            </BrowserRouter>
        </div>
    )
}
export default RoutingApplication;
```

```js
// Routing Application
import React from "react";
import {BrowserRouter, Switch, Route} from 'react-router-dom';
import About from "./About";
import Home from "./Home";

function RoutingApplication() {
    return(
        <div>
            <h1>Welcome to React Routing Application</h1>
            <ul>
                <li>
                    <a href="/">Home</a>
                </li>
                <li>
                    <a href="/about">About</a>
                </li>
            </ul>
            <BrowserRouter>
                <Switch>
                    <Route path="/about">
                        <About></About>
                    </Route>
                    <Route path="/">
                        <Home></Home>
                    </Route>
                </Switch>
            </BrowserRouter>
        </div>
    )
}
export default RoutingApplication;
```
* In React we dont use Hyperlinks, as if we click the hyperlink the complete page or application reloads.

```js
// Routing Application
import React from "react";
import {BrowserRouter as Router, Switch, Route, Link} from 'react-router-dom';
import About from "./About";
import Home from "./Home";

function RoutingApplication() {
    return(
        <div>
            <h1>Welcome to React Routing Application</h1>
            <Router>
                <ul>
                    <li>
                        <Link to="/">Home</Link>
                    </li>
                    <li>
                        <Link to="/about">About</Link>
                    </li>
                </ul>
                <Switch>
                    <Route path="/about">
                        <About></About>
                    </Route>
                    <Route path="/">
                        <Home></Home>
                    </Route>
                </Switch>
            </Router>
        </div>
    )
}
export default RoutingApplication;

import React from "react";
import {BrowserRouter as Router, Switch, Route, Link} from 'react-router-dom';
import About from "./About";
import Home from "./Home";

function RoutingApplication() {
    return(
        <div>
            <h1>Welcome to React Routing Application</h1>
            <Router>
                <ul>
                    <li>
                        <Link to="/">Home</Link>
                    </li>
                    <li>
                        <Link to="/about">About</Link>
                    </li>
                </ul>
                <Switch>
                    <Route exact path="/" component={Home}></Route>
                    <Route exact path="/about" component={About}></Route>
                </Switch>
            </Router>
        </div>
    )
}
export default RoutingApplication;
```

#### Passing data through URL's:
```js
// RoutingApplication.js
import React from "react";
import {BrowserRouter as Router, Switch, Route, Link} from 'react-router-dom';
import About from "./About";
import Home from "./Home";
import Products from "./Products";
import Productdetails from "./Productdetails";
function RoutingApplication() {
    return(
        <div>
            <h1>Welcome to React Routing Application</h1>
            <Router>
                <ul>
                    <li>
                        <Link to="/">Home</Link>
                    </li>
                    <li>
                        <Link to="/about">About</Link>
                    </li>
                    <li>
                        <Link to="/products">Products</Link>
                    </li>
                </ul>
                <Switch>
                    <Route exact path="/" component={Home}></Route>
                    <Route exact path="/about" component={About}></Route>
                    <Route exact path="/products" component={Products}></Route>
                    <Route exact path="/productdetails/:pname/:price" component={Productdetails}></Route>
                </Switch>
            </Router>
        </div>
    )
}
export default RoutingApplication;

// Products.js
import React, {useState} from "react";
import { Link } from "react-router-dom";
const Products = function(){
    var [products] = useState([
        {pname:"iPhone", price:65000},
        {pname:"Samsung", price:50000},
        {pname:"Oppo", price:35000},
        {pname:"Vivo", price:25000},
        {pname:"Redmi", price:30000},
    ]);
    return(
        <div>
            <h2>Welcome to Products Component</h2>
            <ol>
                {
                    products.map((p) => {
                        return(
                            <ol>
                                <Link to={`/productdetails/${p.pname}/${p.price}`}>{p.pname}</Link>
                            </ol>
                        )
                    })
                }
            </ol>
        </div>
    )
}
export default Products;

// Productdetails.js
import React from "react";
import { useParams } from "react-router-dom";

const Productdetails = function (){
    var {pname, price} = useParams();
    return(
        <div>
            <h2>Welcome to productdetails Component</h2>
            <h3>{pname}</h3>
            <h3>{price}</h3>
        </div>
    )
}
export default Productdetails;
```