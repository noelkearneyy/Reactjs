# React Bootstrap Tutorial 

  - React-Bootstrap; https://react-bootstrap.github.io/
  - Bootstrap v5; https://getbootstrap.com/

  1) Create Reactjs (CRA) - npx create-react-app <Name of App> 
  2) CD into the new app - cd <Name of App>
  3) Install Bootstrap and React-Bootstrap - npm install bootstrap react-bootstrap
  4) Include within main 'src/index.js' -
  ```
  // Bootstrap CSS
  import "bootstrap/dist/css/bootstrap.min.css";
  // Bootstrap Bundle JS
  import "bootstrap/dist/js/bootstrap.bundle.min";
  ```
  
  - You should import individual components like - import Button from 'react-bootstrap/Button'; - rather than the entire library. Reduce amount of code being sent to the client. 
  - If using Sass the simplest way is to include Bootstrap;s source Sass files in your main Sass file and then require it on your 'src/index.js' -
  ```
  /* The following line can be included in a src/App.scss */
  @import "~bootstrap/scss/bootstrap";

  /* The following line can be included in your src/index.js or App.js file */
  import './App.scss';
  ```
  
  ## `as` Prop API
  - With some React-Bootstrap components, you may want to change the component or HTML tag that is rendered. If you want to change the HTML tag but keep the styling of that component you can use the `as` prop to do so. 
  ```
  <Button as="a" variant="primary">
    Button as link
  </Button>
  ```

 ## Bootstrap Components
 ```
  import Button from 'react-bootstrap/Button';
  import { Container, Row, Col, Button, Alert, Breadcrumb, Card, Form } from 'react-bootstrap';
  import 'bootstrap/dist/css/bootstrap.min.css';
  
  //Form
  <Form>
    <Form.Group controlId='formEmail'>
      <Form.Label>E-mail Address</Form.Label> 
      <Form.Control type='email' placeholder='email@domain.com' />
      <Form.Text className='text-muted'>
        No personal data is given to third parties.
      </Form.Text>
    </Form.Group>
    
    <Form.Group controlId='formPassword'>
      <Form.Label>Password</Form.Label> 
      <Form.Control type='password' placeholder='Password' />
      <Button variant='secondary' type='submit'>Login</Button>
    </Form.Group>
  </Form>
  
  //Card
  <Card>
    <Card.Img src='IMAGE URL'>
    <Card.Body>
      <Card.Title>Card Example</Card.Title>
      <Card.Text>This is a Card example.</Card.Text>
      <Button variant='primary'>Read More</Button>
    </Card.Body>
  </Card>
  
  //Breadcrumb
  <Breadcrumb>
    <Breadcrumb.Item>Test</Breadcrumb.Item>
    <Breadcrumb.Item>Test2</Breadcrumb.Item>
    <Breadcrumb.Item active>Test3</Breadcrumb.Item>
  </Breadcrumb>
  
  //Alert
  <Alert variant='primary '>This is a button</Alert>
  
  //Button
  <Button>Test Button</Button>
  ```
## Why React-Bootstrap? 
 - Re-implementation of the Bootstrap components using React. It has no dependency on either `bootstrap.js` or jQuery. If you have React setup and React-Bootstrap installed, you have everthing you need. 
 - Method and events using jQuery is done imperatively by directly manipulating the DOM. In contrast, React uses updates to the state to update the virtual DOM. Therefore, React-Bootstrap provides a more reliable solution by incorporating Bootstrap functionality in to React's Virtual DOM.
   
### Bootstrap with State
  - Since React-Bootstrap is built with React JS, state can be passed within React-Bootstrap components as a prop. Makes it easier to mange the state as updates are made using React's state instead of directly manipulating the state of the DOM.  
 
## Server-side Rendering 
  - React-Bootstrap auto generates an `id` for some components if they're not provided. This is done for accessibility purposes. 
  - In server-side rendered applications, a `SSRProvider` must wrap the application in order to ensure the auto-genereated ids are consistent between the server and client. 
    ```
    import SSRProvider from 'react-bootstrap/SSRProvider';

    <SSRProvider>
      <App />
    </SSRProvider>
    ```
    
 ## Layout 
  ### Breakpoints
    - Breakpoints are cutomisable widths that determin how your responsive layout behaves.
  ### Grid System
    - Bootstrap's grid system uses containers, rows and columns to layout and align content.
    - It is built using flexbox and is fully responsive. Flexbox Basics - https://css-tricks.com/snippets/css/a-guide-to-flexbox/#flexbox-background
    #### Container
    
    
 
 ## Bootstrap-React Layout - https://www.youtube.com/watch?v=RaFN1KU6cDU
  

    
