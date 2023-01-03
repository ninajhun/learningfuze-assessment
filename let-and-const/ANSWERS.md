## Answer Key to LESSON.ms Questions:
**1. Why does Uncaught ReferenceError: greeting is not defined occur?** (Var)
   -  Greeting is not in the global scope where this console.log is being called. Greeting has function scope and can only be used within the function it was initialized in. 

**2. Why does Uncaught ReferenceError: greeting is not defined occur?** (Let)
-  Greeting is not in the global scope where this console.log is being called. Greeting has block scope and can only be used within the block it was initialized in. 

**3.  What will be the output of these two console.log?**
-  “say Hello instead”, "say Hi"
 
**4. Why is it possible to update an property on a const variable that points to an Object or to `.push()` a new value into a const variable that points to an Array?**
-  When you're adding to an array or object you're not re-assigning or re-declaring the constant, it's already declared and assigned, you're just adding to the "list" that the constant points to.

.

## Solution to `exercise.js`
```
const array = ["hi", "hello", "hey", "bye"];
 for (let i = 0; i < array.length; i++) {
   const message = array[i];
    console.log(message);
 }
```
