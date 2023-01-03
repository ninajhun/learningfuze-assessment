# ES6 - Let and Const 
This lesson is a overview of Var, Let, and Const. The material was adapted from the following article: https://www.freecodecamp.org/news/var-let-and-const-whats-the-difference/


# Overview
Let and Const were introduced in ES6 to avoid some common pitfalls of Var declarations. Var, Let, and Const vary in scope, ability to be redeclared and updated, and hoisting. This lesson goes over these differences. 

## A Review of Var 

### What is Scope? 

- The scope is the current context of execution in which values and expressions are "visible" or can be referenced. ([MDN](https://developer.mozilla.org/en-US/docs/Glossary/Scope))
- Simply put, Scope means **where a variable can be called for use in the code.** 

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
    
-  **Question 1: Why does `Uncaught ReferenceError: greeting is not defined` occur?** 


### 2. var variables can be reassigned/updated and redeclared within its scope 
Case 1 - Reassigned:
  ```
  var text = "hey hi";
  text = "say Hello instead";
  ```
Case 2 - Redeclared: 
  ``` 
  var text = "hey hi";
  var text = "say Hello instead";
  ```

  
### 3. Hoisting of var

#### What is Hoisting? 
Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution. This means that if we do this:

```
console.log(greeting) // undefined
var greeting;
```

The var variables are hoisted to the top of their scope and initialized with a value of `undefined`.

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
   console.log(text) // "say Hi" 
   console.log(greeting) // Uncaught ReferenceError: greeting is not defined
```   
-  **Question 2: Why does `Uncaught ReferenceError: greeting is not defined` occur?**

### 2. let can be reassigned/updated but not re-declared within its scope.
Case 1 - Reassigned: 

```
let greeting = "say Hi";
greeting = "say Hello instead";
```
    
Case 2 - Redeclared: 

```
let greeting = "say Hi";
let greeting = "say Hello instead"; // error: Identifier 'greeting' has already been declared
```

Example:
```
let greeting = "say Hi";
if (true) {
    let greeting = "say Hello instead";
    console.log(greeting); // ??
}
console.log(greeting); // ?? 
```    
- **Question 3: What will be the output of these two `console.log`?**

### 3. Hoisting of let
- Just like  var, let declarations are hoisted to the top. However, the let keyword is not initialized. So if you try to use a let variable before declaration, you'll get a Reference Error.

```
 console.log(greeting) // Uncaught ReferenceError: greeting is not defined
 let greeting;
```

## Const
Variables declared with the const maintain constant values. const declarations share some similarities with let declarations.

### 1. const declarations are block scoped
Like let declarations, const declarations can only be accessed within the block they were declared.

### 2. const cannot be reassigned/updated or re-declared
This means that the value of a variable declared with const remains the same within its scope. It cannot be updated or re-declared. 

Case 1 - Reassigned: 

```
const greeting = "say Hi";
greeting = "say Hello instead";// error: Assignment to constant variable. 
```

Case 2 - Redeclared: 

```
const greeting = "say Hi";
const greeting = "say Hello instead";// error: Identifier 'greeting' has already been declared
```
    
#### *However, you CAN update the objects/arrays that are assigned to a const variable.*

**Case 1:** Updating an Object's Properties 
```
    const greeting = {
        message: "Hello World",
        times: 4
        }
```

This does NOT work:
``` 
    greeting = {
        words: "Hello",
        number: "five"
    } // error:  Assignment to constant variable.
```

This works: 
```
 greeting.message: "Hi LFZ"
```

**Case 2:** Updating an Array 
```
    const numbers = [1 , 2 , 3]
```

This does NOT work:
``` 
    numbers = [4, 5, 6]
    } // error:  Assignment to constant variable.
```

This works: 
```
 numbers.push(4)
```
- **Question 4: Why is it possible to update an property on a const variable that points to an Object or to `.push()` a new value into a const variable that points to an Array?**

### 3. Every const declaration must be initialized at the time of declaration.
```
const test // Uncaught SyntaxError: Missing initializer in const declaration
```

### 4. Hoisting of const
Just like let, const declarations are hoisted to the top but are not initialized.
 
 ```
 console.log(greeting) // Uncaught ReferenceError: greeting is not defined
 const greeting;
```
# Summary

## Table of Differences

|                                     | **Var**                                                         | **Let**                                                    | **Const**                                                  |
|-------------------------------------|-----------------------------------------------------------------|------------------------------------------------------------|------------------------------------------------------------|
| **Scope**                           | global or function scoped                                       | block scope                                                | block scoped                                               |
| **Hoisting**                        | hoisted to the top of their scope and initialized with undefined | hoisted to the top of their scope but  are not initialized | hoisted to the top of their scope but are not initialized  |
| **Redeclaration within Scope**      | Yes                                                             | No                                                         | No                                                         |
| **Reassigned(Update) within Scope** | Yes                                                             | Yes                                                        | No                                                         |

