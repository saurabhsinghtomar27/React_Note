# React Notes
## How to Create a React App
 npm create vite@latest -> vite + React app

 npx create-create-app project_name -> React App

 # Hooks
 ## useState

Tt is used to showcase UI Updation
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
