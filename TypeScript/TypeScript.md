
# TypeScript Course

## Getting Started

### What is TypeScript?

A Javascript SuperSet

Adds new Features + Advantages to Javascript

Browser can´t execute it

Write Typescript, then compiled to Javascript

### Using TypeScript

Error of JS in calculator, that brings the .value as string always

Install:
````bash
npm install -g typescript
````

Then create file with `.ts` extension, copy and paste the code of JS file here, need to delete then the JS file

````TS
const input1 = document.getElementById('num1')! as HTMLInputElement; // this last part is TypeScript
````
Can add types too:
````TS
function add(num1:number, num2:number) {// add the type
	return num1 + num2;
}
````

To compile to JS:

````bash
//terminal
tsc file.ts
````
You can manage the error and compile again

**Always import the JS file**

## TypeScript Basics & Basic Types

### Using Types

 - Number 
 - String
 - Boolean 

How to write the type:
````TS
function add(num1:number, num2:number) {// add the type
	return num1 + num2;
}
````
**Typescript helps you during development, not changing your code if you have an error**

### JS Types vs TS Types

````
//JS
console.log(typeof n1); // number
````

With TS you see the problems early in development, not when it throw the error in JS

### Numbers, Strings and Booleans

````
//JS boolean and string example
function add(num1:number, num2:number,showResult:boolean, phrase:string) {
	const result = num1 +num2
	if (showResult) {
		console.log (phrase+result);
	}else {
		return result;
		}
}
````

### Type Assigment & Type Inference

````
//Type Assigment
num1: number
````

If you dont initialize is a good practice to assign the type

````
let number1:number;
````
The inference is that TS understand which type need in a constant, and if it is wrong, it will tell you

Type inference,  refers to **the automatic detection of the type of an expression in a formal language**

### Object Types

If the object dont have the property, throws an error

````js
//object
const person {
	name: 'Franco',
	age: 32
}
// type of this object automatically
const person {
	name: string;
	age: number;
}
// now change it to thw right way writting it
const person: {
	name: string;
	age: number;
} = {
	name: 'Franco',
	age: 32
}
````

### Array Types

````js
const person: {
	name: string;
	age: number;
	hobbies: string[];
} = {
	name: 'Franco',
	age: 32,
	hobbies: ['Sports','Cooking'] // type string[]
}
````
Types:

 - String[]
 - Any[]

Can use `.toUpperCase()` because it knows that is a `string[]`

### Working with Tuples

Tuple -Fix lenght array
````js
const person: {
	name: string;
	age: number;
	hobbies: string[];
	role: [number,string];// only two elements
} = {
	name: 'Franco',
	age: 32,
	hobbies: ['Sports','Cooking'],
	role: [2,'author'] // only two elements, (string | number)[]
	}
````

**`.push()` is an exeption**

### Working with Enums

Automatically enumerated global constant identifiers

````js
enum Role {ADMIN, READ_ONLY, AUTHOR}; // can assign values or text tho each constant, for default:0,1,2...

const person = {
	name: 'Franco',
	age: 32,
	hobbies: ['Sports','Cooking'],
	role: Role.ADMIN
	}
````

### The Any Type

````
let favoriteActivities = any[];
````
Not used because you lose the advantages of typescript

### The Union Type

````
imput1: number | string; //accept this two types
````
Can use if to sum things if are numbers and if the are strings

### Literal Types

Specify the type

````
resultConversion: 'as-number' | 'as-text'
````
He use it in the function to make the condition

### Type Aliases/Custom Types

````
type Combinable = number | string;
````
Use `Combinable` instead of writing the type

### Function Return Types & void

Functions have a return type, you see it when you hover the mouse
````
function add(n1:number,n2:number):number { // can add the type manually but is not convinient, let TS do his job
	return n1+n2
}

function printResult(num:number) { //have void type this function
	console.log ('Result' +num)
}
````
Void because it has no return statement

### Function as Types

````
let combineValues: (a:number,b:number) => number; // a variable with a function with two parameters and the result is a number
````

### Function Types & Callbacks

````
function addHandler (n1:number,n2:number,cb: (num:number)=>void) {
	const result= n1+n2;
	cb(result);
}
````

### The Unknown Type

````
let userInput: unknown; // store any value without errors
let userName:string;

userName = userInput // error, cannot assign unknown to string 

userInput = 'Max';
if (userUnput === 'string') {
	userName = userInput // now it doesnt throw an error, firt need to check the variable
}
````

Better than `any`, because you need to check

### The Never Type

Another type for functions
````
function generateError (message:string,code:number):never {
	throw {message:message,errorCode:code}
}
````
Crash the script into the error

### Useful Resources & Links

These links might also be interesting:

-   Official TypeScript Docs:  [https://www.typescriptlang.org/docs/handbook/basic-types.html](https://www.typescriptlang.org/docs/handbook/basic-types.html)

## The TypeScript Compiler

### Watch Mode

````
// Terminal
tsc app.ts -w
````
Auto recompile to JS

### Compile entire Proyect/Multiple Files

````
// Terminal
tsc --init // everything in the foulder is managed by TS

tsc // to add files

tsc -w // to add changes
````

### Including/Excluding Files

In `tsconfig.json` created with `tsc --init`,at the end

````
	...},
	"exclude": [
		"analytics.ts",
		"*.dev.ts",// ends with that
		"**/*.dev.ts", // any file with that pattern in any foulder
		"node_modules" // it is the default to exclude node
	]
	"include": [
	]
	"files":[] // for foulder moreover
}
````

### Setting a Compilation Target

In `tsconfig.json` created with `tsc --init`

````
{
	"compilerOptions": {
		target: "es5" //can change the version with crtl + space, like es6 more modern
	}
````

### Understanding TS Core Libs

````
{
	"compilerOptions": {
		"lib": [
			"dom",
			"es6",
			"dom.iterable",
			"scripthost" // core JS features, is the default
		]
	}
````

Further Links:

tsconfig Docs:  [https://www.typescriptlang.org/docs/handbook/tsconfig-json.html](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

Compiler Options (Official Docs: )[https://www.typescriptlang.org/docs/handbook/compiler-options.html](https://www.typescriptlang.org/docs/handbook/compiler-options.html)

### More Configuration & Compilation Option

````
{
	"compilerOptions": {
		"allowJS" // add JS files to the compilation
		"checkJS" // see errors	
	}
````

Use `allowJs` and `checkJS` if you have vanilla JS you want to check

### Working with Source Maps

Helps with debbuging and development
````
{
	"compilerOptions": {
		"sourceMap": true // for debbuging th TS files	
	}
````

### rootDir and outDir

````
{
	"compilerOptions": {
		"outDir": "./dist" // JS files created in dist foulder
		"rootDir": "./scr" // TS files in scr foulder
		"removeComments": true // delete comments in JS files
		"noEmmit": true // dont create JS files of the TS
	}
````

### Stop Emitting Files on Compilation Errors

````
{
	"compilerOptions": {
		"noEmitOnError": true/false, // option not listen, false default, true: not generate the JS file if has an error
	}
````

### Strict Compilation

````
{
	"compilerOptions": {
		"strict": true // enable all strict type from bellow
		"noImplicitAny" // ensure we dont have "any" type
		
	}
````
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjczODI4NjAyLC0xMjk1Njk5ODQ4LDE3Mj
M3ODk1NjAsLTk0NjM2ODUxLDEyODU4OTA5ODAsLTEyNjY1Mjc0
NDMsLTE4OTM1Mjc4MTYsLTIxMjI2NTU2ODUsLTE5MTY2NDkwND
AsLTE1NDk1MDk4NTcsMTA4NDE1NDkzLC0xNTY3NzMyMjM1LC0x
MzAwODgwMTUxLDE4OTI0NjgyNzMsLTEyMzcyNTYwMzQsLTEwMT
I5ODU2ODgsLTc3NjkxMjAzMCwtNjI5ODM3MDIwLC0yMDI3MTM5
OTY5LC03Mzc2MzYzMzFdfQ==
-->