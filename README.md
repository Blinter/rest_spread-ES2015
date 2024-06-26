# Rest / Spread Operator Exercises

## Refactor ES5 code into ES2015
```javascript
function filterOutOdds() {
  var nums = Array.prototype.slice.call(arguments);
  return nums.filter(function(num) {
    return num % 2 === 0
  });
```
## ES2015 code
```javascript
const filterOutOdds = (...a) => a.filter(v => v % 2 === 0);
```
+ filterOutOdds(0,1,2,3,4,5,6,7,8,9,10,1000,2000,2543,10246); 
    - returns `(9)[0, 2, 4, 6, 8, 10, 1000, 2000, 10246]`

## findMin
> Write a function called `findMin` that accepts a variable number of arguments and returns the smallest argument. Make sure to do this using the rest and spread operator.

+ findMin(1,4,12,-3) 
    - returns `-3`
+ findMin(1,-1) 
    - returns `-1`
+ findMin(3,1) 
    - returns `1`
```javascript
const findMin = (...a) => Math.min(...a);
```

## mergeObjects
> Write a function called `mergeObjects` that accepts two objects and returns a new object which contains all the keys and values of the first object and second object.

```javascript
const mergeObjects = (a1, a2) => ({ ...a1, ...a2 });
```
+ mergeObjects({a:1, b:2}, {c:3, d:4}) 
    - returns `{a:1, b:2, c:3, d:4}`

## doubleAndReturnArgs
> Write a function called `doubleAndReturnArgs` which accepts an array and a variable number of arguments. The function should return a new array with the original array values and all of additional arguments doubled.
```javascript
const doubleAndReturnArgs = (a, ...args) => [...a, ...args.map(v => v * 2)];
```
+ doubleAndReturnArgs(\[1,2,3],4,4) 
    - returns `[1,2,3,8,8]`
+ doubleAndReturnArgs(\[2],10,4) 
    - returns `[2, 20, 8]`
## removeRandom
> Remove a `random` element in the items array and return a new array without that item. 
```javascript
const removeRandom = items => {
    const random = Math.floor(Math.random() * items.length);
    return [...items.slice(0, random), ...items.slice(random + 1)];
}
```
+ removeRandom(\[0,1,2,3,4,5,6,7,8,9,10,1000,2000,2543,10246]); 
    - returns `(14) [0, 1, 2, 3, 4, 5, 6, 7, 9, 10, 1000, 2000, 2543, 10246]`

## extend
> Return a new array with every item in `array1` and `array2`. 
```javascript
const extend = (array1, array2) => [...array1, ...array2];
```
+ extend(\[0,1,2,3,4,5,6],\[7,8,9,10,1000,2000,2543,10246]); 
    - returns `(15) [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 1000, 2000, 2543, 10246]`

## addKeyVal
> Return a new object with all the keys and values from obj and a `new key/value pair` 
```javascript
const addKeyVal = (obj, key, val) => {
    const newObj = { ...obj };
    newObj[key] = val;
    return newObj;
};
```
or
```javascript
const addKeyVal = (obj, key, val) => ({ ...obj, [key]: val });
```
+ addKeyVal([{name: "none", job: "two"},{name: "some", job: "three"},{name: "all", job:"four"}], "title", "instructor");
    - returns `{0: {…}, 1: {…}, 2: {…}, title: 'instructor'}`

## removeKey
> Return a new object with a `key removed`. 
```javascript
const removeKey = (obj, key) => {
    delete obj[key];
    return obj;
}
```
or
```javascript
const removeKey = (obj, key) => {
    const { [key]: removedKey, ...rest} = obj;
    return rest;
}
```

+ removeKey({name: "none", job: "two"}, "job"); 
    - returns `{name: 'none'}`

## Combine 
> `Combine` two objects and return a new object.
```javascript
const combine = (obj1, obj2) => ({ ...obj1, ...obj2 });
```
+ combine({ b: 3, c: 4 }, { a: 1, b: 2 }); 
    - returns `{b: 2, c: 4, a: 1}`
+ combine({ d: 3, c: 4 }, { a: 1, b: 2 }); 
    - returns `{d: 3, c: 4, a: 1, b: 2}`
+ combine({name:"Bob", job: "no job"},{name:"Alice",job: "good job"});
    - returns `{name: 'Alice', job: 'good job'}`

+ combine({name:"Bob", job: "no job"},{othername:"Alice",otherjob: "good job"});
    - returns `{name: 'Bob', job: 'no job', othername: 'Alice', otherjob: 'good job'}`

## Update
> Return a new object with a `modified` key and value.
```javascript
const update = (obj, key, value) => {
    obj[key] = value;
    return obj;
}
```
or
```javascript
const update = (obj, key, value) => ({ ...obj, [key]: val });
```
+ update([{name: "none", job: "two"},{name: "some", job: "three"},{name: "all", job:"four"}], "title", "instructor");
    - returns: `[{…}, {…}, {…}, title: 'instructor']`