```
// -------------------------------------------------------------------------------------------------
// LOCAL STORAGE FUNCTIONS 
// -------------------------------------------------------------------------------------------------

const setLocalStorage = (object) => {
  localStorage.setItem('taskObject', JSON.stringify(object));
}

const getTaskObject = () => {
  let taskObject = localStorage.getItem('taskObject');
  return JSON.parse(taskObject);
}

// -------------------------------------------------------------------------------------------------

```
