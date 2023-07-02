### Contents:
1. Setting Dynamic Inline styles
2. Setting CSS Classes dynamically
3. Introducing Styled Components
4. Styled Components and Dynamic Props
5. Media Queries with CSS Modules
6. Debugging react apps

```js
// CourseGoalItem.js
import React from 'react';
import './CourseGoalItem.css';

const CourseGoalItem = props => {
  // const [deleteText, setDeleteText] = useState('');
  const deleteHandler = () => {
    // setDeleteText('(Deleted!)');
    props.onDelete(props.id);
  };
  return (
    <li className="goal-item" onClick={deleteHandler}>
      {props.children}                
    </li>
  );
};
export default CourseGoalItem;

// CourseGoalList.js
import React from 'react';
import CourseGoalItem from '../CourseGoalItem/CourseGoalItem';
import './CourseGoalList.css';

const CourseGoalList = props => {
  return (
    <ul className="goal-list">
      {props.items.map(goal => (
        <CourseGoalItem
          key={goal.id}
          id={goal.id}
          onDelete={props.onDeleteItem}
        >
          {goal.text}
        </CourseGoalItem>
      ))}
    </ul>
  );
};
export default CourseGoalList;

// CourseInput.js
import React, { useState } from 'react';
import Button from '../../UI/Button/Button';
import './CourseInput.css';

const CourseInput = props => {
  const [enteredValue, setEnteredValue] = useState('');
  const goalInputChangeHandler = event => {
    setEnteredValue(event.target.value);
  };
  const formSubmitHandler = event => {
    event.preventDefault();
    props.onAddGoal(enteredValue);
  };
  return (
    <form onSubmit={formSubmitHandler}>
      <div className="form-control">
        <label>Course Goal</label>
        <input type="text" onChange={goalInputChangeHandler} />
      </div>
      <Button type="submit">Add Goal</Button>
    </form>
  );
};
export default CourseInput;
```
```css
/* CourseGoalItem.css */
.goal-item {
  margin: 1rem 0;
  background: #8b005d;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  color: white;
  padding: 1rem 2rem;
  cursor: pointer;
}

/* CourseGoalList.css */
.goal-list {
  list-style: none;
  margin: 0;
  padding: 0;
}

/* CourseInput.css */
.form-control {
  margin: 0.5rem 0;
}

.form-control label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

.form-control input {
  display: block;
  width: 100%;
  border: 1px solid #ccc;
  font: inherit;
  line-height: 1.5rem;
  padding: 0 0.25rem;
}

.form-control input:focus {
  outline: none;
  background: #fad0ec;
  border-color: #8b005d;
}
```

#### 1. Setting Dynamic Inline styles :

```js
// for not adding an empty course goal
if (enteredValue.trim().length === 0) {
    return;
}
// trim() - removes excess white spaces
// CourseInput.js
```
* If we want to add an empty goal, the text should change the color to red
```js
<form onSubmit={formSubmitHandler}>
  <div className="form-control">
    <label style={{ color: !isValid ? 'red' : 'black'}}>Course Goal</label>
    <input type="text" onChange={goalInputChangeHandler} />
  </div>
  <Button type="submit">Add Goal</Button>
</form>
```
```js
// Adding some inline styles
<input 
  style = {{
    bordercolor: !isValid ? 'red' : 'black',
    backgroundcolor: !isValid ? 'salmon' : 'transparent'
  }}
  type = "text" onChange = {goalInputChangeHandler}
/>
```

```js
// CourseInput.js
import React, { useState } from 'react';

import Button from '../../UI/Button/Button';
import './CourseInput.css';

const CourseInput = props => {
  const [enteredValue, setEnteredValue] = useState('');
  const [isValid, setIsValid] = useState(true);
  const goalInputChangeHandler = event => {
    if (event.target.value.trim().length > 0){
      setIsValid(true);
    }
    setEnteredValue(event.target.value);
  };

  const formSubmitHandler = event => {
    event.preventDefault();
    if (enteredValue.trim().length === 0) {
      setIsValid(false)
      return;
    }
    props.onAddGoal(enteredValue);
  };
  return (
    <form onSubmit={formSubmitHandler}>
      <div className="form-control">
        <label style={{ color: !isValid ? 'red' : 'black'}}>Course Goal</label>
        <input 
        style={{
          bordercolor: !isValid ? 'red' : 'black',
          backgroundcolor: !isValid ? 'salmon' : 'transparent'
        }}
        type="text" onChange={goalInputChangeHandler} />
      </div>
      <Button type="submit">Add Goal</Button>
    </form>
  );
};
export default CourseInput;
```

#### Exercise - Dynamic inline Styles:
```js
import React from 'react';
export default function App() {
    const [highlighted, setHighlighted] = React.useState(false);
    function clickHandler() {
      setHighlighted(isHighlighted => !isHighlighted)
    }
    return (
      <div>
        <p style={{color: highlighted ? 'red' : 'white'}}>Style me!</p>
        <button onClick={clickHandler}>Toggle style</button>
      </div>
    );
}
```
* Here, the setHighlighted() state updating function uses a function to set the new state - this is done to follow the common best practice of using such a function if the new state is based on the previous state. Here, the new state is the opposite of the old state (!isHighlighted sets true to false and vice versa).

#### 2. Setting CSS Classes Dynamically:
```js
<div className={`form-control ${!isValid ? 'invalid' : ''}`}>
  <label style={{ color: !isValid ? 'red' : 'black'}}>Course Goal</label>
  <input 
  style={{
    borderColor: !isValid ? 'red' : 'black',
    background: !isValid ? 'salmon' : 'transparent'
  }}
  type="text" onChange={goalInputChangeHandler} />
</div>
```
```css
.form-control.invalid input{
  border-color: red;
  background: #ffd7d7;
}
.form-control.invalid label{
  color: red;
}
```

#### Exercise - Dynamic CSS Classes:
```js
import React from 'react';
export default function App() {
    const [highlighted, setHighlighted] = React.useState(false);
    function clickHandler() {
        setHighlighted(isHighlighted => !isHighlighted)
    }
    return (
        <div>
            <p className={highlighted ? 'active' : ''}>Style me!</p>
            <button onClick={clickHandler}>Toggle style</button>
        </div>
    );
}
```
```css
body {
    font-family: sans-serif;
    margin: 0;
    padding: 3rem;
    background-color: #2d2c2c;
    color: #959090;
    text-align: center;
}
.active {
    background-color: orange;
    padding: 0.5rem;
    border-radius: 4px;
    color: black;
}
```

#### 3. Introducing Styled Components:
* To install the styled components `npm install --save styled-components`
```js
const Button = styled.button``;
```
* This is called Attacked template literal
* Its a default Javascript feature, its not specific to the package and not specific to react
* Here button is simply a method on this styled object 

```js
// Button.js
import styled from 'styled-components';

const Button = styled.button`
    font: inherit;
    padding: 0.5rem 1.5rem;
    border: 1px solid #8b005d;
    color: white;
    background: #8b005d;
    box-shadow: 0 0 4px rgba(0, 0, 0, 0.26);
    cursor: pointer;

    &:focus {
        outline: none;
    }
    
    &:hover,
    &:active {
        background: #ac0e77;
        border-color: #ac0e77;
        box-shadow: 0 0 8px rgba(0, 0, 0, 0.26);
    }
`;
// This is called Attacked template literal

export default Button;
```

#### Dynamic Props:
```js
// CourseInput.js
import React, { useState } from 'react';
import Button from '../../UI/Button/Button';
import './CourseInput.css';
import styled from 'styled-components';

const FormControl = styled.div`
  margin: 0.5rem 0;

  & label {
    font-weight: bold;
    display: block;
    margin-bottom: 0.5rem;
    color: ${props => (props.invalid ? 'red' : 'black')};
  }

  & input {
    display: block;
    width: 100%;
    border: 1px solid ${props => (props.invalid ? 'red' : '#ccc')};
    background: ${props => (props.invalid ? '#ffd7d7' : 'transparent')};
    font: inherit;
    line-height: 1.5rem;
    padding: 0 0.25rem;
  }

  & input:focus {
    outline: none;
    background: #fad0ec;
    border-color: #8b005d;
  }
`;

const CourseInput = props => {
  const [enteredValue, setEnteredValue] = useState('');
  const [isValid, setIsValid] = useState(true);
  const goalInputChangeHandler = event => {
    if (event.target.value.trim().length > 0){
      setIsValid(true);
    }
    setEnteredValue(event.target.value);
  };

  const formSubmitHandler = event => {
    event.preventDefault();
    if (enteredValue.trim().length === 0) {
      setIsValid(false)
      return;
    }
    props.onAddGoal(enteredValue);
  };
  return (
    <form onSubmit={formSubmitHandler}>
      <FormControl invalid={!isValid}>
        <label>Course Goal</label>
        <input type="text" onChange={goalInputChangeHandler}/>
      </FormControl>
      <Button type="submit">Add Goal</Button>
    </form>
  );
};

export default CourseInput;
```

#### Media Queries:
```js
// Button.js
const Button = styled.button`
  width: 100%;
  ....
  @media (min-width: 768px) {
      width:auto;
  }
`;
```

#### 4. CSS Modules:
* Our react is already configured with CSS modules
* For this we need to change the name of Button.css to Button.module.css

```js
// Button.js
import React from "react";
import styles from './Button.module.css'
const Button = props => {
    return (
        <button type={props.type} className={styles.button} onClick={props.onClick}>
            {props.children}
        </button>
    )
}
export default Button;
```

#### Dynamic Styles with CSS Modules:
```js
// CourseInput.js
import React, { useState } from 'react';
import Button from '../../UI/Button/Button';
import styles from './CourseInput.module.css';

const CourseInput = props => {
  const [enteredValue, setEnteredValue] = useState('');
  const [isValid, setIsValid] = useState(true);
  const goalInputChangeHandler = event => {
    if (event.target.value.trim().length > 0){
      setIsValid(true);
    }
    setEnteredValue(event.target.value);
  };

  const formSubmitHandler = event => {
    event.preventDefault();
    if (enteredValue.trim().length === 0) {
      setIsValid(false)
      return;
    }
    props.onAddGoal(enteredValue);
  };
  return (
    <form onSubmit={formSubmitHandler}>
      <div className={`${styles['form-control']} ${!isValid && styles.invalid}`}>
        <label>Course Goal</label>
        <input type="text" onChange={goalInputChangeHandler}/>
      </div>
      <Button type="submit">Add Goal</Button>
    </form>
  );
};
export default CourseInput;
```

#### 5. Media Queries with CSS Modules:
```js
// Button.js
import React from "react";
import styles from './Button.module.css'

const Button = props => {
    return (
        <button type={props.type} className={styles.button} onClick={props.onClick}>
            {props.children}
        </button>
    )
}
export default Button;
```
```css
/* Button.module.css */
.button {
  width: 100%;
  font: inherit;
  padding: 0.5rem 1.5rem;
  border: 1px solid #8b005d;
  color: white;
  background: #8b005d;
  box-shadow: 0 0 4px rgba(0, 0, 0, 0.26);
  cursor: pointer;
}
.button:focus {
  outline: none;
}
.button:hover,
.button:active {
  background: #ac0e77;
  border-color: #ac0e77;
  box-shadow: 0 0 8px rgba(0, 0, 0, 0.26);
}
@media (min-width: 768px) {
  .button{
    width: auto;
  }
}
```

### 6. Debugging React Apps:
1. Understanding React Error Messages
2. Analyzing code flow and Warnings
3. Working with Breakpoints
4. Using the React Dev Tools