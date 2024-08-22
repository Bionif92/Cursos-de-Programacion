
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
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1NDk1MDk4NTcsMTA4NDE1NDkzLC0xNT
Y3NzMyMjM1LC0xMzAwODgwMTUxLDE4OTI0NjgyNzMsLTEyMzcy
NTYwMzQsLTEwMTI5ODU2ODgsLTc3NjkxMjAzMCwtNjI5ODM3MD
IwLC0yMDI3MTM5OTY5LC03Mzc2MzYzMzEsLTE1MTIyODU0NDYs
MTMzNzcxNDM0OSwtMTQ2ODcwNjQzOCwzOTMwODEzMzksMjA5ND
E4MTU0NSwtMTg2Njg3NjE0NywtNDI1MzI4NjUyLC0xMDAxMjc1
NjE0LC0yMjMwMDE1NDddfQ==
-->