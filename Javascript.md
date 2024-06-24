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

### Declaring a constant with 2 possible values

It's a great scenario for a `ternary operator`:

```js
const userName = mode===MODE_ATTACK ? ATTACK_VALUE : STRONGATTACK_VALUE;
```

use for simple stuff, not nesting it, because gets unreadable

### Expression vs Statement

```js
// expression - used on the right hand side of assignment operators
// it returns something
isLoggedIn ? 'Max' : null;

//statement. It CAN'T be used on the right hand side of assignment operators

const username = const somethingelse ❌

// an `if` STATEMENT is an example
```
### Boolean tricks with logical operators

**Double bang** `!!` to convert truthy/falsy values to true/false:

```js
!!"" // return false
```

**Default value** assigment via OR || operator:

```js
const userName = someInput || 'Max'; // the || operator will return the 
// first truthy value
```
**double &&**:
```js
const userName = isLoggedIn && 'Max' 
// will assign 'Max if isLoggedIn is trushy
// and will assign the isLoggedIn value if it's falsy
```

### Switch statement

```js
if (location === 'Argentina'){
    console.log('hola')
} else if (location === 'UK'){
    console.log('hello');
} else if //
```

the above code repeats the equality expression, so `switch` statement is a more compact alternative:

```js
switch(location) { // location or and expresion that returns a value
    case 'argentina':
        console.log('hola');
    break;
    case 'UK': {
       console.log('hello');
    }
    break;
}
```

`switch` uses `===` under the hood.

add `break` keyword, because `switch` statements use `fall through` mechanism, and it doesn't stop till the end.
 Use `default`for the last condition
 
### For loop

```js
for (let i = 0; i < 10; i++){
    //do something
}
```

`let i = 10` is code that runs at the beginning, and `let` has been chosen in order to reassign it.

`i < 10` is a condition that gets evaluated on every iteration;

`i++` is a code that runs after every iteration.

### For of (arrays)
```js
 for (const el of log) {
    console.log(el);
 }

 // const is used because el is recreated on every iteration
```
**Use log. lenght for the amount of thing inside**

The above syntax simplifies this loop:

```js
  for (let i = 0; i < log.length; i++) {
        console.log(log[i]);
    }
```

variables defined inside the `for` parenthesis, are scoped to the loop.

Do you want to keep track of the index as well? no problem:

```js
let i = 0;
 for (const el of log) {
    console.log(el);
    console.log(i);
    i++;
 }
```
### For in (objects)
```js
const offer = {
        price: 10,
        tag: 'perfume'
    }
    for (const key in offer) {
        console.log(offer[key]);
    }
```

`offer.key` won't work because JS will look for a property in the object called `key`.

A string must be passed to inside the brackets [];

### While loop

```js
 let i = 0;
    while (i < 10) {
        console.log(i);
        i++
    }
 // the above example should be done with a classic for loop instead

 let finished = false;
 const randomNumbers = [];
 while (!finished) {
     const rndNumber = Math.random();
     randomNumbers.push(rndNumber);
     if (rndNumber < 0.5) {
         // to exit the loop  
         finished = true;
 }
 }
```

a while loop start not knowing how many iterations it will take to complete.

### Do while loop

```js
let i = 10
do {
        console.log(i);
        i++
    }
    while (i < 10);

// will print 10, because the do block runs first
```

how does it work? first do, then check the condition

### Loop + break: good for liping iterations execution

```js
for (let i = 0; i < 5; i++) {
        //lets stops the execution if i === 3
        if (i === 3) {
            break;
        }
        console.log(i);
    }

//prints 0,1,2
```

useful for stoping the loop executions under certain conditions.

### Loop + continue:  good for skipping one iteration

```js
for (let i = 0; i < 5; i++) {
       //lets avoid printing 3
       if (i === 3) {
           continue;
       }
       console.log(i);
   }

// prints 0,1,2,4
```

### Labels: useful for breaking outer loop from inside inner loop

```js
outerLoop: for (let i = 0; i < 5; i++) {
    console.log('outer', i);
    for (let i = 0; i < 5; i++) {
        if (i === 3) {
            break outerLoop;
        }
        console.log('inner', i);
    }
}
```
You name `outerLoop` the loop of your choise

### Try and catch

We can throw many things that will stop execution, like objects, strings, Error, etc

```js
throw {message: 'code below wont run'};

//it prints: app.js:155 Uncaught {message: 'code below wont run'}
//, (in red colour, indicating it's a system error);
```

maybe a `user input` or `network error` causes the code to stop exectution, not ideal, right?

```js
try {
    throw {message: 'code below wont run'};
} catch {
    console.log('there was an error, but code below will be executed :)')
}
// code below keeps being executed!
```

It's common to throw our own errors in the app, so we save up adding a lot of if statements for different types of errors.

```js
let chosenMaxLife;

function getValue() {
    const enteredValue = prompt('enter the max life value', '100');
    userInput = +enteredValue;
    if(isNaN(userInput) || userInput <= 0) {
        throw {message: 'invalid user input'}
    } else {
        return userInput;
    }
}

try {
    chosenMaxLife = getValue();

} catch (error) {
    console.log(error);
    chosenMaxLife = 100;
}
```

### Finally block

is rarely used.

```js
try {
    // some code that might fail
} catch (error) {
    // maybe store the error in a database
    // re-throw the errror
    throw(error); // not very common, very advanced
} finally {
    // runs after the try {} block;
    // do something, if throws error, rest of code wont execute 
    // wont run if there isnt an error
}
// rest of the code
```

The following resources may be helpful.

-   Control Structures (MDN): [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Control_flow_and_error_handling](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
-   JavaScript Loops (MDN): [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration)

### ES5 &  ES6

Var vs Let & Const

1) **Better scoping**

2. **Better variables and usage order declaration**

3. **Avoids redeclaring variables**:

Use let and const all the time. Block the variables inside the {}, var doesn´t

Var has global/function (local) scope and let and const have block scope (variables created on {} stay on that scope)

4. **Strict-mode can be enabled**
   
   use `use strict` mode at the file or function level, to avoid unexpected behaviours, that browser vendors do when executing the JS code. Generally, it's not neccessary.
   
   ```js
   // behaviour no 1: assigning a non declared variable
   
   userName = 'Max' // assigning value to a non declared variable
   console.log(userName); // prints Max, wow! 
   
   
   'use strict'
    userName = 'Max'
    console.log(userName); // throws an error
   // uncaught ReferenceError: userName is not defined

​		  

```js
 // behaviour no 2: assigning a reserved name
 var undefined = 'foo' // doesnt throw an error

 'use strict'
 var undefined = 'foo' // Uncaught TypeError: Cannot assign 
 // to read only property 'undefined' of object '#<Window>'


 //using let or const, also disables this behaviour
 let undefined = 'foo';
 const undefined = 'foo'; // Uncaught SyntaxError: Identifier 
 //'undefined' has already been declared
```
## JS engines and what they do

#### Parsing and compilation

code is interpreted to `bytecode` (faster) and starts execution, but still low performance, so it's then compiled to `machine code` (OS code) that runs on the chip.

What are browser APIs? bridges between the JS code and C++ code built in the browser, like `window.document`, etc

#### Execution: inside the JS engine

1) Managing memory: `heap` is long term memory. The `stack` is the short term memory and manages which function is executing and if there's a return, to which function is returning a value to.
   
   functions code gets stored in the `heap`.
   
   The browser reaches the `heap` and the `stack`.

2) Managing execution steps


### The `stack`

the first thing to be pushed to the `stack` is all the code present in the file, and it's kind of wrapped in an `anonymous` function. Then, the function `greet()` is added to the top of the stack, so the thing on top of th stack is the thing that is currently running.
Then, `getName()` is added to the top of the stack; Then `prompt()` is added to the top of the stack.

The stack manages execution contenxt, e.g which functions are being executed, and the order of the nested calls and primitite values (cheap to re-create). The heap stores reference values, like objects, because are expensive the re-create.

One the `prompt()` function is done, by returning a value to `getName()` is being removed from the stack;

Even if a function doesn't have a `return` statement, there's an implicit return after the last line, which makes the stack to remove when done.

Once the `greet()` function is done, the `anonymous` function is also removed from the stack because there's no more things to run on the file.

```js
function getUserName() {
  return prompt('enter userName', '');
}


function greet() {
  const userName = getUserName();
  console.log('Hello' + userName);
}

greet();
```

The stack is a shortlive data structure to keep track of which functions are being executed.

#### Debugger & the stack

go to `Sources`, place a breakpoint, and the check the stack, you'll see the functions there stacked.

So to sum it up JS engine = heap + stack.

If event listeners have been set up, the `Event loop` knows them and it will reach the JS engine and push callback functions to the stack.

### Primitive vs Reference values

#### Primitives

 are shared by copy (they'r cheap to re-create! stored in the stack (short term things))

```js
let name = "Max";
let anotherName = name; // "Max" was copied, stored in the stack,
// and passed here
console.log(anotherName) // prints "Max";
name = "Manu";
console.log(anotherName) // still prints "Max";
```

name.length(), tells us that a string can be temparely be transformed to an object to access some properties.


#### Reference values:

when assigning an object to a variable, the pointer is stored in that variable, not the object itself.

they're expensive to re-create (stored in the heap)

```js
let userData = {
    name: 'tebi',
    age: 32
}; // this object is stored in the heap, and userData holds the 
// pointer (or reference) to it.

let newUserData  = userData; // the same pointer is passed here

userData.name = 'Sarah';
console.log(newUserData.name) = 'Sarah';
```

How to avoid mutating the object? cloning objects and arrays

```js
let newUserData = {...userData};
userData.name = 'Sarah'; // 
console.log(newUserData.name) = 'tebi'; // different pointer
// it's pointing to another object, a clone one
```

### Garbage collection

JS engines have garbage collectors that delete stored things in the heap.

```js
let person = {name: 'Max'};
person = null; 
// garbage collector deletes {name: 'Max'} from the heap;
// because the pointer is no longer used in the rest of the code
```

Nowadays, browsers are intelligent enough to check if `person` is being used or not, and also delete the object from the heap, without the need of having to reassign the variable to null, for example.

#### Memory leaks

when you keep having references to objects in the code, but you don't use them, so it's means keeping space in memory for nothing.

adding `click` event listeners to a button will always result on event listener replacement `if the same function pointer is passed as callback`, so a button will woun't trigger 2 callback functions.

```js
function print() {
    console.log('button clicked');
}

someHtmlElement.addEventListener('click', print);
someHtmlElement.addEventListener('click', print);

// upon click, just one console.log() will be printed


someHtmlElement.addEventListener('click', function() {console.log('button clicked')};
someHtmlElement.addEventListener('click', function() {console.log('button clicked')};

//upon click, 2 console.log() will be printed!!
// 2 functions that do the same are stored in the heap!
// that's a memory leak;
```

## More on functions

### Parameters vs Arguments

**Parameters**  are these variables which you  **specify between parentheses**  when defining a function.

`function sayHi(name) { ... } `

In this example,  `name`  is a parameter.

**Arguments**  then are the  **concrete values**  you pass to a function when calling that function:

`sayHi('Max');`

`'Max'` is an  **argument**  of the function therefore - for the  `name`  parameter to be precise.

### Method

Function inside an object

`addEventListener`is a method

### Functions are objects

````javascript
function hello () {
    console.log('hello');
} 👈 // no semicolon to function declarations, that's the convention

console.log(typeof hello); // prints `function`

console.dir(hello) // it prints the function object!
````

The method **`console.dir()`** displays an interactive list of the properties of the specified JavaScript object.

### Function expression vs function declaration

Expression: right hand side of an `=` operator.

````javascript
// right hand side, it's an expression
const start = function 👉 ❌startGame() { // the name of the function is not needed, could be anonymous
  console.log('Game is starting...');
}; 👈 // semicolon is usually added to expressions.
startGameBtn.addEventListener('click', start);

//it's a declaration
function startGame() {}
````

```javascript
// right hand side breaks hoisting! `start` is hoisted as undefined 😕
startGameBtn.addEventListener('click', start);

const start = function() {
  console.log('Game is starting...');
};

❌ Uncaught ReferenceError: Cannot access 'start' before initialization
    at app.js:16:40
```

### Which approach to choose?

the expression approach is prefered since it forces devs to declare the function before calling it:

```javascript
✅ // prefered approach
const start = function() {
  console.log('Game is starting...');
};
```

### To be anonymous or not, that's the question 🤔

You might want to name them to get better logs in the console when that function breaks.

```javascript
// anonymous function log
startGameBtn.addEventListener('click', function() {
  console.log('Game is starting...', age);
});

app.js:19 Uncaught ReferenceError: age is not defined
    at HTMLButtonElement.<anonymous>👈 (app.js:19:38) 👈 // line number is not enough when having bundled code in prod


// named function log
    startGameBtn.addEventListener('click', function startGame() {
  console.log('Game is starting...', age);
});

app.js:4 Uncaught ReferenceError: age is not defined
    at HTMLButtonElement.startGame👈 (app.js:4:38) 
```

### Arrow functions

`=>` is a keyword made up of math symbols, it's not an operator like the `=` operator!

Predence: && have precedence over || operator, so && are executed before.

````javascript
// empty return, `undefined` is returned
const getWinner = (computerSelection, playerSelection) => {
	....some code
	return;
}

const winner = getWinner(); // winner will be `undefined`
````

````javascript
// calling functions with less arguments than expected
// there's no JS error 😮

 const winner = getWinner(computerSelection); // doesn't throw error!
````

````js
// fallback params!

const getWinner = (computerSelection, playerSelection👉 = DEFAULT_SELECTION) => {
  // only kicks in when `playerSelection` is `undefined`.
  // it doesn't work for falsy values, like null, 0, etc
  
// we can add a value depending on other argument's values!
  const getWinner = (computerSelection, playerSelection👉 = computerSelection === ROCK ? PAPER : DEFAULT_SELECTION) => {
````

### Default Arguments

`const getWinner= (cChoise, pChoise= Default_User_Choise)`

Always the last parameter can put this way, with a default value

### How to add breakpoints when the code stopped in one?

just go to `Source` in the dev tools and add a new breakpoint with the cursos, and press the play button! Easy!

I can also disable the selected breakpoints by going to `Source->Breakpoints` window, and uncheck them!

### Rest parameters (...someNumers)

variable amount of arguments! https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters

this function it can handle any number of args:

```js
const addNumbers = (...numbers) => {
  let sum = 0;
  numbers.forEach(number => {
    sum = sum + number;
  });
  return sum;
}

console.log(addNumbers(1,2));
```

The arguments get added to an array, so we can iterate over it!

```js
// OLD way ❌

const addNumbers = function () {
  let sum = 0;
  for (number of 👉 arguments) { // arguments is magically in the scope of the fn,
    // it's not an array, an array-like object, so it doesn't have the .forEach method 😮
    sum = sum + number;
  }
  return sum;
}

console.log(addNumbers(1,2));
```

### Declaring functions inside functions

````js
const addNumbers = (...numbers) => {
  👉 const validateNumber = (number) => {
		return isNaN(number) ? 0 : number;
	}

  let sum = 0;
  numbers.forEach(number => {
    sum = sum + validateNumber(number);
  });
  return sum;
}
````

functions are objects, so we can can objects stored inside objects, right?

The `validateNumber` function is scoped to the curly braces of the parent function.

### Callbacks

````
const addNumbers = (👉 callback, ...numbers) => {
  const validateNumber = (number) => {
		return isNaN(number) ? 0 : number;
	}

  let sum = 0;
  numbers.forEach(number => {
    sum = sum + validateNumber(number);
  });
  👉callback(sum);
}

const myCallBack = (sum) => {
  alert(sum);
}

addNumbers(👉myCallBack, 1,2, 'banana', 5);
````
In an example

```
function checkImput (cb, ...strings) {
let HasEmptyText = false
for (const text of strings) {
if (!text) { HasEmptyText = true; 
break;}}
if (!HasEmptyText) {cb ()}
}

checkImput (() => {console.log ('All not empty')}, 'Hello', '12', 'adsfa','')
```

Otro ejemplo

```
function saludar(nombre) {
  alert("Hola " + nombre);
}

function procesarEntradaUsuario(callback) {
  var nombre = prompt("Por favor ingresa tu nombre.");
  callback(nombre);
}

procesarEntradaUsuario(saludar);
```


### Adding extra parameters on the fly: the .bind() method:

Using .bind() method returns a new function reference with some new configuration (give values to some params), so that function can be called at some point (upon an event, etc) with the pre-configured param values!

````js
const sayHello2 = (👉 greeting, name) =>{
  console.log(greeting + name);
}
// silly example calling the function right away, not done in real life

sayHello2.bind(this, 👉'Special greetings ','tebi!'); // Special greetings, tebi!
````

💡 usually the binded function is passed as a callback fn an then exectuted at some point by the parent function

````js
someFn(sayHello2.bind(this, 'Special greetings'), someOtherParams);

const someFn = (callback, someOtherParams) => {
	callback('tebi');
}

// there could be some logic inside the someFn to pass the appropiate greeting to callback, but that could lead
// to a lot of if checks on the someOtherParams, or ternary expressions
````

````js
// bind usage in the calculator
// the callbacks are preconfigured for each button 🔥
const operators = {
  ADD: '+',
  SUBSTRACT: '-',
  MULTIPLY: '*',
  DIVIDE: '/'
}

function calculate(operation) {
  const enteredNumber = getUserNumberInput();
  const initialResult = currentResult;
  
  if (operation === 'ADD') {
    currentResult += enteredNumber;
  } else if (operation === 'SUBTRACT') {
    currentResult -= enteredNumber;
  } else if (operation === 'MULTIPLY') {
    currentResult *= enteredNumber;
  } else {
    currentResult /= enteredNumber;
  }
  createAndWriteOutput(operator.operation, initialResult, enteredNumber);
  writeToLog(operation, initialResult, enteredNumber, currentResult);
}

addBtn.addEventListener('click', calculate.bind(this, 'ADD'));
subtractBtn.addEventListener('click', calculate.bind(this, 'SUBTRACT'));
multiplyBtn.addEventListener('click', calculate.bind(this, 'MULTIPLY'));
divideBtn.addEventListener('click', calculate.bind(this, 'DIVIDE'));
````

The following resources may be helpful.

-   More on Functions (MDN): [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)
-   bind(): [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Function/bind](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Function/bind)

### Interacting with the DOM

````
// console
document
// we see kind of HTML, and we can select html elements, and they get hovered on the page
// document is just a JS object (with all the methods we need), represented by Chrome in this HTML way in the console.
````
````bash
console.dir(document) // to see the full object!
````

### Why can we use `alert()` without the window.?

because the browser adds the window. to functions and variables it doesn't find in our code! 😮

### Document vs Window

Two are global objetct, Document is part of the Window

**Document**: Root DOM Node, provide access to element queryng, DOM document

**Window**: The active browser window, act as the global storage of the script, provides access to specific window properties and methods

### The DOM

There are 2 types of Nodes (JS objects):

- Element Nodes divs, paragraphs, etc
- Text Nodes (white spaces coming from the indentation of the HTML file)

whitespaces are Text Nodes, and not rendered in the screen 😮

#### The `$0` shortcut:

the last selected element in the `Elements` tab in the dev tools gets stored in the `$0` variable, so it can be used in the console, neat!

We can't see the text nodes in the `Elements` tab.

### Targeting elements

there are 2 camps of methods:

- return the fisrt match (getElementById, querySelector)
- return an array-like array: NodeList (it might not have .forEach and other methods) (e.g querySelectorAll)

`document.querySelector ('li:last-of-type')` return the last list item

💡`getElementBySomething` methods return an object that is updated if the Node changes later in time ⏺

the other ones just return a snapshot of the Nodes 📸

### Applying methods on Element Nodes

we can do `someElement.querySelector('some-selector');` that's great! we can have a more scoped search

`getElementById` is not inside Element Nodes, only in the document.

```js
const h1 = document.querySelector('h1');
h1.textContent = 'Lalala'; // deletes and creates a new Text Node
```

Use mdn to look for the Element Node documentation, e.g h1. Under `DOM interface`, we have, eg. https://developer.mozilla.org/en-US/docs/Web/API/HTMLHeadingElement.

Some props are read only ⚠️

### Node query methods

Here's a summary of the various methods you got to reach out to DOM elements (note: you can only query for element nodes).

Besides the below query methods, you also got these special properties on the document object to select parts of the document:

`document.body`  => Selects the  `<body>`  element node.

`document.head`  => Selects the  `<head>` element node.

`document.documentElement`  => Selects the  `<html>`  element node

### Query methods

`document.querySelector(<CSS selector>);`

Takes any CSS selector (e.g.  `'#some-id'`,  `'.some-class'`  or  `'div p.some-class'`) and returns the first (!) matching element in the DOM. Returns  `null`  if no matching element could be found.

More information: [https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)

`document.getElementById(<ID>);`

Takes an ID (without  `#`, just the id name) and returns the element that has this id. Since the same ID shouldn't occur more than once on your page, it'll always return exactly that one element. Returns  `null`  if no element with the specified ID could be found.

More information: [https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById)

`document.querySelectorAll(<CSS selector>);`

Takes any CSS selector (e.g.  `'#some-id'`,  `'.some-class'`  or  `'div p.some-class'`) and returns all matching elements in the DOM as a static (non-live) `NodeList`. Returns and empty  `NodeList`  if no matching element could be found.

More information: [https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll)

`document.getElementsByClassName(<CSS CLASS>);`

Takes a CSS class g (e.g.  `'some-class'`) and returns a live  `HTMLCollection`  of matched elements in your DOM. Returns an empty  `HTMLCollection`  if not matching elements were found.

More information: [https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByClassName](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByClassName)

`document.getElementsByTagName(<HTML TAG>);`

Takes an HTML tag (e.g.  `'p'`) and returns a live  `HTMLCollection`  of matched elements in your DOM. Returns an empty  `HTMLCollection`  if not matching elements were found.

More information: [https://developer.mozilla.org/en-US/docs/Web/API/Element/getElementsByTagName](https://developer.mozilla.org/en-US/docs/Web/API/Element/getElementsByTagName)

There also is the  `getElementsByName()` method which really isn't used commonly ([https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByName](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByName)).

### Attributes vs Properties

- Attributes: what's inside the HTML tag, e.g `id`
- Properties: the browsers configures some props, like the `id` based what is was passed in the HTML as attributes

Some attributes, like <input value="some text here">, can't be changes with input.value method.

````
<input value="some text here">
input.value = 'other random text'

// we check Elements tab
<input value="some text here"> // still the same, one way data binding


input.id = 'some-id';
<input value="some text here" 👉 id="some-id"> // updates the HTML! 2 way data binding
````

So, when the user types, the value of `value` is updated in the JS object but not on the HTML attribute read on Elements tab, so 

````
input.setAttribute('value', 'some other default text');
<input 👉 value="some other default text">

input.value = 'some previous text the user entered' // decoupled state!
````

💡value attribute and property are decouple on purpose, so we can always backtrack to the original value if we need to, after the user entered some text:

````js
input.value = input.getAttribute('value'); // reseting the value propr with the original attribute!
````

Tip: the JS object propr and the rendered UI are in sync

`input.getAttribute()` helps to read the value written in the HTML tag attribute

### Changing color 

`const  var1  =  document.getElementById ('task-1');`
`var1.style.color  =  'white';`

### Selecting multiple elements

`document.querySelectorAll()` or `document.getElementsByTagName ()`

Last one will be dinamic

### Traversing the DOM: children, descendents, Parent and Ancestors

use `.children` to navigate the Node Elements (skiping the Text Nodes);

if you use `.childNodes` you get the list of all nodes (Elements and Text).

Remember: even the indentation of the HTML gets converted into text nodes. e.g: `someTextNode.data: "\n      "`

How to see the text nodes being rendered on the screen:
```css
// add this to the ol/ul or other element on the console
element.style {
    white-space: pre;
}
```

Then, if we have the nodelist of text and element nodes in the console.dir, and we hover over the text nodes, we'll see them highlighted in the rendered page!

### Child Nodes Examples

```
const ul = document.querySelector ('ul')

ul.children // see an array of the nodes inside

ul.children [1] // get the second line

ul.childNodes // see elements and text nodes 
```
#### Perfomance issues:

````
document.querySelector('li:last-of-type'); // 🐌 running a query like that at the document level is expensive!

document.querySelector('ul').lastElementChild() 🚀
````

`````
someElement.closest('some-selector'); // looks for the closes parent that matches that selector
// it's kind of querySelector but for looking upstream
`````

💡 Run as fewer .querySelector queries as possible, and use parent and children navigation instead (always taking into account code readability, and future changes in the HTML order)

Deep traversing is also bad for perfomance

### Parent Nodes Examples

```
const li = document.querySelector ('li')

li.parentElement // always parent element node

li.parentNodes // the same as the previous one

const liFirst= document.querySelector ('li')

liFirst.closest ('body´) // select any ancestor of the tree
```
### Sibiling Nodes Examples

```
ul.previousElementSibling // Element

ul.previousSibling // Node

ul.nextElementSibling // Element

ul.nextSibling // Node
```
### Query Method

```
const ul= document.body.firstElementChild.nextElementSibling; // gives you the second child of body
```
This can change if the html change

Use them with care, if the traversal relation will still the same

### Styling DOM elements - Classes and Attribute

````
// inline
someElement.style.backgroundColor = 'red' // inline style -> highest specificity

// classes
someElement.className = 'banana' // add or remove classes, I can re-use styles
// cumbersome, be careful not to override previous classes added to the element ❌

someElement.classList.add('banana'); ✅
someElement.classList.remove('banana');

`section.classList.contains // see the classes`

`section.classList.replace`

`section.classList.toggle ('visible´) or invisible // turn on and off the class`

// ids
someElement.id = 'banana'

// some attributes (that are already targetted in the CSS file)
someElement.setAttribute('banana', 'true');
````

### Creating and inserting Elements

#### #1 HTML string

##### `innerHTML`:

````js
// innerHtml

const ol = document.querySelector('ol');

ol.innerHTML = '<li>the only element</>'; // replaces ALL original HTML content
````

Performance and lossing state issues:

````js
ol.innerHTML = ol.innerHTML + '<li>the only element</>'; // re-renders the original content, purple flashing on those elements
// on Chrome dev tools ⚠️

<div id="someId">
  <input>
</div>

const div = document.getElementById('someId')
 div.innerHTML = div.innerHTML + '<p>Something went wrong</p>'; // I loose the input value of the `value` prop
````

Use innerHTML when you want to change or add something to the nodes, without caring about previous data (will be gone)

##### `insertAdjacentHTML`

```js
div.insertAdjacentHTML('beforeend', '<p>Something went wrong</p>'); // doesn't re-render the input field!
// more performant ✅
// but I only set the attributes ⚠️
```

 what if I want to attach and event listener to a button I've just added? 🤔
 I'd have to target it with querySelector and then add the prop, so annoying and poor perfomance ❌

**Search for insertAdjacentHTML on web to se how to write each way of writing the final statement**

#### Creating Node Element + append it

The methods to add the nodes are `append`, appendChild `prepend`, `before`, `after`, `replaceWith`.

```js
// createElement + appendChild

const div = document.getElementById('input-wrapper');

const error = document.createElement('p');

error.textContent = 'Something broke!';

div.appendChild(error);
```

These are better APIs, since I can append a list of Node Elements separated by a coma:

```js
div.append(error, otherNodeHere);
```
It is the shortest version to add

### Nodes are objects!

```js
div.append(error); // put the error on the bottom

div.prepend(error); // moves the element up, it's the same object reference
```

### Create element

`const newLi = document.createElement ('li')`

`newLi.textContent = 'Item 4' // put text on it` 

### Example

`list.lastElementChild.before (newLi) // put the item before last element`

The existing element will change place, it dont copy an paste it

`list.firstElementChild.replaceWith (newLi) // will replace the item`

`secondLi.insertAdjacentElement ('afterend',newLi)`

For this one, search on internet different ways as `afterend`

### Cloning elements = cloning objects

Remember to deep clone nodes to, e.g get the textContent cloned as well:

````js
div.append(error);

const errorClone = error.cloneNode(true);

div.prepend(errorClone);
````
With false, you only copy the item, with true, all the decendents too

#### NodeList vs HTMLCollection

NodeList (querySelectorAll) is more perfomant because it's not updated when inserting **new** Elements there with JS, or deleting them.

HTMLCollection (getElementByTag) reflects new/removed items in the array when targeted with JS

````
const ol = document.querySelector('ol');

const nodeList = document.querySelectorAll('li');

const HTMLElementList = document.getElementsByTagName('li');

const newLi = document.createElement('li');

newLi.textContent = 'added item';

ol.append(newLi);


console.log('nodelist', nodeList); 👈 not updated in terms of new/removed elements

console.log('HTMLElementList', HTMLElementList); 👈 updated! ✅
````

Having a non live array it's maybe not an issue.

`document.getElementsBy(Name, Class, etc, not By) will be a live array

### Removing elements from the DOM

```js
someElement.remove()
```

`list.parentElement.removeChild (list)`is also valid

## More on arrays and iterables

### what are iterable objects?

objects that can be looped using a `for of` loop.

````js
const name = 'Max';

for (letter of myString) { 
	console.log(letter); // prints 'M', 'a', 'x'
}
````

E.g: `NodeList` and `String`.

### what are array-like objects?

E.g: `NodeList` and `String`.

We can access items indexes, and they have a .length property

```js
const name = 'Max';

console.log(name.length); // outputs '3'

console.log(name[0]); outputs 'M'
```

### Creating arrays

```js
const numbers = [1,2,3]; 🚀 best performance

const numbers = Array(1,2,3); // ❓is Array a function here?

const numbers = new Array(1,2,3);

// unexpected behaviour

const numbers = Array(5); // [empty x5]

const numbers = new Array(5); // [empty x5 ] // numbers[0] outputs undefined

const moreNewNumbers = Arry.from ('Hi!'); // create array like objetc, give you back ['H','i','!']

```
### Converting iterables and array-like objects into arrays

```js
// NodeList example
const divsNodeList = document.querySelectorAll('div');
const divArray = Array.from(divsNodeList);

//String example
const name = 'Max';
const nameArray = Array.from(name); // ['M', 'a', 'x'];
```
That way, we could use, e.g .splice() on the converted array.

### Adding and removing elements in arrays

```
.push(element) // 🚀fastest perfomance
.pop() // removes last element // 🚀 fastest perfomance
.shift() // removes the first element => shiftes elements to the left // 🐌 bad performance
.unshift(element) // adds to the begining of the array => // 🐌 shiftes elements to the right
```

```js
// how not to mutate elements ❌

const countries = ['Argentina']
countries[5] = 'Brazil';

console.log(countries); // ['Argentina', empty × 4, 'Brazil']
```
### Splice method: powerful

```js
  const animals = ['bear', 'parrot', 'fish']

// remove
animals.splice(1,1) // ['bear','fish']

// add
animals.splice(1,0, 'donkey');  // ['bear', 'donkey', parrot', 'fish']

// replace
  animals.splice(0,1, 'wale'); // ['wale', 'parrot', 'fish']

// delete all items (1 arg)
animals.splice(1); // ['bear']


// start from the end of array (negative indexes)
animals.splice(-2, 1); // ['bear', 'fish']
```

it returns the deleted elements and mutate the array.
`splice (where to start, how many delete(for all put nothing), add more data)`

**Can put the animal.splice into a constant not to loose the data**

### Slice method

Shallow copies! ⚠️:

`slice() , Array. from() , Object. assign() , and Object. create() ) **do not create deep copies** (instead, they create shallow copies).`

```js
const users = [{name: 'John'}, {name: 'Paul'}];

const shallowUsersClone = users.slice(); // ⚠️ shallow copy created

users[0].name = 'Matthew';

console.log(users, shallowUsersClone); 
// outputs [{name: 👉'Matthew'}, {name: 'Paul'}] [{name: 👉'Matthew'}, {name: 'Paul'}]
```
```js
const animals = ['bear', 'parrot', 'fish']

const fullSlice = animals.slice(); // shallow copy ['bear', 'parrot', 'fish'] 

const smallSlice = animals.slice(0,2); ['bear', 'parrot']

const fromNegativeSlice = animals.slice(-2,2); // always slices to the right! ['parrot', 'fish']]
```
it returns a shallow copy of the slice.

### Concat method

useful for combining to arrays into a **brand new one**! (shallow copy)

```
const wild = ['bison'];

const domestic = ['cat'];

const animals = wild.concat(domestic); // ['bison', 'cat']
```
### IndexOf method

finds the first index of an occurrance.

```
const wildAnimals = ['bison', 'lion'];

const lionIndex = wildAnimals.indexOf('lion');

if (lionIndex !== -1) {
    // and the cat becomes a wild animal!
    wildAnimals[lionIndex] = 'cat';
}
```

Gotcha here: it works fine for primite values, but not for references (objects)

```
const people = [{name: 'Max'}, {name: 'Manu'}];

console.log(people.indexOf({name: 'Max'})); // -1, not found!

// use .find() instead
console.log(people.findIndex(element => element.name === 'Max')); // 0
```

### LastIndexOf method

similar to the above, but starts looking from the end of the array

### Find method

it accepts a callback that is executed for each element.

it returns the first element that matches the returned condition.

⚠️ It doesn't create a copy of objects returned in the array, they're the same references! 😮

````
const people = [{name: 'Max'}, {name: 'Manu'}];

const max = people.find(element=> element.name === 'Max');

max.name = "Rob";

console.log(people); // [{name: 'Rob'}, {name: 'Manu'}]
````

### FindIndex method

```
console.log(people.findIndex(element => element.name === 'Max')); // 0, found
```

### .includes

It's case sensitive

````
console.log(wildAnimals.includes('bison')); //
````

Doesn't work to find object and arrays (reference values)

Works well for primitive values

### .forEach

doesn't return anything

````js
const prices = [1, 2];

const tax = 0.20;

const updatedPrices = [];

prices.forEach(element => updatedPrices.push(element*(1 + tax)));
````

### .map

return a new array (shallow copy!)⚠️
Transform into a new array

````js
// primitive values
const prices = [1, 2];

const tax = 0.20;

const updatedPrices = prices.map(element => element*(1 + tax));

// reference values
const people = [{name: 'Max'}, {name: 'Manu'}];
const updatedPeople = people.map(element => element.name = 'Banana');
console.log (people, updatedPeople); // [{name: 'banana'}, {name: 'banana'}];, [{name: 'banana'}, {name: 'banana'}];

// clone deep, to avoid pushing references to the new array
const updatedPeople = people.map(element => { 
    return {...element, name: 'Banana'};
});
````

with `.reverse`it sort backwards

### .sort

it mutates the array, and returns the mutate one (psss, don't do use that returned value, footgun);

````
// how not to use it ❌

//footgun here 🔫
const sortedAnimals = wildAnimals.sort(); // it returns the same array reference ⚠️

wildAnimals[0] = 'banana';

console.log(sortedAnimals); // ['banana', etc] 🤦‍♂️


// how to use it
wildAnimals.sort();
console.log(wildAnimals) // sorted wild animals

````

it sorts strings alphabetically.

⚠️ If numbers are on the array, they'r converted to a string, and the first string character is used for sorting:

```js
const prices = [10.99, 1.50, 3.75, 5.80];

prices.sort(); // [1.5, 10.99, 3.75, 5.8] 😮


// let's do it properly
prices.sort((a,b) => {
    if (a < b) {
        return -1;
    } else if (a === b) {
        return 0;
    } else {
        return 1
    }
});

// [1.5, 3.75, 5.8, 10.99] ✅
```

### .filter

returns shallow copy array ⚠️

Callback function return true to keep it, false to discard it in the new array

```js
// primitive values
const prices = [10.99, 1.50, 3.75, 5.80];

const filteredPrices = prices.filter(element => element < 10); // [1.5, 3.75, 5.8]
```

```js
 // reference values
// how not to do it ❌
 const people = [{name: 'Max'}, {name: 'Manu'}];

const filteredPeople = people.filter(element => element.name === 'Max');

filteredPeople[0].name = 'banana';

console.log(people); // [{name: 'banana'}, {name: 'Manu'}];
```

````
✅ use a .forEach and push a cloned object to an array insted OR .map and return a cloned object
````

### .reduce

reduce an array into a single value! e.g sum numbers in an array:


````js
const numbers = [1,2,3];

const sum = numbers.reduce((prevValue, currentValue) => prevValue + currentValue, 0);
````

0 is the prevValue in the first iteration, can be changed

easier than initializing variable and using .forEach to add numbers!

prevValue is `undefined` in the first iteration of not specified.

### Chaining methods 

Step by step
```js
const originalArray = [{price: 10.99}, {price: 5.99}, {price: 29.99}];
const transformedArray = originalArray.map(obj => obj.price); // produces [10.99, 5.99, 29.99]
const sum = transformedArray.reduce((sumVal, curVal) => sumVal + curVal, 0); // => 46.97
```
Skiping map step
```js
const originalArray = [{price: 10.99}, {price: 5.99}, {price: 29.99}];
const sum = originalArray.reduce((sumVal, curVal) => sumVal + curVal.price, 0); // => 46.97
```
Chaining the steps

```js
const originalArray = [{price: 10.99}, {price: 5.99}, {price: 29.99}];
const sum = originalArray.map(obj => obj.price)
    .reduce((sumVal, curVal) => sumVal + curVal, 0); // => 46.97
```

### .split and .join

````js
const data = 'edinburgh;10';

const dataArray = data.split(';'); // ['edinburgh', '10']

const joinedData = dataArray.join(':'); // 'edinburgh:10'
````

.join will convert everything into a string.

if the `let` or `const` is missing:
````js
joinedData = dataArray.join(':'); // 'edinburgh:10' // window.joinedData is created!
````

### ...operator

example of Math.min()

```
const numbers = [1,2,3];
const min = Math.min(...numbers);// same as (1,2,3)
```

```
how not to use it! ❌
const numbersClone = ...numbers
```

⚠️ only deep clone things you plan to change on the newly created array.

### array Destructuring

Create variables with the information of each element of the array

````js
const data = ['max', `schwarz`];

const [name, surname] = data; // name = 'max', surname = 'schwarz', rest = [ "germany", "34" ]
````

**If you put one more variable, and you have a longuer array, it would make an array of the forgotten elements**

### Arrays, sets and maps

Sets have no guaranteed order and there can't be repeated values. Useful for storing unique things. Things can't be accessed with the index, but I can check if things are present. It has some array protoype methods available. It's iterable

Maps have the order guaranteed, and key value pairs are stored; keys can be anything (even objects). There can't be duplication of key 's values. Values are accessed with the key. Some methods are available. It's iterable.

### Sets: great for uniqueness

```js
const mySet = new Set(['hi', 'there']);

mySet.add('man'); // Set(3) [ "hi", "there", "man" ]

mySet.add('man'); // Set(3) [ "hi", "there", "man" ] // it doesn't throw error

mySet.delete('man'); // Set [ "hi", "there" ]

mySet.delete('inexistant'); // Set [ "hi", "there" ] // it doesn't throw error

const isHiPresent = mySet.has('hi'); // true

for (entrie of mySet.entries()) {
    console.log(entrie); // Array [ "hi", "hi" ] Array [ "there", "there" ]
}

// entries not very handy, they're more built for maps

// let's use .values() for looping instead
for (value of mySet.values()) {
    console.log(value); // hi there
}
```

### Maps: great for not bloating objects used heavily in the app

```js
const animal1 = {name: 'negrito'};
const animal2 = {name: 'toto'}

const myMap = new Map([[animal1, {favouriteFood: 'fish'}]]); // Map { {…} → {…} }

myMap.set(animal2, {favouriteFood: 'meat'}); // Map { {…} → {…}, {…} → {…} }

const animal1Food = myMap.get(animal1); //Object { favouriteFood: "fish" }

for (entrie of myMap.entries()) {
    console.log(entrie); // Array [ {…}, {…} ] Array [ {…}, {…} ]
}

for (key of myMap.keys()) {
    console.log(key); // Object { name: "negrito" } Object { name: "negrito" }
}

for (value of myMap.values()) {
    console.log(value); // { favouriteFood: "fish" } { favouriteFood: "meat" }
}
```

### Weak Set and Weak Map: memory management!

only objects and arrays can be stored there! (no primitive values)

they let **garbage collection** of objects that points to null objects. Very efficient! 

No need to delete those object pointers from arrays when making the object values null somewhere else in the app!

```js
let user1 = {name: 'Max'}
let user2 = {name: 'Manu'}

const users = new WeakSet([user1, user2]);

user1 = null; // the browser at some point will remove this item from the users WeakSet
```

WeakMap doesn't have .size prop or entries method, because the gargage collection can happen anytime and affect the size and hence, the number of items to be iterated over.

````js
let animal1 = {name: 'negrito'};

const myMap = new Map([[animal1, {favouriteFood: 'fish'}]]); // this item will garbage collected at some point after animal1 is set to null

animal1 = null;
````

### Short syntax for returning an object

Use parenteshis to indicate that the return is there otherwise, the body of the functions becomes `number: element`, not very useful!

````
const numbersInObjects = numbers.map(element => 👉( {number: element}));
````

The following resources may be helpful.

-   Thorough Array on MDN (also check the linked methods on the left on that page): [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

## More on objects

### Adding/overriding new props after object creation

````js
const animal = {
    name: 'negrito'
}

console.log(animal.age); // undefined, doesn't throw an error

animal.age = 20; // {name: 'negrito', age: 30};
````

### Deleting props

````js
delete animal.age;
````

### Resetting props

````js
animal.age = undefined // ❌ bad practice! age will still be an active prop though (logged in the console)

animal.age = null ✅// to reset it's value, cleaner, age will still be an active prop though (logged in the console)
````

### Key naming

anything that is used as a variable name can be used as a variable key + strings + positive numbers

Key values are coherced into strings when the object is created.

```js
const first-name = 'tebi'; // Uncaught SyntaxError: Missing initializer in const declaration
```

```js
  const person = {
    'first-name': 'tebi',
    age: 33,
    1: 'positive numbers work'
  }

person['first-name']; // 'tebi'
person.first name; // Uncaught SyntaxError: Unexpected identifier 'name'

person.age; // 33
person['age']; 
person[age]; ❌ // Uncaught ReferenceError: age is not defined at <anonymous>:1:8

person.1; // Uncaught SyntaxError: Unexpected number
person[1]; // 'positive numbers work'
person['1'] // 'positive numbers work'
```

### Order of keys:

If there are only numbers, the order is changed to `ascending`.

If there are at least one string, then the order numbers come first, and then the non numbers order is kept.

````js
// strange example, only for demo purposes
const numbers = {
	5: 'number 5!',
  1: 'number 1'
} // {1: 'number 1', 5: 'number 5!'}

const numbersAndOthers = {
  'hello': 'hello there!',
  'aaa': 'aaaaaaa',
  1: 'number 1'
} // {1: 'number 1', hello: 'hello there!', aaa: 'aaaaaaa'}
````

⚠️ Remember that the console.log when we **expand objects**, always sort things alpabetically. 

### Interacting with the DOM

The DOM Nodes offer both keys!

````js
li.style['background-color'] = 'red'; // ✅
// OR
li.style.backgroundColor = 'red'; // ✅
````

### Dynamically accessing key value pairs

````js
  const person = {
    'first-name': 'tebi',
    age: 33,
    1: 'positive numbers work'
  }

for (const key in person) {
	console.log(person.key) // ❌ undefined x 3, there's no such `key` key
}

for (const key in person) {
	console.log(person[key]) // ✅ // 'tebi', 33, 'positive numbers work'
}
````

### Dynamically defining key value pairs

```js
 const userSelectedKey1 = 'someKey';

const animal = {
    name: 'negrito',
  	[userSelectedKey1]: 'someValue'
}

const userSelectedKey2 = 'customKey';

animal[userSelectedKey2] = 'someOtherValue';

console.log(animal); // {name: 'negrito', someKey: 'someValue', customKey: 'someOtherValue'}
```

### Rendering Elements based on objects project

`renderMovies` clears the `ul` children. It's not ideal. It would be better to keep each movie `li` , and append the new one using the function `addMovie`, but it's done this way to save up some time.

The downside is that each time a renderMovies is called, the entire children are wipped out.

the `renderMovies()` function takes a parameter called filter. `renderMovies(filter = '')`

That was smart, because I didn't need to arrays in the global scope: `movies` and `filteredMovies` ❌, instead, the filtered array was just in the scope of the renderMovies function.

### For in loops and Outputing Dinamic Properties

If you want to access properties that are defined with the [] form, you can use a for loop:

````js
movies.forEach ((movie) => {
 const movieEl= document.createElement('li');
 let text = movie.info.title + '-';
 for (const key in movie.info) {
	 if (key !== 'title' in movie info) { //title with comas to access properties, exclude fixed property 
		text= text + `${key}:${movie.info[key]};
	 }
 }
 movieEl.textContent= text;
 movieList.append (movieEl);
});
````

### Filter functionality

In the function, put the variable like this `(filter='')` to preset it to nun, but you can put the filter of word you want

In the string, use the next funtionality:

```` js
const filteredMovies = !filter 
	? movies
	:  movies.filter (movie => movie.info.title.includes(filter))
````
Then use filteredMovies to show the filter

### Chaining methods

````js
Math.random().toString()
````

everything has that .toString() method in JS


### Spread Operator

````js
const person 2= {...person 1}
````

Make a deep copy of the first object

**Careful, if it is arrays inside, the ... don´t make a deep copy of the array**

If you want to make a real copy you have to:

````js
const person2= {...person1, hobbies: [...person1.hobbies]}
````

### Assign

Another way of coping object

````js
const person1 = {'Max'};

const person2 = Object.assign ({},person1);
````

With the {} inside assign you create a deep copy

### Object destructuring

Imagine you reference `person.name` a lot of times in your code. Wouldn't be better to create a variable for that?
````js
const person = {name: 'tebi', surname: 'munch', hobbies: ['fishing', 'coding']};

// const name = person.name OR
const {name} = person; //✅

// const customName = person.name OR
const { name: customName } = person; //✅

// const hobbies = person.hobbies; OR
const {hobbies} = person; //✅ d oesn't deep clone

hobbies.push('cooking');

console.log(person); // Object { name: "tebi", surname: "munch", hobbies: (3) […] }
````

### Check for property existance

When assigning variables (checks on the right hand side of the equal operator)

````js
const person = {name: 'tebi', surname: 'munch', hobbies: ['fishing', 'coding']};

const unexistingKey = person.places[0]; // ❌throws error, stops code execution
// Uncaught TypeError: person.places is undefined

const unexistingkey1  = person?.places?.[0]; // ✅undefined

const firstHobbie = person?.hobbies?.[0]; // fishing
````



when we need to run blocks of code conditionally

```js
const person = {name: 'tebi', surname: 'munch', hobbies: ['fishing', 'coding']};

if ('name' in person) {
  console.log(`person has a 'name' key!`);
}

if (person.name !== undefined) {
  console.log(`person has a 'name' key!`);
}
```

### This keyword

When using `this` inside functions, `this` refers to the thing calling that function.

Don't use arrow functions when using `this`!

````js
const person = {
  name: 'tebi', 
  getFormattedName: function () { // ✅ function keyword
    return this.name.toLocaleUpperCase();
  }
};

// OR

const person = {
  name: 'tebi', 
  getFormattedName() {  // it doesn use the function keyword, more in the next modules!
    return this.name.toLocaleUpperCase() 
  } 
};

console.log(person.getFormattedName()); // `TEBI`
````

who is calling `getFormattedName`? `person`, because it's in front of the function call: `person.` 

### This became the window object!!

```js
const person = {
  name: 'tebi', 
  getFormattedName () { 
    debugger;
    return this.name.toLocaleUpperCase() } 
};

const { getFormattedName } = person;

// here the this keyword inside the object refers to the 👉 window object!!
console.log(getFormattedName()); 
```

Who called the function? no one! (well, the global execution context to be precise) there wasn't anything before `getFormattedName()` when calling it. So the window object is what the `this` keyword will default to, when using `non-strict` mode. 

If we use `strict` mode:
```js
👉 "use strict"
const person = {
  name: 'tebi', 
  getFormattedName () { 
    debugger;
    return this.name.toLocaleUpperCase() } 
};

// same as const getFormattedName = person.getFormattedName;
const { getFormattedName } = person;

// here the this keyword is 👉 `undefined`
console.log(getFormattedName()); 
```

### Let's restructure + bind the function

````js
const person = {
  name: 'tebi', 
  getFormattedName () { 
    debugger;
    return this.name.toLocaleUpperCase() } 
};

let { getFormattedName } = person;

// I can't do getFormattedName.bind(person)(), I need to do in 2 steps ❌
getFormattedName = getFormattedName.bind(person);

// here the this keyword inside the object refers to the 👉 window object!!
console.log(getFormattedName()); // throws error
````

I had to bind and call the function in two steps, because I can't inmediately execute the function.

.bind() is helpful for telling the function what the `this` keyword refers to inside it, when that function is executed in the future upon an event.

The best option to configure the context when we're executing the function straight away is `.call`

```js
.bind // prepares the function
.call OR .apply // prepares the function + executes it straight away
```

```js
const person = {
  name: 'tebi', 
  getFormattedName () { 
    debugger;
    return this.name.toLocaleUpperCase() } 
};

const { getFormattedName } = person;

// shorter than the previous example
// prepare + call on one line! ✅
console.log(getFormattedName.call(person)); 
```

Difference between .**call** and .**apply**? .call takes the prepended args separated with **commas**, with .apply takes them as an **array**

### Event listners and the this value

````js
const li = document.querySelector('li');

// using the function keyword
// the browser binds the function to the Element that has the event listener attached.
li.addEventListener('click', function () {
  console.log(this); // li element
});
````

### Arrow function and the this keyword

````js
const li = document.querySelector('li');

// using arrow function
li.addEventListener('click', () => {
  console.log(this); // Window
});
````

Arrow functions don't know this! 😅

the `this` value is the same as the one outside the function. An object is not a place where you can write the `this` keyword, so that doesn't count. See example below:

````js
this // window object

// using arrow function
li.addEventListener('click', () => {
  console.log(this); // Window object
});

// next place here
this

const person = {
  name: 'tebi',
  this ❌
  getFormattedName: () => {
    console.log(this); // Window // I can't type `this` inside an object, doesn;t count
    // the next place would be outside the object 😮
    return this.name.toLocaleUpperCase()
  }
};

const { getFormattedName } = person;

console.log(getFormattedName()); // it doesn't work!❌

````

Conclusion: using arrow functions makes the `what thing called the function` rule invalid, same with `use strict` mode. We can get rid of unpleasant side effects!

In other words, using arrow functions doesn't let JS to bind it when called.

Remember React, when using methods defined with arrow functions, I didn;t need to bind the methods before the constructor! ❓

It will be useful to use arrow functions when creating objects with Classes.

If "use strict" is used, then `this` is not `undefined` is still the window object

### When an arrow function can be useful

```js
// arrow function callback
const member = {
  teamName: 'Blue rays',
  memberNames: ['Max', 'Manu'],
  printNames(){
    this.memberNames.forEach(person => console.log(`${person}--${this.teamName}`)); // arrow function as the forEach callback. `this` is the same as the one inside the printNames method, which refers to the `member` object
  }
}

member.printNames(); // Max--Blue rays Manu--Blue rays ✅
```

````js
// function keyword callback
const member = {
  teamName: 'Blue rays',
  memberNames: ['Max', 'Manu'],
  printNames(){
    this.memberNames.forEach(function(person){ 
      console.log(this); // window object, no one's calling the callback function (well, the browser)
      // is called by forEach function in our behalf, we don't call it () ourselves
      console.log(`${person}--${this.teamName}`)
    });
  }
}

member.printNames(); // Max--undefined Manu--undefined ❌
````

### Quiz

what's the purpose of using `this` inside non-arrow methods? To provide access to the thing that called the method

### How to change props with what I know so far

````js
const member = {
  teamName: 'Blue rays',
  changeTeamName(newName){
    this.teamName =  newName;
  }
}

member.changeTeamName('Sparks');

console.log(member);
````

### Getter and setters

we can run some logic (e.g perform checks) before adding/changing/reading a prop of an object.

Kind of security guards to enter, do things inside and exit the object

we can have a propr with no setter, so it's a read only prop! that's neat

````js
const member = {
  _teamName: 'Blue rays', // props with _ are not supposed to be accessed directly
  get teamName(){
    return this._teamName.toUpperCase();
  },
  set teamName(value){
    if(value.includes('p')){
      console.log('sorry, letter p is not allowed')
    } else {
      this._teamName = value;
    }
  }
  
}


console.log(member._teamName); // Blue rays ❌ bad practice
// ❌ member._teamName = 'something' bad practice
console.log(member.teamName); // getter fired, prints BLUE RAYS

member.teamName = 'pepe'; // setter fired , prints `sorry, letter p is not allowed`

member.teamName = 'Argentina'; // setter fired

console.log(member.teamName); // ARGENTINA

console.log(Object.keys(member)); // ['_teamName', 'teamName']
````

The following resources may be helpful.

-   More on the `this` keyword (MDN): [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)

## Objects oriented Programming

### OOP programming

so far, to render a list of products into a page with **functional programming**, we'd do:
````js
// function to fetch an API
// function to iterate over the products and append it as a children
````

Simplified **functional programming** approach

````js
const productList = [{},{}];

const renderProductList = () => {
	// create a ul element
	// iterate over products and append one by one the the ul element
	// append the ul element to another element already in the HTML
}

renderProductList();
````

OOP approach

````js
const ProductList = {
	products: [{},{}],
	render() {
		// create a ul element
		// iterate over products 👉(this.products) and append one by one the the ul element
		// append the ul element to another element already in the HTML
	}
}

ProductList.render();
````

With OOP, we can have a class `Products`  that when instantiated, return  objects that have the list of products, a method to render it. Same for a class `Product` that holds props of the products and a method to render it (so that can be used inside the Products class when interating over the array of products).

### Classes

```
class 👉Dog = {
	sound 👉= 'wooof';👈
}
```
The convention is to use first letter capitalized.

equal signs and commas are used

````js
class Product {
  constructor(title, price, description) {
    this.title = title;
    this.price = price;
    this.description = description;
  }
}

const product1 = new Product('Computer', 1000, 'a really nice computer');

console.log(product1);// Product {title: 'Computer', price: 1000, description: 'a really nice computer'}
// Prototype -> constructor: class Product

// TS sugar
class Product {
  title;
  price;
  description;
  constructor( private title, private, private description){}
}  
````

the `constructor` method is autmatically called by JS when using the `new` keyword.

We use classes to create objects that have logic (methods in it).

We wouldn't use a class to create objects that just hold props , e.g { sound: 'woof'}

In Max's example, Product can hold some props and a method to render it (e.g under /product?id=xx page);

In the end Macx decided to use a class **Product** to just hold props, and then **ProductItem** that has the props + a render method

Off topic example using an object from an API:

````js
class Product {
  title = 'Default'; // ❌ Doesn't make sense in this case. We can define fields before the constructor
  constructor(title, price, description) { 
    this.title = title; // overrides default value
    this.price = price;
    this.description = description;
  }
  reducePrice(){
    this.price = this.price * 0.8;
  }
}

const productFromApi = {
  title: 'computer',
  price: 1000,
  description: 'a nice computer'
}

const product = new Product(...Object.values(productFromApi)); 

console.log(product); // Product {title: 'computer', price: 1000, description: 'a nice computer'}
````

```js
class ProductV2 {
  constructor(product){ // accepts the object, much more easier
    this.title = product.title;
    this.price = product.price
    this.description = product.description
  }
  reducePrice(){
    this.price = this.price * 0.8;
  }
  render(){ //return li node}
}
  
const product = new Product(productFromApi);
```
The order of classes doesn't matter.

You can use classes into another classes even if the class is defined after it

````js
class ProductList { products = [new Product(someArgs)]}
class Product{} // ✅ defined before executing the parent class
const products  = new ProductList();

````

### Max's classes

````js
class Products {} // holds the products
class ProductItem {} // holds the props + a render method that returns a li node element
class ProductList {} // holds the products list + a render method that appens ul to the DOM
````

he separated Products + ProductItem into 2 lists. I'd just merge them. I like holding data and methods to render that to the DOM altogether.

### How to update the cart UI when an item is added to it?

```js
class Cart {
	items = [];
	
	addItem(product){
		items.push(product); // I could use a setter instead, and assign a new array
    // let's update the DOM
		👉dynamicMarkupNode.innerHTML = <<div>Total: 1<div>;
	}
	
	render(){
		some external markup
    // let's keep the Node as a prop
		const 👉this.dynamicMarkupNode = // some Node with <div>Total: 0<div>;
		return all the markup // used by a parent class Shop that renders all parts of the app
	}
}
```
### Static props, fields and methods

A way to encapsulate all code on classes:

```js
// this was the only code of the app outside a class
const shop = new Shop();
shop.render
```

````js
// let's put inside a box! 📦
class App {
	static init(){
		const shop = new Shop();
		shop.render();
	}
}

App.init();
````

### How to add products to the cart?

⚠️ **I need just one instance of the Cart class**, and then using all over the app. But where do I store that instance?

In a class!!

So the idea is that there is no global variables outside classes holding that, as I'd have with functional programming.

```js
//FP way of thinking ❌
const 👉cart = new Cart();

// then reuse that cart instance in classes
class Product {
	constructor(👉cart){}
	// some methods that pushed to the 👉cart instance
}
```

```js
// OOP what of thinking ✅

class Product {
  App.cart.addItem(product);
}

class App {
  static cart = new Cart // OR
  
  static someMethod(){
    //some logic
    this.cart = new Cart
  }
}
```

So a static field is really usefull for sharing a class instance!

````js
// FP concrete example ❌
class Cart {
  items = [];  
  addItem(product) { 
    this.items.push(product);
  }  
}

class ProductList {
    products = ['banana', 'bread', 'butter'];

    constructor (cartInstance) { ❌
        this.cartInstance = cartInstance;
    }
    pushRandomItem() {
        this.cartInstance.addItem(this.products[Math.round(Math.random())]);
    }
}

const cart = new Cart;

const productList = new ProductList(cart);
````

The above way is not very helpful ❌. I don't want to use constructors 🤔

I can keep those classes instances as static fields in a class, and access them everywhere without constructors!



````js
// OOP concrete example ✅

class Cart {
    items = [];  
    addItem(product) { 
      this.items.push(product);
    }  
  }
  
  class ProductList {
      products = ['banana', 'bread', 'butter'];
      pushRandomItem() {
          👉 App.cart.addItem(this.products[Math.round(Math.random())]); // I could turn this into a static method as well?
      }
  }
  
  class Shop {
      render(){
        this.cart = new Cart;
        // some more logic here
      }
  }
  
  class App {
      // static cart; // 💡this can be ommitted

      static init(){
              const shop = new Shop(); 
              this.cart = shop.cart; // 💡😮 it creates a static field, because we're inside a static method
              shop.render();
      }

      static playWithClasses(){
          const productList = new ProductList;
          productList.pushRandomItem();
          productList.pushRandomItem();
          console.log(App.cart.items);
      }
  }

  App.init();
  App.playWithClasses();
````



To recap, static methods and props are good for sharing things across the app.

Remember! class instances are objects, so I can do object destructuring for example:

```js
class Person {
	constructor(age){
		this.age = age;
	}
}

const { age } = new Person(35);

console.log(age); // logs 35
```

### When to use classes?

when we plan to create the same object holding props and logic multiple times.

When we have some methods(logic)

### When to use object literals?

when there's no logic, and we need to have the object create once or so. It performs better than using classes to create it, but that perfomance difference can be seen if we create thousands/millions of objects

### Setters and getters

we don't use them like this: ❌

````js
class Cart {
	items = []; // naming colision here 💥!!
	set items(newArray){ //❌
		debugger; //never runs
        this.items = newArray;
	}
}

class App {
	static playWithCart(){
		this.cart = new Cart;
		this.cart.items = ['banana', 'bread']; // ⚠️doesn't trigger the setter, it just re-assigns the prop directly
	}
}
````



They can be syntactic sugar to run some logic:

````js
class Cart {
    items = [];
      👉set cartItems(itemsArray){
          this.items = itemsArray // reassigns the prop to a new array
      // more logic here! like updating the DOM Node displaying the total price
      console.log('running the setter!')
      }
  }
  
  class App {
      static playWithCart(){
          this.cart = new Cart;
          this.cart.👉cartItems = ['banana', 'bread']; // ✅ triggers the setter
      console.log(this.cart.items)
      }
  }

  App.playWithCart();
````

Please note there's no such cartItems prop at all inside the class, but calling the setter syntax is like assigning that prop.

**Without** a setter:

```js
class Cart {
    items = [];
      👉setCartItems(itemsArray){
          this.items = itemsArray // reassigns the prop to a new array
      // more logic here! like updating the DOM Node displaying the total price
      console.log('running the setter!')
      }
  }
  
  class App {
      static playWithCart(){
          this.cart = new Cart;
          this.cart.👉setCartItems(['banana', 'bread']); // parenthesis syntax
      console.log(this.cart.items)
      }
  }

  App.playWithCart();
```

An example of getters:

```js
class Cart {
    items = [];
      set cartItems(itemsArray){
          this.items = itemsArray // reassigns the prop to a new array
      this.someNode.innerHTML = `<div>Total${this.👉total}</div>`; // 💡triggers the `total` getter
      console.log('running the setter!')
      }
  
  		👉get total(){
        return items.reduce((prevValue, currValue) => prevVal + currValue.price, 0);
      }
  }
  
  class App {
      static playWithCart(){
          this.cart = new Cart;
          this.cart.cartItems = [{ name: 'banana', price: 10} , { name: 'bread', price: 20 }];
      console.log(this.cart.items);
      console.log(this.cart.total);  
      }
  }

  App.playWithCart();
```

So, as we can see, OOP does't use much `const` and `let`, but uses `this` to store values, and they'r scoped to the objects, so that's really neat, we'r not polluting the global space.

### Event listeners

Two options to fix it: `.bind` the reference, or use arrow syntax

```js
class ProductItem {
  constructor(product){
    this.product = product;
  }
  someFunction() {
    console.log(this.product) // ❌ undefined. This refers to the event object! who called the event listener? JS
    console.log(this); // document object
  }
	render() {
    document.addEventListener('click', this.someFunction);
  }
}

Option #1: Bind the listener
class ProductItem {
  constructor(product){
    this.product = product;
  }
  someFunction() {
    console.log(this.product) // logs 'banana' !
    console.log(this); // logs ProductItem
  }
	render() {
    document.addEventListener('click', this.someFunction.👉bind(this)); // it works as longs as `render` is called as product1.render()
  }
}

// Option 2#: use arrow syntax to define the listener
class ProductItem {
  constructor(product){
    this.product = product;
  }
  // `this` (I can type it at the class level, so that's why arrow function works well here)
  someFunction 👉= () => {
    console.log(this.product) // logs 'banana' !
    console.log(this); // logs ProductItem
  }
	render() {
    document.addEventListener('click', this.someFunction);
  }
}

const product1 = new ProductItem('banana');

product1.render();
```

### Inheritance

what if two classes have a method that does more or less the same?

````js
class someClass {
	render(){
		// creates Node // shared code ✅
		// appends some stuff to it (differs from class to class) ❌
    // appends node to an anchor ✅
		// return Node // shared code ✅
	}
}
````

Example:

````js
class Component {
  constructor(anchorElementId){
    this.anchorElementId = anchorElementId;
  }
  
  createNode(tag, classes, attributes){
		...
    return someNode;
  }
}
````

```js
class Cart extends Component {
	render(){
		const node = this.createNode('section', 'cart');
		// add some content to the node
		return node;
	}
}
```



Extended example:
````js
class Component {
  constructor(renderHookId) {
    this.hookId = renderHookId;
  }

  createRootElement(tag, cssClasses, attributes) {
    // 1- Node creation
    const rootElement = document.createElement(tag);
    if (cssClasses) {
      rootElement.className = cssClasses;
    }
    if (attributes && attributes.length > 0) {
      for (const attr of attributes) {
        rootElement.setAttribute(attr.name, attr.value);
      }
    }
    // 2 - Node appended
    document.getElementById(this.hookId).append(rootElement);
    
    //3-  Node returned
    return rootElement; // it returns the node to append things to it later on
  }
}

class ShoppingCart extends Component {
  ...
  render() {
    // get the node using the inherited parent method
    const cartEl = this.createRootElement('section', 'cart');
    // add some content to the node
    cartEl.innerHTML = `
      <h2>Total: \$${0}</h2>
      <button>Order Now!</button>
    `;
    // store some of the Node displaying the total, to be updated when a new item is added to the cart
    this.totalOutput = cartEl.querySelector('h2');
  }
}
````

With `extend` you append the father class to the class you are working

If you dont use a constructor, it will actomatically use the one on the father structure, 
If you need to work with a constructor made in other class use this:
```` js
constructor (renderHookId) {
	super (renderHookId);
	}
````

````js
class Rectangle {
  constructor(height, width) {
    this.name = "Rectangle";
    this.height = height;
    this.width = width;
  }
  sayName() {
    console.log("Hi, I am a ", this.name + ".");
  }
  get area() {
    return this.height * this.width;
  }
  set area(value) {
    this.height = this.width = Math.sqrt(value);
  }
}

class Square extends Rectangle {
  constructor(length) {
    this.height; // ReferenceError, super necesita ser llamado primero!

    // Aquí, llama al constructor de la clase padre con las longitudes
    // previstas para el ancho y la altura de Rectangle
    super(length, length);

    // Nota: En las clases derivadas, se debe llamar a super() antes de
    // poder usar 'this'. Salir de esto provocará un error de referencia.
    this.name = "Square";
  }
}
````

### Constructors of parent and the extended class

```js
class Parent {
	constructor(someArgs){} // get's called ✅
}

class Child extends Parent {
  // no constructor here
}

const newChild = new Child(someArgs);
```

```js
class Parent {
	constructor(someArgs){} // doesn't get called! ❌
}

class Child extends Parent {
  	constructor(someArgs){} // get's called ✅
}

const newChild = new Child(someArgs);
```

How to solve this problem?

````js
class Parent {
	constructor(someArgs){} // doesn't get called second! ✅
}

class Child extends Parent {
  	constructor(someArgs){ // get's called first ✅
  		👉 super(someArgs);
      // I can now access this, as the object has been initialized
      this.something = something;
      //etc
  	} 
}

const newChild = new Child(someArgs);
````



An example:

```js
class Parent {
    constructor(sound){ // gets called ✅
        this.sound = sound;
    }
    makeSound(){
        console.log(this.sound);
    }
}

class Child extends Parent { // no contructor here
}

const newChild = new Child('wohoo!');
newChild.makeSound(); // prints wohoo! 
```

if I add a contructor to `Child`, I get this error:
````js
// app.js:12 Uncaught ReferenceError: Must call super constructor in derived class before accessing 'this' or returning from derived constructor
````

```js
class Parent {
    constructor(sound){
        this.sound = sound;
    }
    makeSound(){
        console.log(this.sound);
    }
}

class Child extends Parent { 
	 constructor(sound, a, b, c,etc){
        super(sound);
        // some other logic here, assigning new props using a,b,c
    }
}

const newChild = new Child('wohoo!', a,b,c ,etc);
newChild.makeSound(); // prints wohoo!🎉
```

When not using TS, a way to ensure a function get objects of the expected shape in a method, is to generate objects using a class for it and pass it to the method.

TS is much better, as we'll find the error before the JS runs in the browser.

### Refactoring rendering methods

classes with the render method can now extend the Component class, and use that logic

`ProductList` and `Cart` are appended to and Node element with id `app`, so they'r the app's top 2 level components.

ProductList needs to be rendered before ProductItem, because ProductItems needs the `ul` element to be added to DOM when in renders.

the original render methods used to return the Node element in order to be appended by the code calling the .render() method. But now, the parent .render() method appends it, so no need to return it anymore.

### Let's add some code in the parent constructors

```js
class Shop {
  render() {
    this.cart = new ShoppingCart('app');
    this.cart.render(); ❌ // let's move both calls to the sub-class constructor
    this.productList = new ProductList('app');
    this.productList.render(); ❌
  }
}

class ProductList extends Component {
    // add content to the node
    for (const prod of this.products) {
      const productItem = new ProductItem(prod, 'product-list');
      productItem.render(); ❌
    }
  }
}

```

```js
// how not to do it ❌
class ShoppingCart extends Component {
	  constructor(renderHookId) {
    super(renderHookId);
    this.render();
  }
}
```

```js
// how to do it ✅

 class Component {
  constructor(renderHookId) {
    this.hookId = renderHookId;
    this.render(); // who called the constructor of this function? the sub-class when instantiated with the `new` keyword. 1 object is being created, and that's an object based on the sub-class (+parent).
  }
   
   // I can ommit having a render method in this class
   // or add it as an empty method, like this: render(){}
   // then, it get's 👉overriden by the render method of the sub-class

  createRootElement(tag, cssClasses, attributes) {
    const rootElement = document.createElement(tag);
    if (cssClasses) {
      rootElement.className = cssClasses;
    }
    if (attributes && attributes.length > 0) {
      for (const attr of attributes) {
        rootElement.setAttribute(attr.name, attr.value);
      }
    }
    document.getElementById(this.hookId).append(rootElement);
    return rootElement;
  }
}
  }
}
```



```js
// much more simpler than before
class Shop extends Component{
  constructor(){
    super();
  }
  render() {
    this.cart = new ShoppingCart('app');
    new ProductList('app');
  }
}

//OR
class Shop { // it's an overkill to extend Component here, for just self-rendering functionality
  constructor(){
    this.render()
  }
  render() {
    this.cart = new ShoppingCart('app');
    new ProductList('app');
  }
}
```

now, classes rendered themselves when instantiated, that's neat!

#### Golden rule: `this` inside the parent constructor referes to the created object from the sub-class

Till Boolean tricks with logical operators!

### Constructor execution, Order & this

````js
// I get the error: this.products is not iterable

class ProductList extends Component {

  products = [
    new Product(
      'A Pillow',
      'https://www.maxpixel.net/static/photo/2x/Soft-Pillow-Green-Decoration-Deco-Snuggle-1241878.jpg',
      'A soft pillow!',
      19.99
    ),
    new Product(
      'A Carpet',
      'https://upload.wikimedia.org/wikipedia/commons/thumb/7/71/Ardabil_Carpet.jpg/397px-Ardabil_Carpet.jpg',
      'A carpet which you might like - or not.',
      89.99
    )
  ];

  constructor(renderHookId) {
    super(renderHookId);
  }

  render() {
    // create the node element and append it
    const prodListdEl = this.createRootElement('ul', 'product-list', [new ElementAttribute('id', 'product-list')]);

    // add content to the node
    for (const prod of this.products) { // `this` only has the parent class props at this point
      const productItem = new ProductItem(prod, 'product-list');
    }
  }
}
````



````js
class Component {
  constructor(renderHookId) {
    this.hookId = renderHookId;
    this.render(); // get's called before the sub-class constructor finishes running, so the fields to be converted to props in the sub-class are not ready yet (not initialized), e.g products
  }

  createRootElement(tag, cssClasses, attributes) {
    const rootElement = document.createElement(tag);
    if (cssClasses) {
      rootElement.className = cssClasses;
    }
    if (attributes && attributes.length > 0) {
      for (const attr of attributes) {
        rootElement.setAttribute(attr.name, attr.value);
      }
    }
    document.getElementById(this.hookId).append(rootElement);
    return rootElement;
  }
}
````



2 approaches to fix this:

1. fetch products, and after they're set, render them + add some if check to only render them if set

```js
class ProductList extends Component {

  constructor(renderHookId) {
    super(renderHookId);
    👉this.fetchProducts();
  }

  fetchProducts(){
    // some call to an API
    this.products = [
      new Product(
        'A Pillow',
        'https://www.maxpixel.net/static/photo/2x/Soft-Pillow-Green-Decoration-Deco-Snuggle-1241878.jpg',
        'A soft pillow!',
        19.99
      ),
      new Product(
        'A Carpet',
        'https://upload.wikimedia.org/wikipedia/commons/thumb/7/71/Ardabil_Carpet.jpg/397px-Ardabil_Carpet.jpg',
        'A carpet which you might like - or not.',
        89.99
      )
    ];

    👉this.renderProducts()

  }

  👉renderProducts(){
     // add content to the node
     for (const prod of this.products) {
      const productItem = new ProductItem(prod, 'product-list');
    }
  }

  render() {
    // create the node element and append it
    const prodListdEl = this.createRootElement('ul', 'product-list', [new ElementAttribute('id', 'product-list')]);
    👉if (this.products && this.products.length > 0) {
      this.renderProducts();
    }
  }
}
```



2. Modify the parent class to accept a boolean to decide to render or not when instantiated, and call this.render manually inside the sub-class constructor.

   ````js
   class Component {
     constructor(renderHookId, 👉shouldRender = true) {
       this.hookId = renderHookId;
       👉if (shouldRender){
         this.render();
       }
     }
     //etc
   }
   
   
   
   class ProductItem extends Component{
     constructor(product, renderHookId) {
       👉super(renderHookId, false);
       👉this.product = product;
       👉this.render();
     }
   
     render() {
       const prodEl = this.createRootElement('li', 'product-item');
     
       prodEl.innerHTML = `
           <div>
             <img src="${this.product.imageUrl}" alt="${this.product.title}" >
             <div class="product-item__content">
               <h2>${this.product.title}</h2>
               <h3>\$${this.product.price}</h3>
               <p>${this.product.description}</p>
               <button>Add to Cart</button>
             </div>
           </div>
         `;
   
       const addCartButton = prodEl.querySelector('button');
       addCartButton.addEventListener('click', this.addToCart.bind(this));
     }
   }
   ````

### Adding event listeners

option 1: bind the method passed a as a listener:

````js
class someClass {
	someListener(){
		console.log(this);
	}
  
  render(){
    someNode.addEventListener('click', this.someListener);
  }
}
````

option 2:

````js
class someClass {
	someListener(){
		console.log(this);
	}
  
  render(){
    someNode.addEventListener('click', 👉() => this.someListener()👈); // arrow functions don't know `this`
  }
}
````

option 3:

````js
class someClass {
	someListener = () => {
		console.log(this);
	}
	
	render(){
		someNode.addEventListener('click', this.someListener); ❌ // this doesn't have that propr when render is called, so it attaches `undefined`;It works for other scenarios
	}
}
````

### Private fields, properties and methods

````js
class ProductList {
	products = [];
  
  fetchProducts(){
    //API call
		this.products = something;
    render();
  }
}
````

I don't want other devs setting products externally, because that wouldn't be reflected in the UI. (plus, I don't have setters in the class that would update the UI when the setter is called);

So let's make `product` field and the fetchProducts method private 🚫

````js
class ProductList extends Component {

  👉#products = []; 

  constructor(renderHookId) {
    super(renderHookId, 👉false);
    👉this.render();
    this.#fetchProducts();
  }

	👉#fetchProducts(){}
  
  //replace this.products by this.#products in all instances
}

const productList = new ProductList();
productList.#products // throws this error: // Uncaught SyntaxError: Private field '#age' must be declared in an enclosing class (at app.js:195:19)
````

At this point, having the parent class Component with the selfcalled render() method doesn't make much sense because it's almost always not run because the parent constructor is passed false as a `shouldRender` , but it made sense at the time.

### Instanceof

it's an operator, like <, >, etc

````
const numbers = [1,2,3]; 
console.log(numbers);// 👉Array(3) [ 1, 2, 3 ]
numbers instanceof Array; // true

````

using [] instantiates an Array class under the hood (maybe not with the new keyword exactly??, because it has slower performance than using the literal notation []);

```js
const numbers = new Array(1,2,3);
console.log(numbers);// 👉Array(3) [ 1, 2, 3 ], same result as above
```

### Object descriptors

it's just some metadata about object props

````js
const person = {
    name: 'tebi',
    printName(){
        console.log(this.name)
    }
}

console.log(Object.getOwnPropertyDescriptors(person));

Object { name: {…}, printName: {…} }
  name: Object { value: "tebi", writable: true, enumerable: true, … }
  configurable: true  // the object can be deleted
  enumerable: true // it can be used in a for loop (useful for skipping methods while looping, and get props, or it can useful for excluding some props)
  value: "tebi"
  writable: true // props can be changed
  etc
}  
````

let's lock the name prop! 🔒

```js
Object.defineProperties(person, {
    name: {
        configurable: true,
        enumerable: true,
        value: person.name,
        writable: false
    }
});

person.name = 'new name'; // it doesn't throw an error though
console.log(person.name); // old prop value kept
```

### Who is Object?

it's constructor function with some static methods, like `assign` method

````js
const person = new Object(); 
console.log(person); // {}

console.log(Object); // function Object(){ getOwnPropertyDescriptor: function(){}, etc, etc}
// there are some static methods inside the object, no need to run the Object function with `new` keyword to access them.
````

The following resources may be helpful.

-   Classes on MDN: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

## Life before the `class` keyword

### Constructor functions

⚠️capital leters are used to indicate that constructor functions should be called with the `new`  keyword, not just as a normal function call

the magic to create the object is given by the usage of the `new` keyword.

```js
// class Person {
//     name = "Max";

//     constructor(){
//         this.age = 30;
//     }

//     printGreeting(){
//         console.log(`Hi I'm ${this.name}`);
//     }
// }

// ⚠️ the function below doesn't really represent the class, TBD
function Person (){
    this.name = 'Max'; 
    this.age = 30;
    this.printGreeting = function(){ // ⚠️this is not technically the same as the printGreeting(){} in the class above, tbd"
        console.log(`Hi I'm ${this.name}`);
    }
 // there's no return! it returns an object just because was called with the 👉 `new` keyword
}

const person = new Person();

console.log(person); // Object { name: "Max", age: 30, printGreeting: printGreeting() }
```

### what does the new keyword does to the called function??

```js
function person (){
    this = {};
    this.name = 'Max'
    // etc
    return this;
}
```
### the class keyword and how it calls a constructor function under the hood

the class keyword is syntactic sugar 🍭, that runs a constructor function under the hood, providing a better dev experience syntax wise

### What are prototypes?

It's a prop of all JS objects, that is used to share code from other objects, which are  👉 **fallback objects** 👈.

If JS doesn't found a propr in an object, it will look for it in the prototype.

JS is a prototype + constructor functions based language!

the prototype is a **prop** of the constructor **function pointer**:

```
const Person = (){//some code};
Person.prototype; //prints Object { … } 
```

All objects in JS have this `Object.prototype`  as the most parent prototype.

````js
function Human(){
    this.breathes = true;
    this.printAge = function() {
        console.log(this.age);
    }
}

function Person (){
    this.name = 'Max'; // this is not technically the same as the name = "Max in the class above, tbd"
    this.age = 30;
    this.printGreeting = function(){
        console.log(`Hi I'm ${this.name}`);
    }

}

// extends keyword does this for me under the hood!
Person.prototype = new Human(); // there are more ways to assing the prototype, see below

const person = new Person();


console.log(person); // Object { name: "Max", age: 30, printGreeting: printGreeting() }
console.log(person.breathes);
person.printAge(); //prints 30 // the `this` inside printAge refers to what called printAge, which is person in this case, it works!

console.log(Person.prototype === person.__proto__); // true! is the very same object in memory, not copies 😮
````

When a propr or method is called, JS checks the chain up one by one:

````js
const person = new Person();
person.breathes; 
// JS will check first in the person object, then in the person.__proto__, if not, person.__proto__.__proto__
````

double underscore AKA dunderscore 😅

`__proto__` is a prop  in every JS object, but `prototype` only on function objects (pointers);

### Ways to assign the prototype

````js
// extends keyword does this for me under the hood!
Person.prototype = new Human();
//OR
Person.prototype = {
    breathes: true,
    printAge: function(){
        console.log(this.age);
    }
}
// OR
Person.prototype.breathes = true;
Person.prototype.printAge = function(){
    console.log(this.age);
}
````



### How to prevent overriding the default prototype of a function?

````
Person.prototype.someNewMethod = function(){}
````

### What is the `__proto__.constructor`? 

is the reference of the constructor function used to create the object:

````js
function Person (){
    this.name = 'Max'; // this is not technically the same as the name = "Max in the class above, tbd"
    this.age = 30;
    this.printGreeting = function(){
        console.log(`Hi I'm ${this.name}`);
    }

}

Person.prototype.breathes = true;
Person.prototype.printAge = function(){
    console.log(this.age);
}


const person = new Person();

const person2 = new person.__proto__.constructor();

console.log(person2); // same as person
````


### the static keyword under the hood

```js
class Person {
	static sayHello(){
		console.log('hello');
	}
}

// is translated to this under the hood
function Person(){} // a constructor function is create

//then a prop is added
Person.sayhello = function(){
  console.log('hello');
}
```



#### 👉 All objects in JS have this `Object.prototype`  as the most parent prototype.👈

What's inside there? Some prop which are like static methods of classes:
`````js
console.log(Object.prototype);
{
	apply: function apply()
  arguments: 
  bind: function bind()
  call: function call()
  caller: 
  constructor: function Function()
  length: 0
  name: ""
  toString: function toString()
  Symbol(Symbol.hasInstance): function Symbol.hasInstance()
}	
`````

#### All objects in JS can use this methods 👆

that' is why I can call `person.toString() ` without getting an error:

```
person.toString();
"[object Object]" 
```

What other things are inside the Object function: (⚠️Firefox browser).
````
assign: function assign()
create: function create()
defineProperties: function defineProperties()
defineProperty: function defineProperty()
entries: function entries()
freeze: function freeze()
fromEntries: function fromEntries()
getOwnPropertyDescriptor: function getOwnPropertyDescriptor()
getOwnPropertyDescriptors: function getOwnPropertyDescriptors()
getOwnPropertyNames: function getOwnPropertyNames()
getOwnPropertySymbols: function getOwnPropertySymbols()
getPrototypeOf: function getPrototypeOf()
hasOwn: function hasOwn()
is: function is()
isExtensible: function isExtensible()
isFrozen: function isFrozen()
isSealed: function isSealed()
keys: function keys()
length: 1
name: "Object"
preventExtensions: function preventExtensions()
prototype: Object { … }
seal: function seal()
setPrototypeOf: function setPrototypeOf()
values: function values()
<prototype> (or ⚠️__proto__ in chrome): function ()
````

That is why we can't call `isFrozen` in person:
````
person.isFrozen(); //❌ Uncaught TypeError: person.isFrozen is not a function
````

static methods OR, under the hood, properties of constructor functions, can only be called without executing the function/instantianting the class:
````js
Object.isFrozen(); // true
````

```js
class Dog {
    static bark(){
        console.log('woof');
    }
}

const dog = new Dog();
dog.bark(); // Uncaught TypeError: dog.bark is not a function
Dog.bark(); // work fine
```

### Where does the chain of prototypes end then?

````js
console.log(Object.prototype.__proto__); // null 
````

the fallback object of the objects created wuth Object function don't have a further fallback than the prototype.

### `.__proto__` vs  `.prototype` props: 

__proto__ is the assigned fallback object. Only present on functions.

**prototype** is the to be assigned fallback object. Present on all objects



### How classes are really translated behind the scenes 

methods are instantiated in a different way, let's start seeing where it has been added: really nested!

````js
class Human {
  	👉breathes = true; 
    👉greet(){
        console.log('hello');
    }
}

class Person extends Human {
    name = 'Max';
  	sayBye(){
      console.log('bye!');
    }
}


const person = new Person();
console.log(person);

//{
	name: 'Max',
  breathes: true, // 👈 was added to the top level 😮
  __proto__: { // ⚠️ extra proto added automatically when instanting the class
    constructor: class Person{},
    sayBye: function sayBye() // nested inside __proto__ 😮, not a top level prop 
    __proto__: class Human {
      prototype: {
        constructor: class Human {},
        👉greet: function greet(){} 👈 // not part of the top level object 😮
      }
    }
  }  
}
````

I have 2 `__protos__`, and I was expencting only one, (to be the pooped object from the Human class). It seems that using `class` keyword generates the extra one.

On the other hand, fields are added like this:


````js
class Person extends Human {
    👉name = 'Max'; // under the hood, this is added to the object after calling super
    
    constructor(){
      super();
      this.age = 30;
      // this happens under the hood, added AFTER the super() call
      🔎 this.name = 'Max';
    }
}
````

Everything that is included in the constructor of a class, can me replicated by adding that code to the body a constructor function, and the result will be the same.

### The extra `__proto__`

````js
class Person extends Human {
    name = 'Max';
  	sayBye(){
      console.log('bye!');
    }
}


const person = new Person();
console.log(person);

//{
	name: 'Max', // this might be assigned other value after object creation
  breathes: true, 
  __proto__: { 👈
    constructor: class Person{},
    sayBye: function sayBye() // popped objects aren't gonna change the function logic...so
````

the function is added to the extra photo because all objects created refer to just a single object, which is the `__proto__`, which is very efficient.

Let's prove that 2 objects are using the same `__proto__` object reference!

```js
class Person extends Human { 
  name = 'Max';
  sayBye(){
    console.log('bye!');
  }
}


const person1 = new Person();
const person2 = new Person();

console.log(person1.__proto__.sayBye === person2.__proto__.sayBye); // true!
```

The same behaviour would be achieved by this:

````js
function Person(){
	this.name = 'Max';
}

Person.prototype = function sayBye(){
	console.log('bye!');
}
````

### How not to write methods ❌

```js
class Person extends Human { 
  name = 'Max';
  constructor(){
  	sayBye(){
  		console.log('bye!'); ❌
  	}
  }
  this.sayBye = function(){ // ❌
    console.log('bye!');
  }
  
  sayBye = ()=> { // ✅ only acceptable as an event listener, to avoid using .bind()
  	console.log();
  }
}
```

`.bind` is less readable than having arrow functions (even though is less performant).

### Prototypes are everywhere!

let's override `.forEach` method of an Array:

```js
(2) ['messi', 'martinez']
0 "messi"
1"martinez"
length: 2
[[Prototype]]:  // console representation of `__proto__`
	forEach: ƒ forEach()
```
### Hijacking .forEach - Use getting and Setting Prototypes

```js
const players = ['messi', 'martinez'];

// just do this when developing ⚠️
players.__proto__.forEach = function(){
    console.log('forEach has been hacked!');
}

// the official way ✅
Object.setPrototypeOf(players, {
    ...Object.getPrototypeOf(players),
    forEach(){
        console.log('forEach has been hacked!');
    }
});

players.forEach(); // 'forEach has been hacked!'
```

that is why we see the MDN docs as Array.prototype.forEach, because it's added to the Array constructor function in with that syntax, added that way to the function pointer.

In objects, it's not neccessary to spread the prototype:

````js
const player = {
    isRightHanded: false
}

// player.__proto__ is Object

Object.setPrototypeOf(players, {
    // ...Object.getPrototypeOf(players)// no need to spread Object, because it will be the protype of the object I'm writing this from
    forEach(){
        console.log('forEach has been hacked!');
    }
});
````



### A new way to create objects

````js
const player = {};
const player = new Object();
const player = Object.create(prototypeHere); // 👈
````

````js
const player = Object.create({ 
    shoutGoal(){
        console.log('goooooool');
    }
}, someOptionalDescriptorHere);

console.log(player);

// {}
//     [[Prototype]]: Object
//     	shoutGoal: ƒ shoutGoal()
//     	[[Prototype]]: Object
//         constructor: ƒ Object()
//         hasOwnProperty: ƒ hasOwnProperty()

player.isRightHanded = false;

// Or I could use
Object.defineProperty('isRightHanded', false, someOptionalDescriptorHere);
````

Side note: to keep all the default descriptors an modify one, I could do:

````js
Object.defineProperty('isRightHanded', false, {
	...Object.getOwnPropertyDescriptor(player),
	...writable: false
});
````

### Differences between constructor functions vs classes

````
constructor functions:
- can be called with new
- all props and METHODS are enumarable
- not in strict mode by default

classes:
- must be called with new
- METHODS are not enumerable (out of the top level object)
- always strict mode

````

The following resources may be helpful.

-   Constructor Functions (MDN): [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects#Using_a_constructor_function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects#Using_a_constructor_function)
-   Prototypes (MDN): [https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object_prototypes](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object_prototypes)

## Dom & More Browser API



<!--stackedit_data:
eyJoaXN0b3J5IjpbNTY2NDcxMjk3LC04NjE5MzMxODgsMTI5OD
kyMTYzMl19
-->