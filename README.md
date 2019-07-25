# Awesome JavaScript gotchas

A collections of some JavaScript gotchas, tips, tricks and useful stuff found around 😎

- ## var, const and let

  - Global declaration

    ```javascript
    var a = "a";
    const b = "b";
    let c = "c";

    console.log(window.a, window.b, window.c);
    //"a", undefined, undefined
    ```

  - hoisting

    ```javascript
    a = "a";
    var a;
    console.log(a);
    //"a"
    ```

    ```javascript
    a = "a";
    let a;

    //VM321:1 Uncaught ReferenceError: Cannot access 'c' before initialization
    ```

Do not use `var` anymore

- ## this

  - use strict

    ```javascript
    function myFunc() {
      console.log(this);
    }
    myFunc();

    //window
    ```

    ```javascript
    "use strict";
    function myFunc() {
      this.a = "a";
      console.log(this);
    }
    myFunc();
    //undefined
    ```

- ## Types
  - A more accurate method to detect types in JavaScript
    ```javascript
    function type(val) {
      return Object.prototype.toString.call(val).slice(8, -1);
    }
    
    type([]) // "Array"
    ```
    
 - ## Event loop
  - Microtask and macrotasks
    ```javascript
    setTimeout(() => {
    console.log('hello 1')
    }, 0);

    Promise.resolve().then(() => console.log('hello 2'))

    console.log('hello 3')
    
    //hello 3
    //hello 2
    //hello 1
    ```
