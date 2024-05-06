# Javascript Course

## Getting Started

### Prettier VS Code Format Document

`File -> Preferences ->Keyboard Shortcuts`
Type `Format Document`
Option `Shift + Alt + F`

### VSCode settings

`File -> Preferences -> Settings`
`User` applied to all projects
`Workspace` applied to the a specific project

### Using incognito mode on VSCode

It helps preventing extensions running extra code on our apps

### Dev Tool Chrome

`Control + Shift + I`

## Basics: Variables, Data Types, Operators & Functions

`Control + S`Save document

how to add JS code to an `html` file?

1) ```html
   <head>
    <script>
        alert('hey, I'm an alert!)
    </script>
   </head>
   ```

the downside: the html gets long an messy with inline JS.

2) ```html
   <head>
       <script src="path-to-the-JS-file"> </script >
   </head>
   ```
3) Add the script to the end of the `<body>`:
   
   ```html
   <body>
       <script src="path-to-the-JS-file"> </script >
   </body>
   ```

#### The order if JS imports matter

### Declaring variables

A variable can be declared, but not defined, so it becomes a **uninitialized variable**:

```js
let currentResult;
```
and the value is `undefined`.
Use let to declare the variable, then is not need it more

`let`For defining a variable that can change
`const`For a variable that can´t change

### Operators

Styntax features that let us manipulate values

#### Mathematical operators

the not known by me are:

1) `%` that returns the remainder of dividing two numbers. 

2) `**`Exponentiation, `2**3=8`

The operators return things, e.g `+` like the SUM result of two number

#### Data Types
1) Numbers
2) Strings `Hi`The single coma for text, filled with text, nothing or numbers

### String concatenation

adding dinamyc values to strings:

```js
let fullName = 'Franco ' + surname + ' some extra random surname'
```
the `+` operator here doesn't SUM numbers but it joins strings into a single one. Downside? messy syntax. It's better to do **string interpolation**.

### Template literals or string interpolation

is the solution to string concatenation, which is ugly.



```js
let greeting = `Welcome onboard ${userName}`
```

### Writting strings into multiple lines:

#### with string interpolation:

```js
let greeting = `Hello


this is multiline string`
```

in the browser, it looks like this:

`Hello this is a multiline string`

#### With single or double quotes

```js
let greeting = 'Hello ' +
                'this is multiline string'
```

White spaces and tab spaces are not taking into account, because there's a calculation`+` in between. 

So, how to add line breakes and spaces then?

```js
let greeting = 'Hello \n
                this is a multiline string'
```

this `/n` can also be used for backticks, but it's not used too much because the backticks allow line splitting in the code already

The `\` character escapes the next one, that means that then next one is not treated ,e.g, as a normal `n`, but is combined with with the `\` to form a `line break`

More escape sequences here: [String - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#Escape_notation)

### Functions

functions are code on demand.

```js
function addNumbers (num1, num2) {
    //do something here
    return something
}
```
Can write the funtion wherever you want
Need to call a funtion to generate the output

#### IMPORTANT: usually no `;` is added after the the funcion `}` closing curly brace, in function declarations, but it's added to function expressions (functions saved in constants)
`num1` variable is defined inside the function body of the function, which is a block, but can't be used outside the function.

**Strings always have to be in one line** (or split into multiple strings, concatenated `via +`)

### Pure function

```js
// a pure function
function addNumber(num1, num2) {
    return num1 + num2;
}
```

it gets inputs, returns outputs. With the same intputs, it returns the same outputs. 

Funtions can be everywhere in the script, the program will run them first

Can not use variable as global if they are inside a funtion. Whith`return`you can use the variable outside

### Shadow variables

it's a local variable, declared in a function, that has the same name as an already declared global variable.

```js
let userName = 'Max';
function greetUser(name) {
  let userName = name;
  alert(userName);
}
userName = 'Manu';
greetUser('Max'); // will still greet Max
```

the local `userName` variable inside the funtion is `shadowed`, so it doesn't overwrite the global variable, it's a different variable than the global one, named the same, inside the function block.

### The return statement:

the `return` statement finish the function execution.

### Direct and Indirect funtion
`add()`for use the funtion inmidiatelly
`add` to use the funtion when is called

### Mixing Numbers & Strings

If we give JS a string and number in a sum, it will treat the number as a string, and create a long string:

```js
let sum = 1 + someInput.value; 
``` 
Will return a string
To change it to a number use `parseInt`(without float number) or `parseFloat`(with float) or put a `+`before the variable
```js
let sum = 1 + +someInput.value; 
``` 
`currentResult.toString()`will change number to string

`+` can add a string with number
`- , * , / ` generate the ecuation with a number and a string

```js
const calcDescription = `${currentResult} + ${userInput.value}`

```
// it has currentResult.toString() under the hood

### Comments

```
// this is a comment

/* this is a block comment
that can use multiple lines!*/
```
### More operators

```js
currentResult = currentResult + enteredNumber;

// SAME AS

currentResult += enteredNumber
// it also works for -, * and / operators
```

```js
currentResult = currentResult + 1

// SAME AS

currentResult++

// it also works for -
currentResult--

// the ++ is Increment operator
// the -- is Decrement operator

//they return the value of the value before change
```

```js
++currentResult // returns the modified value
```

### Arrays

```js
let logEntries = [];

logEntries.push (enteredNumber) // to enter the data you need in the array

console.log (logEntries) // put the list in console of Chrome

console.log (logEntries[0])// only first number of arrray appear, 1 the second, and so on
```
Appear `undefined` if the value doesn´t exist yet, 

### Objects

```js
const logEntry = {operation:'ADD',prevResult:number 1,number:number 2,result: number 3}

logEntries.push (logEntry) 

console.log (logEntries)// log the entire object and the array
```
To access an specific part of the object 

```js
console.log (logEntry.operation)
```
### Undefined, Null and NaN

To reset a variable:

```js 
username = null
```

NaN means Not a Number

```js 
username = 3 * 'hi'
```
The result will be NaN

### Type Of

Wanna check the `type` of a variable at runtime? it returns a string with the type.

```js
typeof 'hola' // prints "string"
typeof 1 // prints "number"
```

playing with `typeof`:

```js
typeof undefined; // prints "undefined""
typeof null; // prints "object"
typeof NaN // print "number"


typeof {name: "tebi"} // prints "object"
typeof [1,2] // prints "object"
```

### Async and defer: never blocks HTML parsing 😉

#### ⚠️ make sure you start downloading your scripts in the head!

Keep this word in mind: **HTML parsing**

If `JS` code depends on `HTML` (like accessing DOM elements), the `JS` files can be imported at the end of the `<body>`:

```html
   </body>
   SOME HTML HERE

    <script src="assets/scripts/vendor.js"></script>
    <script src="assets/scripts/app.js"></script>
  </body>
```

BUT, there's a performace issue, that can be checked going to `Incognito chrome tab` -> `inspect` -> `performance` -> `start recording` -> `check the timeline` -> `expand Network part in the zoom in the middle window`.

Then look at `Main` in the lower window, to see events:
The HTML is finished parsed, and then after some miliseconds, the `Scripts` are Evaluated. We could do better.

The key:

###### I'd like to `start downloading the scripts` at the same time as `Parsing the HTML`, but executing the `Scripts` after the `HTML Parsing` has been finished.

Option 1: (not recommended)

```html
<head>
  <script src="assets/scripts/vendor.js"></script>
  <script src="assets/scripts/app.js"></script>   
</head>
<body>
</body>
```

⚠️ It throws an error because the `JS` code targets DOM elements not yet parsed.
```bash
Uncaught ReferenceError: addBtn is not defined
    at app.js:59
```

The download of the `JS` files blocks (or stops) the HTML parsing.

### Defer attribute: when the JS targets the DOM

Download JS -> execute it when the HTML parsing finished.

it tells the browser to download the `JS` files straight away, no blocking the **HTML parsing**, and execute the `JS` after the HTML has been parsed.
```html
<head>
  <script src="assets/scripts/vendor.js" defer></script>
  <script src="assets/scripts/app.js" defer></script>   
</head>
<body>
</body>
```

💡The time difference between the end of the HTML parse and the `Script execution` is much shorter than when importing the scripts at the end of the `<body>`.

With `defer` the scripts execution follows the order they're listed on the HTML.

### Async attribute: when the JS doesn't target the DOM

Download JS -> execute when finished downloading - difference with defer, execute all right away

when the  `JS` doesnt target the DOM, why bothering waiting for the HTML parse to finish? it just executes the `JS` when the download finished. When script dont interact with the web page, you use `async`

```html
<head>
  <script src="assets/scripts/vendor.js" async></script>
  <script src="assets/scripts/app.js" async></script>   
</head>
<body>
</body>
```

when using `async` the order of the scripts executions depends on which one gets downloaded first.

⚠️`async & defer` doesn't have any effect when used here:
```html
//No effect!
<script defer or async>
 alert('hello world')
</script>
```

because there's no such `JS` file to download.😅
```html
// DONT combine inline JS and src
// the inline script will be ignored!
<script src="...">
 alert('hello world')
</script>
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY2Nzg0MzIzMl19
-->