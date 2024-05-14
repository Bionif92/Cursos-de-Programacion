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

## Debugging and efficient development

### VSCode shorcuts

Go to `File` -> `Preferences` -> `Keyboard Shortcuts` and look for command names

### Autocompletion

if the function name autocompletion menu has been exited by pressing `ESC`, it can be re-opened with `ctrl + space`.

if the parameters hint has been escaped, it can be reopened with `Trigger Parameter Hints`, `shift + cmd + space`.

### Help and Tips	

https://developer.mozilla.org/es/ Use MDN to help you 
https://ecma-international.org/publications-and-standards/standards/ecma-262/ Use ECMA to see Java languague
https://es.stackoverflow.com/ Forums

To search in google, use `javascript + problem`

### Debuggin
Can use `console.log`to see how the code is in certain part of the script

### Breakpoints
Tell the browser to stop code execution when a certain part of the code is reached
After hitting a `debugger` keyword in the code or `breakpoint` applied on the Chrome dev tools, there are buttons:

- Play button: Resume script execution

- Step over next function call. (kind of go the next line):
  
  ```js
   debugger;
   const enteredNumber = getUserInput();
   // will jump to this line
   currentResult += enteredNumber;
  ```

- down arrow: Step into next function call (chain of function calls)

Will get you inside this function:

```js
function getUserInput() {
  return parseInt(userInput.value); //on this line
}
```

How to get out of that function? press the up arrow

- up arrow: set out of current function

- The right arrow with the point: Step. It's a combination of `Step Over next function call` and `down arrow`.

#### Conditional breakpoints

You can right click `Edit breakpoint` and add a condition for it's triggered.

```js
getUserInput() > 100
```
#### Brekpoints on events

What if I wanna stop JS execution and debbug whenever a registered event for clicks happens in the app? e.g when clicking add, deduct, didive and multiply?
would be cumbersome to add 4 breakpoint manually.

The most efficient way is to use `Event listeners breakpoint` and select `click`.

#### Conect VS Code to Chrome for debug

Install `Javascript Debugger`, then clic on the left side of the sentence of the script you want a breakpoint, and then clic `Run -> Start Debugging` and select Chrome, and change Url on the Launch app that appear, and copy the url of the chrome page

#### Useful information

-   VS Code Docs: [https://code.visualstudio.com/docs](https://code.visualstudio.com/docs)
-   VS Code Keybindings: [https://code.visualstudio.com/docs/getstarted/keybindings](https://code.visualstudio.com/docs/getstarted/keybindings)
-   VS Code Extensions Docs: [https://code.visualstudio.com/docs/editor/extension-gallery](https://code.visualstudio.com/docs/editor/extension-gallery)
-   Google Chrome DevTools Docs: [https://developers.google.com/web/tools/chrome-devtools/](https://developers.google.com/web/tools/chrome-devtools/)

## Control structures

### if blocks

```js
if (condition1) {
    //do something
} else if (condition2) {
    // do something
} else {
    // do something else
}
```
conditions evaluate to true or false.

In order to get this booleans values, `boolean operators` are used:

1) `==` and `!=` equal and non equal operators, they check value. e.g: `3 == '3'` return `true`

2) `===` and `!===` **strict** equal and non equal operators. They **check value and type**. e.g `3 === '3'` returns `false`.

3) `> >= ` and `< <=` for numbers and strings

4) `!` not True operator

#### If and Else If

```js 
if (calculationType == 'ADD') {}

else or else if () {} 
```
else if, when you want to next more conditions

Can put `if`inside a `function`

### Danger!: Comparing objects and Arrays

```javascript
{name: "Esteban"} == {name: "Esteban"} // returns false
[1,2] == [1,2] // returns false
```

event the content is the same, they're different pointers (not copies, like `strings` and `numbers`).

### Early return

it's better to have early returns, so the main logic is not nested in an `if` block:
```javascript
// early return
const someFunction() {
    if (condition I don't want) { ✅
        return
    }

//rest of the logic
}
```

```javascript
// nested main code here, bad practice ❌
const someFunction() {
    if (condition I want) {
        //rest of the logic
    }
}
```
### AND and OR operators

```javascript
if (calculationType !== 'ADD'&& calculationType !== 'SUBTRACT')
```
`&&` Add operator

```javascript
if (calculationType === 'ADD'|| calculationType === 'SUBTRACT')
```
`||` Or operator

### Operators precedence

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence
Order of priority of operators, which one is evaluated first

Which operators are executed first by JS in the same line?

```javascript
3 + 2 < 7 + 20 //returns true

// + operator has precedence over < operator  (is executed first) 
```
### Falsy an truthy values

if non-bolean values are used as a condition, JS coerces ("convert without really converting") them to booleans.

```javascript
if(""){// doesn't get executed} // empty string evaluates to false
if("Hola"){// gets executed} // non-empty strings evaluate to true


if(0){//doesn't get executed}
if(-1){//gets executed} // numbers != 0 evaluate to true

if({}){// all objects are truthy} ⚠️
if([]){// all arrays are truthy} ⚠️

if(null) if(undefined) if(Nan){//all are falsy}
```

### Hardcoded values convention

```javascript
const ATTACK_VALUE = 10;
```

capital letters and underscores.

### Event listeners naming conventions

```javascript
function attackHandler() {}
// OR
function onAttack(){}

attackBtn.addEventListener('click', attackHandler);

attackBtn.addEventListener('click', onAttack);
```
### Putting re-used strings constants into variables

```js
const ATTACK = "ATTACK";

function attackHandler(){
   attack(ATTACK);
}

function attack(mode) {
    let attackMonsterValue;
    if (mode === ATTACK) {...
```

write the string once, and use the variable instead

### Give the user the chance to change initial values

```js
const enterValue = parseInt (prompt ('Maximum life monster and you', '100'));
```
### Check if value is not a number

```js
isNaN (enterValue)
```
use if to change the value if not a number the one given

### Want to put a new line on an object

```js
logEntry.target = 'Monster'
```
The new line contain target

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4MzU4NzM0NDYsMTQ0NDI5NDAyOCwxMT
gxNTMyNTksODI0NTQxNDkzLC0xNjM0NTM2MjQ5XX0=
-->