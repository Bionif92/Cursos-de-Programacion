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

````
function checkImput (cb, ...strings) {
let HasEmptyText = false
for (const text of strings) {
if (!text) { HasEmptyText = true; 
break;}}
if (!HasEmptyText) {cb ()}
}

checkImput (() => {console.log ('All not empty')}, 'Hello', '12', 'adsfa','')````

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
``

### Adding extra parameters on the fly: the .bind() method:

Using .bind() method returns a new function reference with some new configuration (give values to some params), so that function can be called at some point (upon an event, etc) with the pre-configured param values!

````js
const sayHello2 = (👉 greeting, name) =>{
  console.log(greeting + name);
}
// silly example calling the function right away, not done in real life

sayHello2.bind(this, 👉'Special greetings ')('tebi!'); // Special greetings, tebi!
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
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc1ODY1MDM2NSwxMjQzOTgwOTQwLDE1Mj
M0MDY2MzldfQ==
-->