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
NaN means No
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAzNjgzNzk5NywtMzY2MTY2OTFdfQ==
-->