# What you should know about JavaScript
What you should know about JavaScript: Comprehensive JavaScript tips

## Table Of Contents
## Array
#### Truncate an array
To truncate an array from end, it's not necessary to pop one by one from the end, but setting the `length` property will achieve it.
```javascript
var arr = [1, 2, 3, 4, 5];
arr.length = 2;
console.log(arr); //[1, 2];
``` 
## License
MIT
