
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

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwMzU0MjkzMzcsLTE0MzE2MjYyMjQsMT
U1MzEwNDc2NSwxNTI3NzU0NTI5LDE4MTI0MzExNjAsLTE4NzE2
Nzg2MjUsMTY2MzM3MDAzNCwtMTU0NDkzMzE3NSwtMTU5NjM1Nj
MwMCwyMDQwMjk3NjIyXX0=
-->