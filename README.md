# What you should know about JavaScript
What you should know about JavaScript: Comprehensive JavaScript tips

## Table Of Contents
  1. [Array](#array)
  2. [Class](#class)
  3. [String](#string)
  4. [Regex](#regex)
  5. [Number](#number)
  
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
var arr = [1, 2, 3, 4, ];
console.log(arr); //[1, 2, 3, 4]
```
If there is no value or element between two commas, an `undefined` will be inserted there.
```javascript
var arr = [1, 2, , 3];
console.log(arr); //[1, 2, undefined, 3]
```
#### 
## Class
## String
## Regex
## Number
## License
MIT
