# useRef()
  - The useRef hook allows you to persist values between renders. 
  - It can be used to store a mutable value that doesn't cause a re-render when updated.
  - It can be used to access a DOM element directly. 
  ```
  const refContainer = useRef(initialValue);
  ```
  - useRef returns a mutable ref object whose `.current` property is initialised to the passed argument (initialValue).
  - The returned object will persist for the full lifetime of the component. 
  - Essentially, useRef is like a box that can hold a mutable value in its .current property. 
  - If you pass a ref object to React with `<div ref={myRef} />`, React will set its .current property to the corresponding DOM node whenever that node changes.
  - However, useRef() is useful for more than the ref attribute. It can be used to keep any mutable value around similar to how you'd use instance fields in classes.
  - useRef() creates a plain Javascript object. The only difference between useRef() and creating {current: ...} object yourself is that useRef will give you the same ref object on every render. 
  - Note that useRef doesn't notify you when its content changes. Mutating the .current property doesn't cause a re-render. If you want to run some code when React attaches or detaches a ref to a DOM node, you may want to use a callback ref instead.
  
  ## Sources
  - https://www.w3schools.com/react/react_useref.asp
  - https://reactjs.org/docs/hooks-reference.html#useref
 
