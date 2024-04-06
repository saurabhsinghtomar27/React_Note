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

## React Router
It is library which we use for routing

```
npm i react-router-dom
```

