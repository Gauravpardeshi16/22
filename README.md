slip-1/10
Build a multi-page React application that includes two pages “Home” and “Profile”;
a. Create a navigation bar with links to the “Home” and “Profile” pages.
import React from 'react'

const About = () => {
  return (
    <>
     <h1>Welcome to About page</h1>
    </>
  )
}

export default About
import React from 'react'

const Home = () => {
  return (
    <>
    <h1>Welcome to Home page </h1>
    </>
  )
}

export default Home
import React from 'react';
import {Link} from 'react-router-dom'

const Nav = () => {
  return (
    <>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
  <div class="container-fluid">
    <Link class="navbar-brand" to="/">Logo</Link>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <Link class="nav-link active" aria-current="page" to="/">Home</Link>
        </li>
        <li class="nav-item">
          <Link class="nav-link active" aria-current="page" to="/about">About</Link>
        </li>
      </ul>
    </div>
  </div>
</nav>
    </>
  )
}

export default Nav




slip-2/15
Print below array elements using map into the screen.
a. const weekdays = [“Monday”, “Tuesday”, “Wednesday”, “Thursday”, “Friday”, “Saturday”, “Sunday”]
b. Create drop down list using above array.
import React from 'react'

const weekDays = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday","Saturday", "Sunday"];
const Map = () => {
  return (
    <>
    <h1>Week Days</h1>
    <ul>
        {weekDays.map((weekDays)=>(
            <li>{weekDays}</li>
        ))}
    </ul>

</>
  )
}

export default Map


slip-3
Write a program for react application, create a button that toggles between ON and OFF states when clicked.

slip-4/19
Implement useEffect hook and print all three-lifecycle state
a. E.g Inside mount
b. E.g Inside update
c. E.g Inside unmounts
d. fetch api data using “useEffect”

slip-5/6/8/11
Create a basic to do list application: (use useState() )
a. Build a component for adding, displaying, and deleting tasks.
b. Use state to manage the list of tasks.
c. Add a form for users to input new tasks.
d. Display the list of tasks and provide a button to remove them.
e. Add a counter for the total number of tasks.
import React, { useState } from 'react'

const Todo = () => {
    const [tasks, setTasks] = useState([]);
    const [task, setTask] = useState('');

    const add = () => {
        if (task.trim() !== '') {
            setTasks([...tasks, task]);
            setTask('');
        }
    };

    const del = (index) => {
        const newTasks = tasks.filter((_, x) => x !== index);
        setTasks(newTasks);
    };

    return (
        <>
            <h1>Todo List</h1>
            <input type="text" value={task} onChange={(e) => setTask(e.target.value)} placeholder="Enter a new task" />
            <button onClick={add}>Add Task</button>
            <h2>Total Tasks: {tasks.length}</h2>
            <ul>
                {tasks.map((task, index) => (
                    <li key={index}>
                        {task}
                        <button onClick={()=> del (index)}>Delete</button>
                    </li>
                ))}
            </ul>

        </>
    )
}

export default Todo



slip-7/14/16
Design login form which accepts username and password (Two text box) [12]
and submit button
a. On submit button click it should validate username and password and
console log if its valid
b. Validity check should be simple like username: Admin &amp; password:
Pass123
c. If any other credentials it should say unauthorized
d. If router name is wrong then show message is “404 Error, Page Not Found”.
import React,{useState} from 'react'

const Validation = () => {
    const [username, setUsername] = useState('');
    const [password, setPassword] = useState('');
    const [message, setMessage] = useState('');
 

    const handleSubmit = (e) => {
      e.preventDefault();
      if (username === 'Admin' && password === 'Pass123') {
        console.log('Login successful');
        setMessage('Login successful');
      } else {
        console.log('Unauthorized');
        setMessage('Unauthorized');
      }
    };
  return (
    <>
      <h1>Login</h1>
      <form onSubmit={handleSubmit}>
        <div>
          <label>Username:</label>
          <input
            type="text"
            value={username}
            onChange={(e) => setUsername(e.target.value)}
          />
        </div>
        <div>
          <label>Password:</label>
          <input
            type="password"
            value={password}
            onChange={(e) => setPassword(e.target.value)}
          />
        </div>
        <button type="submit">Submit</button>
      </form>
      {message}  
    </>
  )
}

export default Validation






slip-9
Create a simple React component called counter that displays a number and has two: buttons "Increment" and "Decrement." The number should start at 0 and change when the buttons are clicked. (using class component)
a.
Use state to manage the number.
b.
Pass the initial number as a prop to the Counter component
import React, { useState } from 'react'

const Counter = (props) => {
    const[counter,setCounter]=useState(props.num);
  return (
    <>
     <h1>{counter} </h1>
    <button onClick={()=>setCounter(counter+1)}>Inc</button>
    <button onClick={()=>setCounter(counter-1)}>Dec</button>
    </>
  )
}

export default Counter


slip-12/20/24
Write a program for react application, Create Counter button, when click on button then keep track of how many times the button was clicked using “useRef” hook.

slip-13/25
Create Redux store of counter button to display the current count and provides two buttons increment and decrement the count.
import React, { useEffect, useState } from 'react'

const Lifecycle = () => {
    const[count, setCount]=useState(0);

    useEffect(()=>{
        console.log('Mount');

        return()=>{
            console.log('Unmount')
        };
    },[]);

    useEffect(() => {
        if (count > 0) {
          console.log('Update');
        }
      }, [count]); 


  return (
    <>
       <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>  
      <button onClick={() => setCount(count - 1)}>Decrement</button>  
    </>
  )
}

export default Lifecycle

slip-17/23
Create React application for Sign-In and Sign-Out functionality using “useState” hook. When sign in Button clicked then display message is Hello, Welcome in Home Page and sign out button is clicked then display message is “Please sign in first”.

slip-18/21
  Create react application for counter button when component was rendering first 
time then automatically counting should be start. (Using “useEffect” hook)











slip-22
Print below array elements using map into the screen     
Let fruits1 = ["apple", "banana”,” guava”, “Almond”];  
Let fruits2 = ["cherry", "orange",” banana”, “Mango”, “Avocado”]; 
a. Merge both fruits array using spread operator  
b. print last two elements in array  

import React from 'react'

function Maparray() {
    const fruits = ["apple", "banana", "cherry", "bat"];
    const Fruits = fruits.filter(fruit => fruit !== "bat");


    return (
        <>
            <h1>Fruit List</h1>
            <ul>
                {Fruits.map((Fruits) => (
                    <li >{Fruits}</li>
                ))}
            </ul>

        </>
    )
}

export default Maparray
