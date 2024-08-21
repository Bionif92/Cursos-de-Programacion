
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
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTk2MDM2NzAxLDE4MTI0MzExNjAsLTE4Nz
E2Nzg2MjUsMTY2MzM3MDAzNCwtMTU0NDkzMzE3NSwtMTU5NjM1
NjMwMCwyMDQwMjk3NjIyXX0=
-->