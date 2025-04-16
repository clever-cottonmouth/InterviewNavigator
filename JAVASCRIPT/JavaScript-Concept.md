# call

The **`call()`** method of [`Function`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function) instances calls this function with a given `this` value and arguments provided individually.
var person =
{
  age: 20
};

let birthDay = function(years) {
  this.age += years;
};

console.log(person.age); //20
birthDay.call(person, 3); //the "this" keyword of birthDay function will refer to "person" object.
console.log(person.age); //23

# apply

The apply() method of Function instances calls this function with a given this value, and arguments provided as an array (or an array-like object).

var student1 = {
  studentName: "Scott",
  section: "A"
};

var student2 = {
  studentName: "John",
  section: "B"
};

//function at outside the object
function calculateTotalMarks(subject1, subject2, subject3)
{
  let totalMarks = subject1 + subject2 + subject3;
  let message = `Hey ${this.studentName}, your total marks is: ${totalMarks}`;
  console.log(message);
}

calculateTotalMarks.apply(student1, [ 60, 70, 80 ] ); //supply "student" object as "this" keyword of calculateTotalMarks function; and also supply the values of array into respective parameters, sequentially.
calculateTotalMarks.apply(student2, [ 56, 45, 88 ] );

# bind

The **`bind()`** method of [`Function`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function) instances creates a new function that, when called, calls this function with its `this` keyword set to the provided value, and a given sequence of arguments preceding any provided when the new function is called.

var student2 = {
  studentName: "John",
  section: "B"
};

//function at outside the object
function calculateTotalMarks(subject1, subject2, subject3)
{
  let totalMarks = subject1 + subject2 + subject3;
  let message = `Hey ${this.studentName}, your total marks is: ${totalMarks}`;
  console.log(message);
}

var student1Calculate = calculateTotalMarks.bind(student1); //it creates a new function and stores reference of student1 as "this" keyword. The function will not be executed.
student1Calculate(60, 70, 80); //executes the function; this = student1

var student2Calculate = calculateTotalMarks.bind(student2); //it creates a new function and stores reference of student2 as "this" keyword. The function will not be executed.
student2Calculate(56, 45, 88); //executes the function; this = student2

var student1 = {
  studentName: "Scott",
  section: "A"
};

# Hoisting

Hoisting is JavaScript's default behavior of moving declarations to the top.

```
alert(Sum(5, 5)); // 10

function Sum(val1, val2)
{
    return val1 + val2;
}
```

Please note that JavaScript compiler does not move function expression.

```
Add(5, 5); // error

var Add = function Sum(val1, val2)
{
    return val1 + val2;
}
```

# Closure

A **closure** is the combination of a function bundled together (enclosed) with references to its surrounding state (the  **lexical environment** ). In other words, a closure gives a function access to its outer scope. In JavaScript, closures are created every time a function is created, at function creation time.

```
function a(){
for (var i = 0; i < 3; i++) {
  setTimeout(function log() {
    console.log(i); // What is logged?
  }, 1000);
}
}
a();
```

```
function init() {
  var name = "Mozilla"; // name is a local variable created by init
  function displayName() {
    // displayName() is the inner function, that forms a closure
    console.log(name); // use variable declared in the parent function
  }
  displayName();
}
init();
```

# Slice And Splice

 * **Modification** :

* `slice()`: Does not modify the original array.
* `splice()`: Modifies the original array.
* **Return Value** :
* `slice()`: Returns a new array containing the extracted elements.
* `splice()`: Returns an array containing the removed elements.
* **Use Cases** :
* `slice()`: When you need a portion of the array without altering the original.
* [`splice()`: When you need to add, remove, or replace elements in the array](https://www.geeksforgeeks.org/what-is-the-difference-between-array-slice-and-array-splice-in-javascript/)


# hasOwnProperty

* Checks only the object’s own properties.

let user = { name: "John", age: 30 };

console.log(user.hasOwnProperty('name')); // true
console.log(user.hasOwnProperty('address')); // false
