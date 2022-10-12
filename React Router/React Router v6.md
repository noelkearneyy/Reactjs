# React Router v6

## The Basics
- First you must wrap your Reactjs App in the Router of your choice. E.g.
```
import { BrowserRouter } from "react-router-dom"
<React>
  <BrowserRouter>
    <App />
  </BrowserRouter>
</React>
````

- Then in your App component you must wrap each Route in Routes tags. Each Route need to have a Path which they go to (URL), then define the component you wish to navigate.
- The Element could be any JSX you wish.
```
import { Route, Routes } from "react-router-dom";
const app = ()=>{
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/about_us" element={<AboutUs />} />
    </Routes>
  )
}
```

- To be able to use navigation buttons in React you need to use Links, which essentially replace all of the <a> tags in your component. Technically, the Link component is an anchor tag underneath but it's going to be used within React Router to automatically swap things out in your app without refreshing your entire app.
- The 'to=' attribute replaces the 'href' in an anchor tag. 
- When you click on a nav button, as described below, only the route components will change and the nav bar will still be visible on each Route.
```
import { Route, Routes } from "react-router-dom";
const app = ()=>{
  return (
 <>
 <nav>
  <ul>
    <li><Link to="/">Home</Link></li>
    <li><Link to="/about_us">About Us</Link></li>
  </ul>
 </nav>
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/about_us" element={<AboutUs />} />
    </Routes>
 </>
  )
}
```

## Router Types
1) HashRouter
- The HashRouter is similar to the the BrowserRouter, in that it still works inside your browser, however, instead of storing the URL as a normal URL it stores it inside of the hashed portion of our URL. It is not actually part of the URL, we still have out domain i.e. localhost:3000/, then everything else is stored in the hash i.e localhost:3000/#.
- Most of the time you will not need this and want to use the BrowserRouter, however, this can be useful when working on a shared server and can't change the URL of your website.
```
import { HashRouter } from "react-router-dom";
<React>
  <HashRouter>
    <App />
  </HashRouter>
</React>
```

2) HistoryRouter 
- This allows you to take control of the history element in React Router, the flow of previous pages. 
- Most of the time you will not need this and currently unstable. Some issues with the history object being duplicated. 
```
import { unstable_HistoryRouter } form "react-router-dom";
```

3) MemoryRouter 
- This is different than all the routers, in that it stores everything relating to where you have been in history inside of memory and it doesn't rely on the URL bar. The URL bar will never change. 
- It is stored inside the memory of the webpage, it is not stored anywhere else at all. 
- This is useful when you need to run tests on your code, if you want to test your React Router code or any of your code which is not in a Browser, then your code will break. 
```
import { MemoryRouter } form "react-router-dom";
```

4) StaticRouter
- This router is for specifically working on the server. This router doesn't actually allow you to change pages, it specifies a single url. If you render your components on a server in React you need to make sure all your components render to the correct page. So this Static Router allows you to tell React what page you're currently rendering. 
- If you're not doing server side rendering just pretend this doesn't exist. 
```
import { StaticRouter } from "react-router-dom/server";

<React>
  <StaticRouter location="/">
    <App />
  </StaticRouter>
</React>
```

5) Native Router 
- The only reason to use this Router is when using React Native.

## Dynamic Routes 
- Dynamic routes allow us to predefine a part of the url. Routes are intialised dynamically when the page gets rendered. With dynamic routing, we can use route changes as the conditions and render components without changing the layouts or pages completely. 
```
 <Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about_us" element={<AboutUs />} />
  <Route path="/to_do_list" element={<ToDoList />} />
  <Route path="/to_do_list/:item_id" element={<ToDoItem />} />
</Routes>
```

## Route Specificity 
- If you have two routes which both technically match, React Router will determine which one you are most likely to choose. For example, if you have a dynamic variable vs a hardcoded variable it will always go with the one that is hard coded as it is more specific. 
- As a result, you don't need to worry about the order of your routes. 
- To create a 404 page in React Router, you need a Route with a Path directed to '*'. This means that this path will match anything you type into the URL bar. 
```
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about_us" element={<AboutUs />} />
  <Route path="/to_do_list" element={<ToDoList />} />
  <Route path="/to_do_list/:item_id" element={<ToDoItem />} />
  <Route path="/to_do_list/new_item" element={<AddDoItem />} />
  <Route path="*" element={<NotFoundPage />} />
</Routes>
```

## Nested Routes
- In the previous examples, we can see path names containing some of the same format i.e. '/to_do_list'. 
- We can use nested routes to create the same outcome, without retyping the routes resulting in better formatted code. It allows us to combine multiple different routes together. 
- To define the path of the initial route, you include 'index' then the element. The 'index' will match what the parent root is. 
```
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about_us" element={<AboutUs />} />
  <Route path="/to_do_list"> 
    <Route index element={<ToDoList />} />
    <Route path=":item_id" element={<ToDoItem />} />
    <Route path="new_item" element={<AddDoItem />} />
  </Route>
  <Route path="*" element={<NotFoundPage />} />
</Routes>
```
- With nesting, you can create a Layout which is rendered on the Parent Route and will be rendered on every child route. However, the child components will not be displayed.
- To display the components of the child routes you need to create an Outlet within the Layout component of the parent route. 
```
//Routes
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about_us" element={<AboutUs />} />
  <Route path="/to_do_list" element={<ToDoListLayout />}> 
    <Route index element={<ToDoList />} />
    <Route path=":item_id" element={<ToDoItem />} />
    <Route path="new_item" element={<AddToDoItem />} />
  </Route>
  <Route path="*" element={<NotFoundPage />} />
</Routes>

//ToDoListLayout
const ToDoListLayout = () => {
  return (
  <>
  <Link to="/to_do_list/new_item" >Add Item</Link>
  <Outlet />
  </>
  )
}
```
- Furthermore, say you have the same Layout for different paths you can leave the path argument out of the parent Route and define the paths within the child routes. This is useful when you need to wrap a bunch of components which aren't necessarily related by URL inside of the same Layout.
- You can pass the Outlet components one prop, `context`, which works like a normal React context and you can define some values which can be passed down to any single component which is inside of the Layout route.
- This is useful for sharing logic and data between different componenets.
```
//ToDoListLayout
const ToDoListLayout = () => {
  return (
  <>
  <Link to="/to_do_list/new_item" >Add Item</Link>
  <Outlet context={{ hello: "world" }}/>
  </>
  )
}

//AddItemComponent
const AddToDoItem = () => {
  //This obj variable will return to us whatever we have defined in our Outlet context prop.
  const obj = useOutletContext()
  return (
  <p>{obj.hello}</p>
  //Add to do item form

)}
```
- Also, you can have multiple Routes in your app. Which can be useful when you want to show content that is different from your main URL. 
- Moreover, you can nest routes inside of other routes. If the app was large you can create specific routes in another file and place them in your main routes file. 
- When you have one route that's just rendering out other routes you need to make sure your path has a "/*" at the ened of it, because you want to make sure it will match anything that comes after it.
```
// ToDoListRoutes
const ToDoListRoutes = () => {
  return (
  <>
  <BookLayout />
  <Routes>
    <Route index element={<ToDoList />} />
    <Route path=":item_id" element={<ToDoItem />} />
    <Route path="new_item" element={<AddToDoItem />} />
  </Routes>
  </>
  )
}

//Routes 
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about_us" element={<AboutUs />} />
  <Route path="/to_do_list/*" element={<ToDoListRoutes />} /> 
  <Route path="*" element={<NotFoundPage />} />
</Routes>
```
## useRoutes Hooks 
- You do not need to define your routes in JSX, they can be defines using the `useRoutes()` hook. You give the hook an array of objects. 
```
let element = useRoutes([
{
  path: "/",
  element: <Home />,
},
{
  path: "*"
  element: <NotFoundPage />,
},
])
```

## Link Component
- The `replace` argument on Link completely removes the page that you clicked on from the history. You go to the page before that one. E.g. logging a user in and redirect them to a new page and if they clicked back you don't want to bring them back to the login page.
- The `reloadDocument` argument on Link will reload the entire page and not just the section that's changing. 
- The `state={}` argument lets you pass data from one page to another without showing up in the URL. 

## NavLink Component
- The NavLink component works exactly the same as the Link component however it lets you do additional things with the active state of a Link. 
- The code below will cause the NavLink to be red when the user has clicked on that page. 
```
<NavLink style={({isActive})=>{
  return isActive ? { color: "red" } : {}
}} to="/">
```
