# ES6 - Move over Var: Let and Const are now in town 

## 1: A Review of Var 

### What is Scope? 

- Simply put, Scope means <b> where a variable can be called for use in the code. </b> 

### 1. Var is Global and function/locally scoped
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


### 2. var variables can be re-declared and updated in the same scope 
Case 1 - Redeclared: 
  ``` 
  var text = "hey hi";
  var text = "say Hello instead";
  ```
Case 2 - Updated:
  ```
  var text = "hey hi";
  text = "say Hello instead";
  ```
  
### 3. Hoisting of var

#### What is Hoisting? 
Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution. This means that if we do this:

```
var greeter;  
console.log(greeter); // greeter is undefined
greeter = "say hello"
```

So var variables are hoisted to the top of their scope and initialized with a value of `undefined`.

## Let

### 1. Let is block scoped
#### What is a block? 
A block is a chunk of code bounded by {} (and aka anything within curly braces is a block).

So a variable declared in a block with let is only available for use within that block. 

Example: 
```
   let text = "say Hi";
   let number = 4;

   if (number > 3) {
        let greeting = "say Hello instead";
        console.log(greeting);// "say Hello instead"
    }
   console.log(greeting) // Uncaught ReferenceError: greeting is not defined
```   
We see that using hello outside its block (the curly braces where it was defined) returns an error. This is because let variables are block scoped .

### 2. let can be updated but not re-declared.
Just like var,  a variable declared with let can be updated within its scope. Unlike var, a let variable cannot be re-declared within its scope. So while this will work:
    ```
    let greeting = "say Hi";
    greeting = "say Hello instead";
    ```
    
this will return an error:
    ```
    let greeting = "say Hi";
    let greeting = "say Hello instead"; // error: Identifier 'greeting' has already been declared
    ```

However, if the same variable is defined in different scopes, there will be no error:

    ```
    let greeting = "say Hi";
    if (true) {
        let greeting = "say Hello instead";
        console.log(greeting); // "say Hello instead"
    }
    console.log(greeting); // "say Hi"
    ```    
- Question: Why is ther. e no error? 

### 3. Hoisting of let
Just like  var, let declarations are hoisted to the top. Unlike var which is initialized as undefined, the let keyword is not initialized. So if you try to use a let variable before declaration, you'll get a Reference Error.

    
    
    




