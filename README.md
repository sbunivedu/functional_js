## Principles for functional programming
1. Don't alter a variable or object - create new variables and objects and return them if need be from a function.
2. Declare function parameters - any computation inside a function depends only on the arguments passed to the function, and not on any global object or variable (declare your dependencies explicitly).

```javascript
array = [1, 2, 3, 4]
=> [ 1, 2, 3, 4 ]
array.splice(1,2)
=> [ 2, 3 ]
array
=> [ 1, 4 ]

array1 = [1,2,3];
=> [1, 2, 3]
array2 = [4, 5]
array1.concat(array2)
=> [1, 2, 3, 4, 5]
array1
=> [1, 2, 3]

[1,2,3,4].slice(0,2)
=> [1, 2]
[1,2,3,4].slice(0,3)
=> [1, 2, 3]
[1,2,3,4].slice(3)
=> [4]
[1,2,3,4].slice(2)
=> [3, 4]

var ratings = watchList.map(item=>({title:item.Title, rating:item.imdbRating}))


// The global variable
var s = [23, 65, 98, 5];

Array.prototype.myMap = function(callback) {
  var newArray = [];
  for(let i=0; i<this.length; i++){
    newArray[i] = callback(this[i]);
  }
  return newArray;
};

var new_s = s.myMap(function(item) {
  return item * 2;
});

var filteredList = watchList.map(
  item=>({title:item.Title, rating:item.imdbRating}))
  .filter(item=>item.rating >= 8.0);


// The global variable
var s = [23, 65, 98, 5];

Array.prototype.myFilter = function(callback) {
  var newArray = [];
  for(let i=0; i<this.length; i++){
    if(callback(this[i])){
      newArray.push(this[i]);
    }
  }
  return newArray;
};

var new_s = s.myFilter(function(item) {
  return item % 2 === 1;
});

const users = [
  { name: 'John', age: 34 },
  { name: 'Amy', age: 20 },
  { name: 'camperCat', age: 10 }
];

const usersObj = users.reduce((obj, user) => {
  obj[user.name] = user.age;
  return obj;
}, {});
console.log(usersObj);

const users = [
  { name: 'John', age: 34 },
  { name: 'Amy', age: 20 },
  { name: 'camperCat', age: 10 }
];

const sumOfAges = users.reduce((sum, user) =>
  sum + user.age, 0);
console.log(sumOfAges);

var numbers = [1, 5, 8, 0, 10, 11];
numbers.every(function(currentValue) {
  return currentValue < 10;
});

function checkPositive(arr) {
  // Only change code below this line

  return arr.every(value=>value>0);
  // Only change code above this line
}
checkPositive([1, 2, 3, -4, 5]);

function checkPositive(arr) {
  // Only change code below this line
  return arr.some(value=>value>0);

  // Only change code above this line
}
checkPositive([1, 2, 3, -4, 5]);
```

`Array.prototype.reduce()`, or simply `reduce()`, is the most general of all array operations in JavaScript. You can solve almost any array processing problem using the reduce method.

The reduce method allows for more general forms of array processing, and it's possible to show that both filter and map can be derived as special applications of reduce. The reduce method iterates over each item in an array and returns a single value (i.e. string, number, object, array). This is achieved via a callback function that is called on each iteration.

The callback function accepts four arguments. The first argument is known as the accumulator, which gets assigned the return value of the callback function from the previous iteration, the second is the current element being processed, the third is the index of that element and the fourth is the array upon which reduce is called.

Sources:
* https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/functional-programming
