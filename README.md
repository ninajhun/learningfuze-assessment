# ES6 - Move over Var: Let and Const are now in town 

# Overview
 - Let and Const were introduced in ES6 to avoid some common pitfalls of Var declarations. 

Var, Let, and Const vary in the following: 
1. scope
2. ability to be redeclared and updated
3. hoisting

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
    
-  Question: Why does `Uncaught ReferenceError: greeting is not defined` occur? 


### 2. var variables can be re-declared and updated within its scope 
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
console.log(greeting) // undefined
var greeting;
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
-  Question: Why does `Uncaught ReferenceError: greeting is not defined` occur? 

### 2. let can be updated but not re-declared within its scope.
Case 1 - Updated: 

    ```
    let greeting = "say Hi";
    greeting = "say Hello instead";
    ```
    
Case 2 - Redeclared: 

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

### 3. Hoisting of let
- Just like  var, let declarations are hoisted to the top. Howwver, the let keyword is not initialized. So if you try to use a let variable before declaration, you'll get a Reference Error.

```
 console.log(greeting) // Uncaught ReferenceError: greeting is not defined
 let greeting;
```



    
    
    




