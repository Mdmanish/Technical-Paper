# JavaScript

## Loops

### for loop

 The for statement creates a loop that consists of three optional expressions, enclosed in parentheses and separated by semicolons, followed by a statement (usually a block statement) to be executed in the loop.

 #### Syntax

 ```js
    for ([initialization]; [condition]; [final-expression])
        statement
 ```

### forEach()

The forEach() method calls a function for each element in an array.
The forEach() method is not executed for empty elements.

#### Syntax

```js
    array.forEach(function(currentValue, index, arr), thisValue)
```

#### Parameters

    function() 	Required. A function to run for each array element.

    currentValue 	Required. The value of the current element.
    
    index 	Optional. The index of the current element.
   
    arr 	Optional. The array of the current element.
    
    thisValue 	Optional. Default undefined. A value passed to the function as its this value.

#### Return Value

undefined

```js
    // Example 1
    let sum = 0;
    const numbers = [65, 44, 12, 4];
    numbers.forEach(myFunction);

    function myFunction(item) {
        sum += item;
    }

    // Example 2
    const numbers = [65, 44, 12, 4];
    numbers.forEach(myFunction)

    function myFunction(item, index, arr) {
        arr[index] = item * 10;
    } 
```

## for .. in

for in statement loops through the properties of an Object and array.

### Syntax

```js
    for (key in object) {
    // statement
    }
```

```js
// Example 1
const person = {fname:"John", lname:"Doe", age:25};

let text = "";
for (let x in person) {
  text += person[x];
}

// Example 2

const numbers = [45, 4, 9, 16, 25];

let txt = "";
for (let x in numbers) {
  txt += numbers[x];
}
```

### Important Points

    Do not use for in over an Array if the index order is important.

    The index order is implementation-dependent, and array values may not be accessed in the order you expect.

    It is better to use a for loop, a for of loop, or Array.forEach() when the order is important.


## for .. of

for of statement loops through the values of an iterable object such as Arrays, Strings, Maps, NodeLists, and more:

### Syntax

```js
for (variable of iterable) {
  // statements
}
```

```js
// Example 1
const cars = ["BMW", "Volvo", "Mini"];
for (let x of cars) {
  console.log(x);
}
// Output
// BMW Volvo Mini

// Example 2
let language = "JavaScript";
for (let x of language) {
    console.log(x);
}

// Output
// JavaScript
```

## while

The while loop loops through a block of code as long as a specified condition is true.

### Syntax

```js
while (condition) {
  // statements
}
```

```js
// Example
while (i < 10) {
  text += "The number is " + i;
  i++;
}
```

If you forget to increase the variable used in the condition, the loop will never end. This will crash your browser.

## do while

The do while loop is a variant of the while loop. This loop will execute the code block once, before checking if the condition is true, then it will repeat the loop as long as the condition is true.

###  Syntax

```js
do {
  // Statements
}
while (condition);
```

## Mutable and Immutable Methods (in strings and arrays)

### Mutable

A mutable value is one that can be changed without creating an entirely new value.

Array methods push, shift, unshift, pop, reverse, splice, sort, copyWithin, fill.

#### push

push adds an item to the end of an array.

```js
const array = ['John', 'Jeroen'];
array.push('Peter');
console.log(array);
// ['John', 'Jeroen', 'Peter']
// You can also add more arguments by separating them by a comma. E.g. array.push('Bob', 'Alice').
```

#### shift

shift removes an item at the beginning of an array.

```js
const array = ['John', 'Jeroen', 'Peter'];
array.shift();
console.log(array);
// ['Jeroen', 'Peter']
```

#### unshift

unshift adds an item to the beginning of an array

```js
const array = ['John', 'Jeroen'];
array.unshift('Peter');
console.log(array);
// ['Peter', 'John', 'Jeroen']
// You can also add more arguments by separating them by a comma. E.g. array.unshift('Bob', Alice').
```

#### pop

pop method removes an item at the end of an array

```js
const array = ['John', 'Jeroen', 'Peter'];
array.pop();
console.log(array);
// ['John', 'Jeroen']
```



### Immutable

An immutable value is one whose content cannot be changed without creating an entirely new value.

#### fill

The fill method is used to overwriting existing items in the array. It can have up to three arguments; the first argument is used for a new value, second for startIndex (optional), and third for endIndex (also optional).

```js
const array = ['John', 'Jeroen', 'Peter'];
array.fill('Bob', 1, 2);
console.log(array);
// ['John', 'Bob', 'Bob']
```

#### splice

A more advanced method is splice. This can be used to remove, change, or add items. The first argument is the startIndex, the second argument is the deleteCount, and the arguments after are the items.

```js
Adding:

const array = ['John', 'Jeroen', 'Peter'];
array.splice(3, 0, 'Bob', 'Alice');
console.log(array);
// ['John', 'Jeroen', 'Peter', 'Bob', 'Alice']

Removing:

const array = ['John', 'Jeroen', 'Peter'];
array.splice(2, 1);
console.log(array);
// ['John', 'Jeroen']

Changing:

const array = ['John', 'Jeroen', 'Peter'];
array.splice(2, 0, 'Bob');
console.log(array);
// ['Jeroen', 'Peter', 'Bob']
```

#### reverse

With reverse, we reverse the order of the array.

```js
const array = ['John', 'Jeroen', 'Peter'];
array.reverse();console.log(array);
// ['Peter', 'Jeroen', 'John']
```

#### sort

To sort our array in some different order. We need to specify two parameters because it will compare the values of the first and the second item. It can be used to sort an array in many ways.

```js
const array = ['John', 'Jeroen', 'Peter'];
array.sort((name1, name2) => name1 < name2);
console.log(array);
// ['Jeroen', 'John', 'Peter']
```

#### copyWithin

The last array method is called copyWithin. This is used to move items inside the array from one place to another. Up to three arguments are allowed. The first argument is used targetIndex, second for startIndex (optional), and third for endIndex (also optional). The example below copies index 1 till 3 and places it from index 0.

```js
const array = ['John', 'Jeroen', 'Peter'];
array.copyWithin(0, 1, 3);
console.log(array);
// ['Jeroen', 'Peter', 'Peter']
```

### Strings are immutable: Strings cannot be changed, only replaced

String Methods

String length
String slice()
String substring()
String substr()
String replace()
String replaceAll()
String toUpperCase()
String toLowerCase()
String concat()
String trim()
String trimStart()
String trimEnd()
String padStart()
String padEnd()
String charAt()
String charCodeAt()
String split()

All string methods return a new string. They don't modify the original string.

#### String Length

The length property returns the length of a string:

```js
let text = 'manish'
console.log(text.length);  // output 6
```

Extracting String Parts

There are 3 methods for extracting a part of a string:

* slice(start, end)
* substring(start, end)
* substr(start, length)

#### slice

slice() extracts a part of a string and returns the extracted part in a new string.

The method takes 2 parameters: start position, and end position (end not included).

```js
let text = "Apple, Banana, Kiwi";
console.log(text.slice(7, 13)); // output Banana
```

If you omit the second parameter, the method will slice out the rest of the string:

```js
let text = "Apple, Banana, Kiwi";
console.log(text.slice(7)); // output Banana
```

#### substring()

substring() is similar to slice().

The difference is that start and end values less than 0 are treated as 0 in substring().

#### substr()

substr() is similar to slice().

The difference is that the second parameter specifies the length of the extracted part.

```js
let text = "Apple, Banana, Kiwi";
console.log(text.slice(7, 6)); // output Banana
```

#### replace()

The replace() method replaces a specified value with another value in a string.

```js
let text = "Please visit Microsoft!";
let newText = text.replace("Microsoft", "W3Schools");
console.log(newText) // output: Please visit W3Schools!
```

The replace() method does not change the string it is called on.

The replace() method returns a new string.

By default, the replace() method is case sensitive. Writing MICROSOFT (with upper-case) will not work.

The replace() method replaces only the first match

If you want to replace all matches, use a regular expression with the /g flag set.

Regular expressions are written without quotes.

```js
let text = "Please visit Microsoft and Microsoft!";
let newText = text.replace(/Microsoft/g, "W3Schools");
console.log(newText) // output: Please visit W3Schools and W3Schools!
```

#### replaceAll()

The replaceAll() method allows you to specify a regular expression instead of a string to be replaced.

If the parameter is a regular expression, the global flag (g) must be set set, otherwise a TypeError is thrown.

```js
 text = text.replaceAll(/Cats/g,"Dogs");
```

#### Upper and Lower Case

A string is converted to upper case with toUpperCase()

A string is converted to lower case with toLowerCase()

```js
let text1 = "Hello World!";
let text2 = text1.toUpperCase();
let text3 = text1.toLowerCase();
```

#### concat()

concat() joins two or more strings.

The concat() method can be used instead of the plus operator. 

```js
let text1 = "Hello";
let text2 = "World";
let text3 = text1.concat(" ", text2);
let text4 = text1 + " " + text2;
// text3 and text4 are same
```

#### trim()

The trim() method removes whitespace from both sides of a string.

```js
let text1 = "      Hello World!      ";
console.log(text1.trim()); // output: Hello World!
```

#### trimStart() trimEnd()

The trimStart() method works like trim(), but removes whitespace only from the start of a string.

The trimEnd() method works like trim(), but removes whitespace only from the end of a string.

#### charAt()

The charAt() method returns the character at a specified index (position) in a string:

#### charCodeAt()

The charCodeAt() method returns the unicode of the character at a specified index in a string:

The method returns a UTF-16 code (an integer between 0 and 65535).

#### split()

A string can be converted to an array with the split() method.

If the separator is omitted, the returned array will contain the whole string in index [0].

If the separator is "", the returned array will be an array of single characters.

## Pass by Reference and Pass by Value

In Pass by value, parameters passed as an arguments create its own copy. So any changes made inside the function is made to the copied value not to the original value.

```js
function Passbyvalue(a, b) {
    let tmp;
    tmp = b;
    b = a;
    a = tmp;
    console.log(`Inside Pass by value function -> a = ${a} b = ${b}`);
}
 
let a = 1;
let b = 2;
console.log(`Before calling Pass by value Function -> a = ${a} b = ${b}`);
 
Passbyvalue(a, b);
 
console.log(`After calling Pass by value Function -> a =${a} b = ${b}`);

// Output:

// Before calling Pass by value Function -> a = 1 b = 2
// Inside Pass by value function -> a = 2 b = 1
// After calling Pass by value Function -> a =1 b = 2

```

In Pass by Reference, Function is called by directly passing the reference/address of the variable as an argument. So changing the value inside the function also change the original value. In JavaScript array and Object follows pass by reference property.

In Pass by reference, parameters passed as an arguments does not create its own copy, it refers to the original value so changes made inside function affect the original value.

```js
function PassbyReference(obj) {
    // Changing the reference of the object
    obj = {
        a: 10,
        b: 20,
        c: "MANISH"
    }
    console.log(`Inside Pass by Reference Function -> obj `);
         
    console.log(obj);
}
 
let obj = {
    a: 10,
    b: 20
}
console.log(`Updating the object reference -> `)
console.log(`Before calling Pass By Reference Function -> obj`);
console.log(obj);
 
PassbyReference(obj)
console.log(`After calling Pass By Reference Function -> obj`);
console.log(obj);

// Output:

// Updating the object reference -> 
// Before calling PassByReference Function -> obj
// {a: 10, b: 20}
// Inside PassbyReference Function -> obj 
// {a: 10, b: 20, c: "MANISH"}
// After calling PassByReference Function -> obj
// {a: 10, b: 20}
```

Mutating the original Object.

```js
function PassbyReference(obj) {
 
    // Mutating the original object
    obj.c = "MANISH";
    console.log(`Inside Pass by Reference Function -> obj `);
    console.log(obj);
}
 
let obj = {
    a: 10,
    b: 20
}
console.log(`Mutating the original object -> `)
console.log(`Before calling Pass By Reference Function -> obj`);
console.log(obj);
 
PassbyReference(obj)
console.log(`After calling Pass By Reference Function -> obj`);
console.log(obj);

// Output:

// Mutating the origanal object -> 
// Before calling PassByReference Function -> obj
// {a: 10, b: 20}
// Inside PassbyReference Function -> obj 
// {a: 10, b: 20, c: "MANISH"}
// After calling PassByReference Function -> obj
// {a: 10, b: 20, c: "MANISH"}
```

## Array methods

### Array.join

The join() method returns an array as a string.

The join() method does not change the original array. So this is immutable.

Any separator can be specified. The default is comma (,).

#### Syntax

```js
array.join(separator) // seperator is optional.
```

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];
let text = fruits.join();
console.log(text) // output: Banana,Orange,Apple,Mango
text = fruits.join(" and ");
console.log(text) // output: Banana and Orange and Apple and Mango
```

### Array.flat

It is used to flatten an array, to reduce the nesting of an array.

#### Syntax

```js
arr.flat([depth])

// depth: It specifies, how deep the nested array should be flattened. The default value is 1 if no depth value is passed as it is an optional parameter.

// Return value: It returns an array i.e. depth levels flat than the original array, it removes nesting according to the depth levels.
```

```js
    // Creating multilevel array
    const numbers = [['1', '2'], ['3', '4',['5',['6'], '7']]];
    const flatNumbers= numbers.flat(Infinity);
    console.log(flatNumbers);

    // Output: 1,2,3,4,5,6,7
```

```js
let nestedArray = [1, [2, 3], [[]],[4, [5]], 6];
let zeroFlat = nestedArray.flat(0);

console.log(
`Zero levels flattened array: ${zeroFlat}`);
// 1 is the default value even
// if no parameters are passed
let oneFlat = nestedArray.flat(1);
console.log(
`One level flattened array: ${oneFlat}`);
 
let twoFlat = nestedArray.flat(2);

console.log(
`Two level flattened array: ${twoFlat}`);
 
// No effect when depth is 3 or
// more since array is already
// flattened completely.
let threeFlat = nestedArray.flat(3);
console.log(
`Three levels flattened array: ${threeFlat}`);

// Output:

// Zero levels flattened array: [1, [2, 3], [[]], [4, [5]], 6]
// One level flattened array: [1, 2, 3, [], 4, [5], 6]
// Two levels flattened array: [1, 2, 3, 4, 5, 6]
// Three levels flattened array: [1, 2, 3, 4, 5, 6]
```

We can also remove empty slots or empty values in an array by using the flat() method.

```js
let arr = [1, 2, 3, , 4];
let newArr = arr.flat();
console.log(newArr);
```

### Array.find

The find() method returns the value of the first element that passes a test.

The find() method executes a function for each array element.

The find() method returns undefined if no elements are found.

The find() method does not execute the function for empty elements.

The find() method does not change the original array.

#### Syntax

```js
array.find(function(currentValue, index, arr),thisValue)

// function() Required. A function to run for each array element.
// currentValue Required. The value of the current element.
// index Optional. The index of the current element.
// arr Optional. The array of the current element.
// thisValue Optional. Default undefined. A value passed to the function as its this value.
```

#### Return value

The value of the first element that pass the test.
Otherwise it returns undefined.

```js
// Example
const ages = [3, 10, 25, 18, 20];

function checkAge(age) {
  return age > 18;
}
console.log(ages.find(checkAge));

// Output: 25
```

### Array.indexOf

The indexOf() method returns the first index (position) of a specified value.

The indexOf() method returns -1 if the value is not found.

The indexOf() method starts at a specified index and searches from left to right.

By default the search starts at the first element and ends at the last.

Negative start values counts from the last element (but still searches from left to right).

#### Syntax

```js
array.indexOf(item, start)

// item Required. The value to search for.
// start Optional. Where to start the search. Default value is 0. Negative values start the search from the end of the array.
```

#### Return value

The index (position) of the first item found. -1 if the item is not found.

### Array.includes

The includes() method returns true if an array contains a specified value.

The includes() method returns false if the value is not found.

The includes() method is case sensitive.

#### Syntax

```js
array.includes(element, start)

// element Required. The value to search for.
// start Optional. Start position. Default is 0.
```

#### Return Value

true if the value is found, otherwise false.

### Array.findIndex

The findIndex() method executes a function for each array element.

The findIndex() method returns the index (position) of the first element that passes a test.

The findIndex() method returns -1 if no match is found.

The findIndex() method does not execute the function for empty array elements.

The findIndex() method does not change the original array.

#### Syntax

```js
array.findIndex(function(currentValue, index, arr), thisValue)

// function() Required. A function to be run for each array element.
// currentValue Required. The value of the current element.
// index Optional. The index of the current element.
// arr Optional. The array of the current element.
// thisValue Optional. Default undefined. A value passed to the function as its this value.
```

#### Return Value

The index of the first element that passes the test.
Otherwise -1.

```js
const ages = [3, 10, 19, 25 18, 20];
ages.findIndex(checkAge);
function checkAge(age) {
    return age > 18;
}
// Output: 2
```

### Array.filter

The filter() method creates a new array filled with elements that pass a test provided by a function.

The filter() method does not execute the function for empty elements.

The filter() method does not change the original array.

#### Syntax

```js
array.filter(function(currentValue, index, arr), thisValue)

// function() Required. A function to run for each array element.
// currentValue Required. The value of the current element.
// index Optional. The index of the current element.
// arr Optional. The array of the current element.
// thisValue Optional. Default undefined. A value passed to the function as its this value.
```

#### Return Value

Containing the elements that pass the test. If no elements pass the test it returns an empty array.

```js
const ages = [32, 33, 16, 40];
const result = ages.filter(checkAdult);

function checkAdult(age) {
  return age >= 18;
}
// Output: 32,33,40
```

### Array.map

map() creates a new array from calling a function for every array element.

map() calls a function once for each element in an array.

map() does not execute the function for empty elements.

map() does not change the original array.

#### Syntax

```js
 array.map(function(currentValue, index, arr), thisValue)

// function() Required. A function to be run for each array element.
// currentValue Required. The value of the current element.
// index Optional. The index of the current element.
// arr Optional. The array of the current element.
// thisValue Optional. Default value undefined. A value passed to the function to be used as its this value.
```

#### Return Value

An array: The results of a function for each array element.

```js
const numbers = [4, 9, 16, 25];
const newArr = numbers.map(Math.sqrt)

// Output: 2,3,4,5
```

### Array.reduce

The reduce() method executes a reducer function for array element.

The reduce() method returns a single value: the function's accumulated result.

The reduce() method does not execute the function for empty array elements.

The reduce() method does not change the original array.

#### Syntax

```js
array.reduce(function(total, currentValue, currentIndex, arr), initialValue)

// function() Required. A function to be run for each element in the array.
// initialValue Optional. A value to be passed to the function as the initial value.

// Reducer function parameters:

// total Required. The initialValue, or the previously returned value of the function.
// currentValue Required. The value of the current element.
// currentIndex Optional. The index of the current element.
// arr Optional. The array the current element belongs to.
```

#### Return Value

The accumulated result from the last call of the callback function.

```js
let arr = [1,2,3,4,5]
let ans = arr.reduce((sum, curr) =>{
    return sum += curr;
});
console.log(ans); // Output: 15
```

### Array.sort

The sort() method sorts an array alphabetically: 

By default, the sort() function sorts values as strings.

This works well for strings ("Manish" comes before "Rahman").

However, if numbers are sorted as strings, "25" is bigger than "100", because "2" is bigger than "1".

Because of this, the sort() method will produce incorrect result when sorting numbers.

It can be fix this by providing a compare function.

```js
// Ascending
const points = [40, 100, 1, 5, 25, 10];
points.sort(function(a, b){return a - b});
// Output order: 1,5,10,25,40,100

// Descending
points.sort(function(a, b){return a - b});
// Output order: 100,40,25,10,5,1
```

#### Compare Function

The purpose of the compare function is to define an alternative sort order.

The compare function should return a negative, zero, or positive value, depending on the arguments:
function(a, b){return a - b}

When the sort() function compares two values, it sends the values to the compare function, and sorts the values according to the returned (negative, zero, positive) value.

If the result is negative, a is sorted before b.

If the result is positive, b is sorted before a.

If the result is 0, no changes are done with the sort order of the two values.

Example:

The compare function compares all the values in the array, two values at a time (a, b).

When comparing 40 and 100, the sort() method calls the compare function(40, 100).

The function calculates 40 - 100 (a - b), and since the result is negative (-60),  the sort function will sort 40 as a value lower than 100.

## Array methods chaining

Following methods are used for chaining.

* Filter method ( filter())
* Map method ( map())
* Reduce method ( reduce())
* Find method ( find())
* Sort method ( sort())

These all methods takes array and returns array, so we can combine all methods or more than one methods to determine final result. Combining more than two methods are called chaining.

```js
// Example

const products = [
    { name: 'dress', price: 600 },
    { name: 'cream', price: 60 },
    { name: 'book', price: 200 },
    { name: 'bottle', price: 50 },
    { name: 'bedsheet', price: 350 }
];

// Writing the different array methods
// on different lines increases the
// readability
sale = products.filter(product => product.price > 100).map(product => `the ${product.name} is ${product.price / 2} rupees`);
console.log(sale);
```

## String methods - add codeblocks and mention mutable/immutable

All string methods are immutable.

String Methods

String length
String slice()
String substring()
String substr()
String replace()
String replaceAll()
String toUpperCase()
String toLowerCase()
String concat()
String trim()
String trimStart()
String trimEnd()
String padStart()
String padEnd()
String charAt()
String charCodeAt()
String split()

## Object methods and operations - add codeblocks and mention mutable/immutable

### this

In JavaScript, the this keyword refers to an object.

Which object depends on how this is being invoked (used or called).

this is not a variable. It is a keyword. You cannot change the value of this.

The this keyword refers to different objects depending on how it is used:

In an object method, this refers to the object.

Alone, this refers to the global object.

In a function, this refers to the global object.

In a function, in strict mode, this is undefined.

In an event, this refers to the element that received the event.

Methods like call(), apply(), and bind() can refer this to any object.

### important built-in object methods

#### Object.keys()

The Object.keys() method returns an array of a given object's own enumerable string-keyed property names.

```js
const object1 = {
  a: 'somestring',
  b: 42,
  c: false
};
console.log(Object.keys(object1));

Output: ["a", "b", "c"]
```

#### Object.values()

The Object.values() method returns an array of a given object's own enumerable string-keyed property values.

```js
const object1 = {
  a: 'somestring',
  b: 42,
  c: false
};
console.log(Object.values(object1));

Output: ["somestring", 42, false]

```

#### Object.hasOwn()

The Object.hasOwn() static method returns true if the specified object has the indicated property as its own property. If the property is inherited, or does not exist, the method returns false.

```js
const object1 = {
  prop: 'exists'
};
console.log(Object.hasOwn(object1, 'prop'));
console.log(Object.hasOwn(object1, 'toString'));

Output: true false
```

#### Object.entries()

The Object.entries() method returns an array of a given object's own enumerable string-keyed property key-value pairs.

```js
const object1 = {
  a: 'somestring',
  b: 42
};
console.log(Object.entries(object1));

Output: [['a', 'somestring'], ['b', 42]]

```

## Hoisting

Hoisting in JavaScript is a behavior in which a function or a variable can be used before declaration.

Hoisting is JavaScript's default behavior of moving all declarations to the top of the current scope (to the top of the current script or the current function).

Variables defined with let and const are hoisted to the top of the block, but not initialized.

Meaning: The block of code is aware of the variable, but it cannot be used until it has been declared.

Using a let variable before it is declared will result in a ReferenceError.

The variable is in a "temporal dead zone" from the start of the block until it is declared:

## Scopes

A scope defines what variables you have access to. There are three kinds of scope – global scope, function scope and block scope.

### Block Scope

let and const these two keywords provide Block Scope in JavaScript.

Variables declared inside a { } block cannot be accessed from outside the block.

```js
{
  let x = 2;
}
// x can NOT be used here 
```

Variables declared with the var keyword can NOT have block scope.

Variables declared inside a { } block can be accessed from outside the block.

#### Local Scope

Variables declared within a JavaScript function, become LOCAL to the function.

Local variables have Function Scope.

They can only be accessed from within the function.

```js
// code here can NOT use carName

function myFunction() {
  let carName = "Volvo";
  // code here CAN use carName
}

// code here can NOT use carName 
```

Since local variables are only recognized inside their functions, variables with the same name can be used in different functions.

Local variables are created when a function starts, and deleted when the function is completed.

Function arguments (parameters) work as local variables inside functions.

### Function Scope

JavaScript has function scope: Each function creates a new scope.

Variables defined inside a function are not accessible (visible) from outside the function.

Variables declared with var, let and const are quite similar when declared inside a function.

They all have Function Scope:

### Global Variables

A variable declared outside a function, becomes GLOBAL.

A global variable has Global Scope.

```js
let carName = "Volvo";
// code here can use carName

function myFunction() {
// code here can also use carName
}
```

#### Global Scope

Variables declared Globally (outside any function) have Global Scope.

Global variables can be accessed from anywhere in a JavaScript program.

Variables declared with var, let and const are quite similar when declared outside a block.

#### Automatically Global

If you assign a value to a variable that has not been declared, it will automatically become a GLOBAL variable.

This code example will declare a global variable carName, even if the value is assigned inside a function.

```js
myFunction();

// code here can use carName

function myFunction() {
  carName = "Volvo";
} 
```

In "Strict Mode", undeclared variables are not automatically global.


#### The Lifetime of JavaScript Variables

The lifetime of a JavaScript variable starts when it is declared.

Function (local) variables are deleted when the function is completed.

In a web browser, global variables are deleted when you close the browser window (or tab).

## Closures

Closure means that an inner function always has access to the vars and parameters of its outer function, even after the outer function has returned.

```js
function OuterFunction() {

    var outerVariable = 100;

    function InnerFunction() {
        alert(outerVariable);
    }

    return InnerFunction;
}
var innerFunc = OuterFunction();

innerFunc(); // 100

```

In the above example, return InnerFunction; returns InnerFunction from OuterFunction when you call OuterFunction(). A variable innerFunc reference the InnerFunction() only, not the OuterFunction(). So now, when you call innerFunc(), it can still access outerVariable which is declared in OuterFunction(). This is called Closure.

 Closure is useful in hiding implementation detail in JavaScript. In other words, it can be useful to create private variables or functions.

The following example shows how to create private functions & variable.

```js
var counter = (function() {
  var privateCounter = 0;
  function changeBy(val) {
    privateCounter += val;
  }
  return {
    increment: function() {
      changeBy(1);
    },
    decrement: function() {
      changeBy(-1);
    },
    value: function() {
      return privateCounter;
    }
  };   
})();

alert(counter.value()); // 0
counter.increment();
counter.increment();
alert(counter.value()); // 2
counter.decrement();
alert(counter.value()); // 1

```

 In the above example, increment(), decrement() and value() becomes public function because they are included in the return object, whereas changeBy() function becomes private function because it is not returned and only used internally by increment() and decrement().

## Higher Order Functions

A Higher Order Function is any function that returns a function when executed, takes a function as one or more of its arguments, or both.

.filter()
.map()
.reduce()
.forEach()
.find()
.findIndex()
.sort()
.includes()
.concat()

## Best Practices

### Best Practices: Indentation

Bad indentation:

```js
 function problem1(inventory,passid){

if(Array.isArray(inventory)){

return inventory;}

else{
    return [];
}
}

module.exports=problem1;
```

Good indentation:

```js
function problem1(inventory, passid) {
    if(Array.isArray(inventory) && passid<50) {
        return inventory;
    } else {
        return [];
    }
}

module.exports = problem1;
```

An easy way to indent your code is to press Ctrl + Shift + I in VSCode.

For Mac, try Cmd + Shift + I

### Best Practices: Variable Naming

Bad naming:

```js
const a = [1, 2, 3, 4, 5];
const a1 = [1, 4, 9, 16, 25];
```

Good naming:

```js
const numbers = [1, 2, 3, 4, 5];
const squares = [1, 4, 9, 16, 25];
```

Bad naming:

```js
const numbers = [1, 2, 3, 4, 5];

function calc(n) {
    return n * n;
}

const squares = numbers.map(calc);
```

Good naming:

```js
const numbers = [1, 2, 3, 4, 5];

function squareNumber(number) {
    return number * number;
}

const squares = numbers.map(squareNumber);
```

### Best Practices: if else

With if else if is to always use {} with the statements.

Bad usages:

```js
let sum = 10;

if(value %2 == 0)
    sum += value;
else if(value == 0)
    sum += 1;
else
    sum += -1;
```

Good usage:

```js
let sum = 10;

if(value %2 == 0) {
    sum += value;
} else if(value == 0) {
    sum += 1;
} else {
    sum += -1;
}
```

### Best Practices: Higher Order Functions

Bad usage:

```js
const arr = [1, 2, 3, 4, 5];

const numbers = arr.filter(number => number > 5).map(number => number * number).reduce((acc, number) => acc + number);
```

Bad usages:

```js
const arr = [1, 2, 3, 4, 5];

const numbers = arr.filter(number => number > 5)
.map(number => number * number)
.reduce((acc, number) => acc + number);
```

Good indentation:

```js
const arr = [1, 2, 3, 4, 5];

const numbers = arr.filter((number) => {
    return number > 5;
})
.map((number) => {
    return number * number;
})
.reduce((acc, number) => {
    acc = acc + number;

    return acc;
})
```

Good usages:

```js
const arr = [1, 2, 3, 4, 5];

const numbers = arr.filter((number) => {
    return number > 5;
});
```

### Naming Loop Variables

Keeping your variable names as descriptive as possible includes naming variables in loops as well.

Bad naming:

```js
for(let i = 0; i < numbers.length; i++) {
    console.log(numbers[i]);
}
```

Good naming:

```js
for(let index = 0; index < numbers.length; index++) {
    console.log(numbers[index]);
}
```

Avoid Global Variables
Declarations on Top of the function
Declare Objects with const
Declare Arrays with const
Don't Use new Object()
Use === Comparison
Use Parameter Defaults

## Debugging

Debugging is the process of testing, finding, and reducing bugs (errors) in computer programs.

The first known computer bug was a real bug (an insect) stuck in the electronics.

Programming code might contain syntax errors, or logical errors.

Many of these errors are difficult to diagnose.

Searching for (and fixing) errors in programming code is called code debugging.

Debugging is not easy. But fortunately, all modern browsers have a built-in JavaScript debugger. You activate debugging in your browser with the F12 key, and select "Console" in the debugger menu.

### Setting Breakpoints

In the debugger window, you can set breakpoints in the JavaScript code.

At each breakpoint, JavaScript will stop executing, and let you examine JavaScript values.

After examining values, you can resume the execution of code

### The debugger Keyword

The debugger keyword stops the execution of JavaScript, and calls (if available) the debugging function.

This has the same function as setting a breakpoint in the debugger.

If no debugging is available, the debugger statement has no effect.

```js
let x = 15 * 5;
debugger;
document.getElementById("demo").innerHTML = x; 
```

In the above code if the debugger turned on, this code will stop executing before it executes the third line.

## Comparision Operator

```js
    if (5 == '5')     // this comparision operator converts the operand in same data type if it's possible
        return true;
    else 
        return false;
    // output true
```

```js
    if (5 === '5')     // this comparision operator doesn't converts the operand in same data type even it's possible
        return true;
    else 
        return false;
    // output false
```
