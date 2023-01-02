# ES6 - Move over Var: Let and Const are now in town 

## 1: A Review of Var 

### What is Scope? 

- Simply put, Scope means <b> where a variable can be called for use. </b> 

### What is Var's Scope? 
- Global and function/locally scoped
- The scope is global when a var variable is declared outside a function. This means that any variable that is declared with var outside a function block is available for use in the whole window.
- var is function scoped when it is declared within a function. This means that it is available and can be accessed only within that function.

#### Example 1:  
```
    var text = "hey hi"; // text is globally scoped
    
    function newFunction() {
        var greeting = "hello"; // greeting is function scoped
    }
```

#### Example 2: 
```
var text = "hey hi"; 

function newFunction() {
    var greeting = "hello"; 
    }
    console.log(text); // "hey hi"
    console.log(greeting); // Uncaught ReferenceError: greeting is not defined
```
    
-  Question: Why does `error: hello is not defined` occur? 


### var variables can be re-declared and updated in the same scope 
Case 1: 
  ``` 
  var greeter = "hey hi";
  var greeter = "say Hello instead";
  ```
Case 2:
  ```
  var greeter = "hey hi";
  greeter = "say Hello instead";
  ```
  
### Hoisting of var

### What is Hoisting? 
Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution. This means that if we do this:

```
var greeter;
console.log(greeter); // greeter is undefined
greeter = "say hello"
```

So var variables are hoisted to the top of their scope and initialized with a value of undefined.
    
    
    




