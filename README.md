# avoiding_callback_hell
Nice way to make code more easier ro read and to avoid callback hell(Christmas tree code) using Promise library 
```javascript
function asyncMethod(task){
  return new Promise(fulfill, reject){
     setTimeout(function(){ 
        console.log(task); // do some stuff in async way
        fulfill(); // with sucessfull result
     } ,1000);
  }
}
function findUser(){
  return asyncMethod('Find User');
}

function validateUser(){
  return asyncMethod('Validate User');
}

function saveToDb(){
  return asyncMethod('Save new user to db');
}
asyncMethod('Open db connection')
  .then(validateUser)
  .then(saveToDb)
  .then(findUser)
  .then(function(){}); // last callback
```
