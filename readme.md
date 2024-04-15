# React Notes
## How to Create a React App
### vite + React
```javascript
 npm create vite@latest
 ````

###React
```javascript
 npx create-create-app project_name 
 ``` 

 # Hooks
 ## useState
It is used to showcase in UI Updation
<br>
Example

```javaScript
import { useState } from 'react';
function App() {
  const [count, setCount] = useState(0)
  const add=()=>{
    setCount(count+1)
  }
  const sub=()=>{
    if(count==0){
      alert('value cant be less than zero')
      return;
    }
    setCount(count-1)
  }

  return (
  <>
  <h1>Let increase a count</h1>
  <h2>count {count}</h2>
  <button onClick={add}>Add 1</button>
  <button onClick={sub}>substract 1</button>
  </>
  )
}

export default App
```
## InterView Question on UseState

```javaScript
import { useState } from 'react'

import './App.css'

function App() {
  const [count, setCount] = useState(0)
  const add=()=>{
    setCount(count+1)
    setCount(count+1)
    setCount(count+1)
    setCount(count+1)
    setCount(count+1)
  }
  const sub=()=>{
    if(count==0){
      alert('value cant be less than zero')
      return;
    }
    setCount(count-1)
  }

  return (
  <>
  <h1>Let increase a count</h1>
  <h2>count {count}</h2>
  <button onClick={add}>Add 1</button>
  <button onClick={sub}>substract 1</button>
  </>
  )
}

export default App
```
### Know by How much count will be Increase ?
#### Ans- I will increase by 1 only because, js will recognize it is same task make it as bunch of task as one one

## know it will increase by as it is taking prev value

```javascript
import { useState } from 'react'

import './App.css'

function App() {
  const [count, setCount] = useState(0)
  const add=()=>{
    setCount((prev)=>prev+1)
    setCount((prev)=>prev+1)
    setCount((prev)=>prev+1)
    setCount((prev)=>prev+1)
    setCount((prev)=>prev+1)
  }
  const sub=()=>{
    if(count==0){
      alert('value cant be less than zero')
      return;
    }
    setCount(count-1)
  }

  return (
  <>
  <h1>Let increase a count</h1>
  <h2>count {count}</h2>
  <button onClick={add}>Add 1</button>
  <button onClick={sub}>substract 1</button>
  </>
  )
}

export default App
```

## useCallback 
### useCallback is a React Hook that lets you cache a function definition between re-renders. <br> * optimized occur in this 

## useEffect 
### 1 .useEffect is a React Hook that lets you synchronize a component with an external system. <br> <bold>2 .It runs before rendering of our page </bold>
## Example with Password Generator
``` javascript
import { useCallback, useEffect, useState } from 'react'

import './App.css'

function App() {
  const [password,setPassword]=useState("gf")
  const [length,setlength]=useState(8)
  const [number,setNumber]=useState(false)
  const [special,setspecial]=useState(false)
  const copy=()=>{
    window.navigator.clipboard.writeText(password);
  }
  const passwordg=useCallback(()=>{
        let str="QWERTYUIOPASDFGHJKLZXCVBNM";
        if(number) str+="12345677890";
        if(special) str+="}{><?:+!@#$%^&*()_+";
        let pass=""
        for(let i=1;i<=length;i++){
          let i=Math.floor(Math.random()*str.length+1)
          pass+=str.charAt(i);
        }
        setPassword(pass)

  },[length,number,special])

  useEffect(()=>{
    passwordg()
  },[length,number,special])
  return (
    <> 
    <div>
      <input type="text" value={password} />
      <button onClick={copy}>Copy</button>
      </div> 
     <div>
     <input type="range" min="1" max="20" value={length}  onChange={(e) => {setlength(e.target.value)}} id="myRange" />
     <label htmlFor="myRange">{length}</label>
     <input type="checkbox" id="numberInput" onChange={()=>setNumber(number=>!number)}></input>
       <label htmlFor='numberInput'>Numbers</label>  
     <input type="checkbox" id="special" onChange={()=>setspecial(prev=>!prev)}></input>
       <label htmlFor='special'>Special</label>  
     </div>
    </>
  )
}

export default App

```
# React Router
[Refer this routing Documentation](https://www.w3schools.com/react/react_router.asp) <br>
It is library which we use for routing

```
npm i react-router-dom
```
### Example 
```javascript
import React from 'react'
import ReactDOM from 'react-dom/client'
import { Route, RouterProvider, createBrowserRouter, createRoutesFromElements } from 'react-router-dom'
import Home from '../Routes/Home.jsx'
import About from '../Routes/About.jsx'
import Contact from '../Routes/Contact.jsx'
import User from '../Routes/User.jsx'
const router = createBrowserRouter(
  createRoutesFromElements(
    <>
    <Route path='' element={<Home />} />
    <Route path='about' element={<About />} />
    <Route path='contact' element={<Contact />} />
    <Route path='user/:userid' element={<User />} />
    </>
     
  
  )
)
ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <RouterProvider router={router} />
  </React.StrictMode>
)
```
### User.jsx
```javascript
import React from 'react'
import {useParams} from 'react-router-dom'
function User() {
    const {userid}=useParams()
  return (
    <div>user {userid}</div>
  )
}

export default User
```
# useContext
[Refer this documentation](https://www.w3schools.com/react/react_usecontext.asp) <br>
React Context is a way to manage state globally. <br>
It can be used together with the useState Hook to share state between deeply nested components more easily than with useState alone.

## Example
``` javascript
import { useState } from 'react'
import {createContext} from 'react'
import './App.css'
import Login from './components/Login'
import Profile from './components/Profile'
export const userContext=createContext()
function App() {
  const [name, setname] = useState("saurabh")

  return (
    <>
     <userContext.Provider value={name}>
      <Login />
      <Profile />
     </userContext.Provider>
    </>
  )
}

export default App
```
### profile File
``` javascript
import React, { useContext } from 'react'
import { userContext } from '../App';
function Profile() {
   const user=useContext(userContext);
  return (
    <div>Profile {user}</div>
  )
}
export default Profile;
```
### context Api Project

# Redux
Redux and Redux-toolkit
<br>
Store-> to store data (same like that we store in context)
<br>
reducer-> A reducer is a pure function that handles state logic within Redux.
<br>
It accepts two arguments: the previous state and an action.
<br>
The reducer’s primary job is to calculate the next state based on the existing state and the dispatched action.
<br>
It then returns the updated state, facilitating changes in React view components.
<br>
useSelector-> to select some value from store
<br>
useDispatch-> to send some value in store
```javascript
npm install @reduxjs/toolkit
```
```javascript
npm install redux
```
```javascript
npm i react-redux
```
## Steps how to used Redux
## Store (Making store ) 
```javascript
import { configureStore } from "@reduxjs/toolkit";
import todoReducer from '../features/todo/todoSlice'
export const store=configureStore({
    reducer:todoReducer
})
```
## slicer is used to give functionalities to store
```javascript
import { createSlice,nanoid } from "@reduxjs/toolkit";

const initialState={
    todos:[{id:1,text:"hello World"}]
}

export const todoSlice=createSlice({
    name:'todo',
    initialState,
    reducers:{
        addTodo:(state,action)=>{
            const todo={
                id:nanoid(),
                text:action.payload
            }
            state.todos.push(todo)
        },
        removeTodo:(state,action)=>{
            state.todos=state.todos.filter((todo)=>todo.id!==action.payload)
        },
    }
})
export const {addTodo,removeTodo}=todoSlice.actions
export default todoSlice.reducer
```
## Add Provider in main js
```javascript
import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App.jsx'
import './index.css'
import { Provider } from 'react-redux'
import { store } from './app/store.js'
ReactDOM.createRoot(document.getElementById('root')).render(
 
    
    <Provider store={store}>
      <App />
    </Provider>,
)

```
## Add todo using Dispatch
```javascript
import React, { useState } from 'react'
import { useDispatch} from 'react-redux'
import {addTodo} from '../features/todo/todoSlice'
function AddTodo() {
    const [input,setInput]=useState('')
    const dispatch=useDispatch()
    const addTodoHandler=(e)=>{
        e.preventDefault()
        // alert("cd")
        dispatch(addTodo(input))
        setInput('')
    }
  return (
    <>
    <div>AddTodo</div>
    <form onSubmit={addTodoHandler}>
        <input type='text' value={input} onChange={(e)=>setInput(e.target.value)} />
       <button>Submit</button>
    </form>
    </>
    
  )
}

export default AddTodo
```
## Deleting todo using useDispatch and useSelector
```javascript
import React from 'react'
import { useSelector,useDispatch } from 'react-redux'
import {removeTodo} from '../features/todo/todoSlice'
function Todos() {
   const todos= useSelector(state=>state.todos)
   const dispatch=useDispatch()
  return (
    <>
      <div>Todos</div>
      {todos.map((todo)=>(
        <li key={todo.id}>
            {todo.text}
            <button onClick={()=>dispatch(removeTodo(todo.id))}>X</button>
        </li>
      ))}
    </>
  )
}

export default Todos
```

