# What you should know about JavaScript
What you should know about JavaScript: Comprehensive JavaScript tips

## Table Of Contents
  1. [Array](#array)
    1. [Truncate an array](#truncate-an-array)
    2. [Comma in array literal decaration](#comma-in-array-literal-declaration)
  2. [Class](#class)
    1. [Robust class declaration](#robust-class-declaration)
  3. [String](#string)
  4. [Regex](#regex)
  5. [Number](#number)
  6. [Object](#object)
    1. [A clean hash table](#a-clean-hash-table)
    2. [Read-only property](#read-only-property)
  7. [Bitwise](#bitwise)
  8. [IIFE](#iife)
  
## Array
#### Truncate an array
To truncate an array from end, it's not necessary to pop up one by one from the end, but setting the `length` property will achieve it.
```javascript
/* truncate an array */
var arr = [1, 2, 3, 4, 5];
arr.length = 2;
console.log(arr); //[1, 2];
``` 
#### Comma in array literal declaration
In an array literal declaration, if there is no value or element between the last comma `,` and `]`, then the last comma will be ignored.
```javascript
/* the last comma is ignored */
var arr = [1, 2, 3, 4, ];
console.log(arr); //[1, 2, 3, 4]
```
If there is no value or element between two commas, an `undefined` will be inserted there.
```javascript
/* two adjacent commas generate an undefined value */
var arr = [1, 2, , 3];
console.log(arr); //[1, 2, undefined, 3]
```

## Class
#### Robust class declaration
There is no difference between declare a JavaScript normal function and a class function, and to reduce user misuse of a class function as a normal function Pascal naming convention is one of the solution. However, this requires the user to follow the rule and not a technical solution. What we need is a robust class declaration, with it user hardly misuse it: use or not use `new` operation on that class will both generate a correct instance of that class.

We can use `this` keyword to detect whether it is pointing to an instance of that class, and if not create a new instance and return it to user.
```javascript
/* a robust class declaration */
function Customer() {
    if (!(this instanceof Customer)) {
        return new Customer();
    }
}
```

To be more generic, `arguments.callee` can be used to replace the `class` name.
```javascript
/* a generic robust class declaration */
function Customer() {
    if (!(this instanceof arguments.callee)) {
        return new arguments.callee();
    }
}
```

The code works on parameter-less classes, but it does not work on any class with parameters because it throws away the parameters. So, we need to restore the parameters.
```javascript
function Customer(name) {
    if (!(this instanceof Customer)) {
        return new Customer(name);
    }
}
```

But if the class accepts length varying parameters, we cannot simply pass the `arguments` parameter to the internal class instantiation statement, but need handle it element by element.

## String
## Regex
## Number
## Object
#### A clean hash table
By nature, a JavaScript object is a hash table, and we can use it for most scenarios. However, it is not clean because it has some predefined keys there and if there will be conflicts if your data has the same key.
```javascript
var hashtable = {}
hashtable.hasOwnProperty; // function hasOwnProperty()
```
Besides the literal object declaration, an object could also be created using `Object` factory method.
```javascript
/* A definition of clean JavaScript hash table */
var hashtable = Object.create(null);
hashtable.hasOwnProperty; // undefined
```

#### Read-only property
A property defined using `this.some_property` or using object notation is write-able. But to define a read-only property, we can use `Object.defineProperty` method to achieve it.
```javascript
var obj = {};
Object.defineProperty(obj, 'name', {
    get: function() {
        return 'abc';
    }
});

console.log(obj.name); // 'abc'
obj.name = 123;
console.log(obj.name); // 'abc'
```
## Bitwise
## IIFE
There are various forms of Immediately-Invoked Function Expressions, and 2 mostly used froms are
```javascript
/* form 1 */
(function() {
    // code
})();

/* form 2 */
(function() {
    // code
}());
```
but if you don't care about the function return value, there are manay other forms
```javascript
/* form 3 */
!function() {
    // code
}();

/* form 4 */
~function() {
    // code
}();

/* form 5 */
void function() {
    // code
}();

/* and more ... */
```
## License
MIT
