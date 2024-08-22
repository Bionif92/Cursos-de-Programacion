
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
//JS
showResult:boolean
````
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4NjY4NzYxNDcsLTQyNTMyODY1MiwtMT
AwMTI3NTYxNCwtMjIzMDAxNTQ3LC0yMDM1NDI5MzM3LC0xNDMx
NjI2MjI0LDE1NTMxMDQ3NjUsMTUyNzc1NDUyOSwxODEyNDMxMT
YwLC0xODcxNjc4NjI1LDE2NjMzNzAwMzQsLTE1NDQ5MzMxNzUs
LTE1OTYzNTYzMDAsMjA0MDI5NzYyMl19
-->