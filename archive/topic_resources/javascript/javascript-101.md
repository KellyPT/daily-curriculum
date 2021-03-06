## JavaScript basics

### Playing with JavaScript

Safari, Firefox, and Chrome all support a JavaScript console, which
allows us to write JavaScript directly in the browser. In Chrome, you
can access the console either via the menu (View > Developer >
JavaScript Console), or via the keyboard shortcut (Command - Option - J).

There are also several sites that allow you to live code JavaScript,
HTML, and CSS. The three most popular are [JSFiddle](//jsfiddle.net),
[CodePen](//codepen.io), and [JS Bin](//jsbin.com). We'll use
JSFiddle for demonstrations, but it's a matter of taste.

Since we are used to using a REPL like IRB, we will be using Node's REPL which will look quite familiar to us now.

### Getting Help

The best JS documentation is on the
[Mozilla Developer Network](https://developer.mozilla.org). ProTip:
add "mdn" to your Google searches about JavaScript
questions. W3Schools results will show up above MDN otherwise, and
their documentation is not as useful.

### Variables

Declare all variables with the var operator!

```javascript
var five = 5;
```

If you omit ```var``` you will get a global variable, which can lead
to all sorts of problems. __JUST DON'T DO IT!__

**Note** that each line of JavaScript code ends with the `;`.
This is optional for the code to work (sometimes, and the rules are inconsistent) but **not** optional when taking into consideration style guidelines.

### Types

[MDN Data Types and Data Structures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)

JavaScript supports similar basic types to Ruby: Boolean, Null,
Undefined, Number, String, Array, Object, and Function.

Open the REPL and try the following examples.

* Boolean is true or false

```javascript
var t = true;
var f = false;
```

* Null is the value null. This represents an "empty" value.

```javascript
var empty = null; // this is false in an if statement
```

* Undefined is the value undefined. When a variable which has not
  declared is accessed, JS returns undefined.

```javascript
if (blahblah) {  // blahblah has not been declared it returns undefined
                 // which is false-y
    // so, this won't happen
}
```

* Number is a numeric value including integers (1, 2, 3, etc.), floats
  (1.4, -40.1), infinity (+Infinity, -Infinity), and NaN which means
  "not a number." NaN is returned when you do a numeric operation on
  anything that's not a Number.

```javascript
var four = 4,     // Note the comma-separated variable declarations
    two = 2.0;

Infinity < Number.MAX_VALUE  // false
Infinity > Number.MAX_VALUE  // true

two == four / two; // true

// All JS numbers are floats, and floats are not 100% accurate...
0.1 + 0.2 == 0.3; // false!
0.1 + 0.2;

"asdf" - 5; // NaN
```

* Strings a declared with "" or ''. They're basically the
  same. Pick one and stick with it!

```javascript
var str = "This is a string";
str.length;      // 16 - access the length property
str.substr(2,5); // "is is" - call the substr function
```

### Arrays
* [Arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) are similar to Ruby arrays. They are declared and accessed
  with square brackets ([]).

```javascript
var arr = [1, 2, 3, 4];
arr.length;  // 4 - access the length property
             // Note this *cannot* be accessed like a method with parenthesis
arr[0];      // 1
arr.pop()    // 4 - call the pop() function
             // Note this method *cannot* be used without the parenthesis
arr;         // [1, 2, 3]
```

### Objects
* [Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object) are like simple Ruby hashes. They are declared with braces
  (`{}`). You can access properties in an Object with bracket notation
  (like an array) or dot notation.

```javascript
var obj = {     // We can span lines; whitespace is mostly ignored.
  num: 5,
  str: "This is a string",
  subObject: {
    otherNum: 4
  }
};

obj.num;    // 5
obj['num']; // 5; note we use a string!
obj.subObject.otherNum; // 4
obj.foo;    // undefined

```

### [Conditionals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else)
* Conditions are surrounded by parenthesis `()` and each block is surrounded by brackets `{}`.
```javascript
var name = "kittens";
if (name == "puppies") {
  name += "!";
} else if (name == "kittens") {
  name += "!!";
} else {
  name = "!" + name;
}
name == "kittens!!"
```

* JavaScript also has the ternary operator
```javascript
var adult = (age > 18) ? "yes" : "no";
```

### Iterators
#### For Loop
- Most common is the **for-loop** which has three parts:
  - `var i = 0` - **starter**  
    This executes at loop start.
  - `i < 5` - **loop condition**  
    The condition to check if loop is finished. It is checked after every execution of loop body.
  - `i++` - **increment**  
    An action to perform after every iteration, but before the loop condition is checked.


```javascript
for (var i = 0; i < 5; i++) {
  // Will execute 5 times
}
```

#### While Loop
JavaScript also uses the `while` loop in a similar way to the way we use it in Ruby.

```javascript
var i = 0;
while (i < 10) {
    text += "The number is " + i;
    i++;
}
console.log(text);
```

### Functions
* Functions in JavaScript are awesome. Rather than using the `def` keyword like we're used to, JavaScript uses the `function` keyword to declare a function.

```javascript
function (choice1, choice2) {
  if (choice1 == choice2) {
    return "This is the same!";
  }
}
```

They are more "pure" than Ruby
  methods and can be put in variables, and passed around like any
  other type. Understanding functions is the key to JavaScript
  enlightenment.

```javascript
var adder = function (a, b) {
    return a + b;   // You need to explicitly call return in JavaScript
}

// You need to use parens to call your function!
adder;        // this returns the function that you just declared
adder(1, 2);  // 3 - this executes the function and returns the result
```

# JavaScript Exercises

### Exercise #1: Create a ToDo object, with the following properties:

- a task (a string) - a description of the thing to do
- assignee (a string) - the name of a person to do it
- done (a boolean) - is the task done or not?
- getDone (a method) - get the value of done, use "this" in the body of the method.
- setDone (a method) - set the value of done, use "this" in the body of the method.

```javascript
var todoList = {
  task: "I am a task",
  assignee: "jeremy",
  done: false,
  getDone: function() { return this.done; },
  setDone: function(state) { this.done = state; }
}
```

### Exercise #2: Find the biggest number in the array

- Utilize the stub code below to complete the problem:
 - `getBiggest`should accept an array as a parameter and return a numeric value which corresponds to the largest value

```javascript
var arrayOfNums = [2, 7, 7, 3, 9, 0, 1, 6, 8, 3, 8, 4, 7, 9];

function getBiggest(array) {

// your code goes here!!

}

//
// pass an array to getBiggest;
// get a return value that is the biggest number in the array
//
var biggest = getBiggest(arrayOfNums);
console.log("The biggest is: ", biggest);
```
