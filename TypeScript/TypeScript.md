
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
function add(num1:number, num2:number) {
	return num1 +num2;
}
````

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY0MzUwMzg5OSwxODEyNDMxMTYwLC0xOD
cxNjc4NjI1LDE2NjMzNzAwMzQsLTE1NDQ5MzMxNzUsLTE1OTYz
NTYzMDAsMjA0MDI5NzYyMl19
-->