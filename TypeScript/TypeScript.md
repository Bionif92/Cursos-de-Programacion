
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
}
````

### Stop Emitting Files on Compilation Errors

````
{
	"compilerOptions": {
		"noEmitOnError": true/false, // option not listen, false default, true: not generate the JS file if has an error
	}
}
````

### Strict Compilation

````
{
	"compilerOptions": {
		"strict": true // enable all strict type from bellow
		"noImplicitAny" // ensure we dont have "any" type
		"strictNullChecks" // strict will null elements
		"strictFunctionTypes" // see later
		"strictBindCallApply" // when you use .bind and you configure to null, and dont put argument
	}
}
````

See other options later in the course

### Code Quality Options

````
{
	"compilerOptions": {
		"noUnusedLocals"
		"noUnusedParameters"
		"noImplicitReturns" // return something in all cases
		"noFallthroghCasesInSwitch"
	}
}
````
Need to enable them for quality code

### Debbuggin with VSC

Can put breakpoints in VSC in a TS file

need to enable "sourceMap": true

Debbug/Start Debbug/Chrome

Create a launch.json
Change: url: "http://localhost:3000"

On terminal tsc

### Useful Resources & Links

Attached you find all the code snapshots for this module - you also find them attached to individual lectures throughout this module.

These links might also be interesting:

-   tsconfig Docs: [https://www.typescriptlang.org/docs/handbook/tsconfig-json.html](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)
-   Compiler Config Docs:  [https://www.typescriptlang.org/docs/handbook/compiler-options.html](https://www.typescriptlang.org/docs/handbook/compiler-options.html)
-   VS Code TS Debugging: [https://code.visualstudio.com/docs/typescript/typescript-debugging](https://code.visualstudio.com/docs/typescript/typescript-debugging)

## Next-Generation: JS & TS

JavaScript Compatibility Table: [https://kangax.github.io/compat-table/es6/](https://kangax.github.io/compat-table/es6/)

New tools:

 - Use let and const
 - Use arrow functions
 - Default function parameters (default on the right)
 - Spread Operator - On arrays and objects
 - Rest Parameters
 - Array & Objects Destructuring

**TS use this tools to run in older browsers, code is compiled**

## Classes & Interfaces

### this.Classes TS

````
class Department {
	name:string; //field
	
	constructor(n:string) {
		this.name:n;
	}

	describe(this:Department) { // only can refer to a Department class
		console.log('Department: '+ this.name)
	}
}

const accountingCopy = {describe: accounting.describe};
accountingCopy.describe(); // error, not refer to Department Class

const accountingCopy = {name: 's', describe: accounting.describe};
accountingCopy.describe(); // now it works
````

### Private & Public Modifiers

````
class Department {
	name:string; //field
	private employees: string[] = []; //only accesible from the method
	
	constructor(n:string) {
		this.name:n;
	}

	describe(this:Department) { // only can refer to a Department class
		console.log('Department: '+ this.name)
	}
	addEmployee(employee:string) {
		this.employees.push(employee); 
	}
}
accounting.addEmployee('Max'); // it is ok
accounting.employees[2] = 'Max'; // not ok

````
Public is the default

### Shorthand Initialization

````
class Department {
	constructor(private id: string, public name:string) { //initialize the properties
	}

	describe(this:Department) { 
		console.log('Department: '+ this.name)
	}
	addEmployee(employee:string) {
		this.employees.push(employee); 
	}
}
````

### Readonly Properties

````
class Department {
	constructor(private readonly id: string, public name:string) { //readonly property
	}

	describe(this:Department) { 
		console.log('Department: '+ this.name)
	}
	addEmployee(employee:string) {
		this.employees.push(employee); 
	}
}
````
Can not change the property with the readonly text

More on inheritance and the JavaScript prototype chain: [https://www.udemy.com/course/understanding-typescript/learn/lecture/16888254#overview](https://www.udemy.com/course/understanding-typescript/learn/lecture/16888254#overview)

### Inheritance

Unless you put a new contructor, it inherit the father one
Need to put super first
````
class ITDepartment extends Department {
	contructor(id:string, public admins: string[]) {
		super(id, 'IT'); // need to add if you make your own contructor and you are inheriting from another class
	}
}
````
**It will have all the new and old properties**

### Overriding properties & The protected Modifier

Overwrite methods or properties of a class: use word protected instead of private for a property, then you can change it if you are on an extended class

### Getters & Setters

````
class AccountingDepartment extends Department {
	private lastReport:string;

	get mostRecentReport() {
		if (this.lastReport) {
			return this.lastReport;
		}
		return new Error ('No report found');
	}
	
	set mostRecentReport(value:string) {
		if (!value) {
			throw new Error('Please enter valid value')
		}
		this.addReport(value);
	}

	constructor(id:string,private reports:string[]) {
		super(id,'Accounting');
		this.lastReport = reports[0];
	}

	addReport(text:string) {
		this.reports.push(text);
		this.lastReport = text;
	}
}
````

Getter: property where you execute a function or method when you retrieve a value
Setter: to set a value

### Static Methods & Properties

You can access directly from the class no need to create a new class

````
class ... {
	static createEmployee(name:string) {
		return {name:name};
	}
}

const employee1 = Department.createEmployee('Max'); // without needing an instance of creating the class
````

Same for properties
**Cannot use static properties or methods inside the class, need to use class.property or class.method**

### Abstract Classes

````
abstract class1 ... {
	abstract method1(this: class1):void;
}

class2 ... extend class1 {
	method1() {
		...;
	}
}
````

If you dont want the exact implementation in the root class of property or method, and you give the specific implementation in the inheritance classes

**Abstract classes cant be instanciated, they are there only to inherit the method or properties**

### Singletons & Private Constructors

Singletons pattern: ensure that ther is only one instance of a certain class
````
class1 ... {
	private static instance: class1;
	
	private contructor() {
	}
	
	static getInstance() {
		if(class1.instance) {
			return this.intance;
		}
		this.instance = new class1(parameters);
		return this.intance;
	}
}

const variable1 = class1.getInstance();
const variable2 = class1.getInstance(); // will recive the same class
````

### A First Interface

Interfase: describe the structure of an object

Only on TS

````
interface Person { // only can define the structure
	name:string;
	age:number;

	greet(phrase:string):void;
}

let user1: Person;

user1 = {	
	name: 'Max',
	age: 30,
	greet(phrase:string) {
		console.log(phrase + ' ' + this.name);
	}
};
````

### Using Interfaces with Classes

Interface only for structuring objects
Can implement interface in a class

````
interface Greetable { 
	name:string;
	greet(phrase:string):void;
}

class Person implements Greetable, anotherInterface {
	name:string;
	age:30;
	constructor(n:string) {
		this.name = n;
	}
	greet() {
	}
} // need to have name and greet but you also can add other things
````

### Why Interfaces?

Enforce structure to other classes

### Readonly Interface Properties

````
interface Greetable { 
	readonly name:string;
	greet(phrase:string):void;
}
````

Also used on types

### Extending Interfaces

````
interface Named {
	readonly name:string;
}
interface Greetable extends Named{ 
	greet(phrase:string):void;
}
````

### Interface as Function Types

Also to give structure to a function

````
interface AddFn {
	(a:number,b:number): number;
}

let add = AddFn;
add = (n1:number,n2:number) => {
	return n1+n2;
}
````

### Optional Parameters & Properties


````
interface Named {
	readonly name:string;
	outputName?:string; // might exist but it doesnt have to
	
}
````

### Useful Resources & Links

Attached you find all the code snapshots for this module - you also find them attached to individual lectures throughout this module.

These links might also be interesting:

-   More on (JS) Classes: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)
-   More on TS Interfaces: [https://www.typescriptlang.org/docs/handbook/interfaces.html](https://www.typescriptlang.org/docs/handbook/interfaces.html)

## Advanced Types

### Intersection Types

Combine other types

````
type Admin = {
	name: string;
	privileges: string[];
}

type Employee = {
	name: string;
	startDate: Date;
}

type ElevatedEmployee = Admin & Employee;

const e1: ElevatedEmployee = {
	name: 'Max',
	privileges: ['create-server'],
	startDate: new Date()
}
````
````
type Combinable: string | number;
type Numeric: number | boolean;
type Universal: Combinable & Numeric; // give the intersection: number
````

Union type - the intersection is the new type
Object type - the combination is the new type

### More on Type Guards

````
type Combinable: string | number;

function add (a:Combinable,b:Combinable) {
	if (typeof a =='string' || typeof b == string) { // guard
		return a.toString()+ b.toString();
	}
	return a+b;
}
````

````
type Admin = {
	name: string;
	privileges: string[];
}

type Employee = {
	name: string;
	startDate: Date;
}

type UnknownEmployee = Employee | Admin;

function printEmployeeInformation (emp:UnknownEmployee) {
	console.log('Name: ' + emp.name)
	if ('privileges' in emp) { // guard
		console.log('Privileges: ' + emp.privileges)
	}
}
````
````
class Car {
	drive() {
		console.log('Driving...');
	}
}

class Truck {
	drive() {
		console.log('Driving a Truck...');
	}
	loadCargo(amount:number) {
		console.log('Loading Cargo...' + amount);
	}
}

type Vehicle = Car | Truck;

const v1 = new Car();
const v2 = new Truck();

function useVehicle (vehicle: Vehicle){
	vehicle.drive();
	if (vehicle instanceof Truck) { // guard for classes
		vehicle.loadCargo();
	}
}
````

### Discriminated Unions

Pattern when you work with union types that makes implementing guards more easy

````
interface Bird {
	type: 'bird'; // common property to describe the type
	flyingSpeed: number;
}

interface Horse {
	type: 'horse';
	runningSpeed: number;
}

type Animal = Bird | Horse;

function moveAnimal (animal:Animal) {
	let speed;
	switch (animal.type) {
		case 'bird':
			speed = animal.flyingSpeed
			break;
		case 'horse':
			speed = animal.runningSpeed
	}
	console.log ('Moving with speed: ' + speed)
}
````

### Type Casting

Tell TS that some value is of an specific type when TS can not detect it by itself

````
const paragraph = document.querySelector('p'); // knows it is a paragraph from the dom

const paragraph = document.getElementById('msg-out'); // dont know the specific type

// Type Casting

const paragraph = <HTMLInputElement>document.getElementById('msg-out');

// other way

const paragraph = document.getElementById('msg-out') as HTMLInputElement;
````

To never yield null:

````
// ! after the element
const paragraph = document.getElementById('msg-out')!;
````

### Index Properties

Create Object that are more flexible with properties

````
// dont know how many properties and the names i will need
interface ErrorContainer { 
	id:string; // can add defined properties
	[prop:string]:string;
}
````

### Function Overload

A feature that allow us define multiple function signatures --  Multiple ways of calling a function with different parameters

````
type Combinable: string | number;

function add (a:Combinable,b:Combinable) {
	if (typeof a =='string' || typeof b == string) { // guard
		return a.toString()+ b.toString();
	}
	return a+b;
}

const result = add(1,5); // Type Combinable, dont know if it is string or number

// can use type casting

const result = add(1,5) as number;

// use function overload better

function add (a:number,b:number):number
function add (a:string,b:string):string
function add (a:Combinable,b:Combinable) {
	if (typeof a =='string' || typeof b == string) { // guard
		return a.toString()+ b.toString();
	}
	return a+b;
}

const result = add(1,5); // number you can use method to this number now
````

### Optional Chaining

See if properties are defined before accesing
````
const fetchedUserData = {
	id: 'u1',
	name:'Max',
	job: {title: 'CEO', description: 'My own company'}
};

// if you dont know if the job property is a thing on the backend

console.log(fetchedUserData?.job?.title); // see if it defined fetchedUserData, then job, and then tries to acces title
````

### Nulling Coalescing

Deal with null data

````
const userInput = null;

const storedData = userInput || 'DEFAULT'; // not useful because it work with undefined or '' too

// Nulling Coalescing

const storedData = userInput ?? 'DEFAULT';// only default if it is null
````

### Useful Resources & Links

Attached you find all the code snapshots for this module - you also find them attached to individual lectures throughout this module.

These links might also be interesting:

-   More on Advanced Types: [https://www.typescriptlang.org/docs/handbook/advanced-types.html](https://www.typescriptlang.org/docs/handbook/advanced-types.html)

## Generics

### Build.in-Generics & What are Generics?

A type linked with another type

**Give us flexibility and safety with the types**

````
const names: Array<string> = [];// string[]
````

Promise type

````
const promise: Promise<string> = new Promise((resolve,reject)=>{
	setTimeout(()=>{
		resolve('This is done');
	},2000);
}); // Promise<unknown> if you dont specify
````
If you know the outcome, you can use then with specific methods

### Creating a Generic function

````
function merge (objA:object,objB:object) {
	return Object.assign(objA,objB);
}

const mergedObj = merge ({name:'Max'},{age:30});
mergedObj.name; // cannot access

// convert into generic function

function merge <T,U>(objA:T,objB:U) {
	return Object.assign(objA,objB);
} // now knows what is inside, because it see the intersection of the types
````
**The types are set dinamically when you put real values**

Can specify also the types when you pass the values to the function, but is redundant
````
const mergedObj = merge <string,number> ({name:'Max'},{age:30});
````

### Working with Contrains

Restrict the type

````
function merge <T extends object,U extends object>(objA:T,objB:U) {
	return Object.assign(objA,objB);
} // restricted to objects
````

### Another Generic function

````
interface Lenghty {
	lenght:number;
}

function countAndDescribe <T extends Lenghty> : [T, string](element:T) {
	let descriptionText = 'Got no value.'
	if (element.lenght == 1) {
		descriptionText = 'Got 1 element.'
	} else if (lement.lenght > 1) {
		descriptionText = 'Got' + element.lenght + 'elements.'
	}
	return [element,descriptionText]
}

console.log(countAndDescribe('Hi there!')); // convert to an object with the property lenght to work inside the function
````

### The keyof Constrain

````
function extractAndConvert <T extends object,U extends keyof T> (obj:T, key:U) { // U is a property of the object
	return 'Value' + obj[key]; // access a property of an object
}

extractAndConvert({name:'Max'},'name');
````

### Generic Classes

````
class DataStorage<T> {
	private data: T[] = [];

	addItem(item:T) {
		this.data.push(item);
	}

	removeItem(item:T) {
		this.data.splice(this.data.indexof(item),1);
	}

	getItems() {
		return [...this.data];
	}
}

const textStorage = new DataStorage<string>();
textStorage.addItem(10);// dont work, need to be a string
textStorage.addItem('Max'); // ok
````
Could generate the same class with different types inside

**Problem with this example are objects, to remove and object, you can not use this class because they are reference values, need to create a variable with the object to remove it this way**

Better if you select the right types you will use:
````
class DataStorage<T extends string | number | boolean> {...}
````

### Generic Utility Types

Built-in utility types: [https://www.typescriptlang.org/docs/handbook/utility-types.html](https://www.typescriptlang.org/docs/handbook/utility-types.html)

Example: 

 - Partial Type- Temporarily make it as certain type and then change it
 - Readonly Type - Not allow to do changes to the type

### Generic vs Union Types

Union Types - can have mix types inside
Generic Types - can only be one type from that list, and stick to it 

### Useful Resources & Links

Attached you find all the code snapshots for this module - you also find them attached to individual lectures throughout this module.

These links might also be interesting:

-   More on Generics: [https://www.typescriptlang.org/docs/handbook/generics.html](https://www.typescriptlang.org/docs/handbook/generics.html)

## Decorators

Decorators are **a TypeScript feature that enables the application of higher-order functions to class constructors and their members**.

### First Class Decorator

In tsconfig.json :

````
"compilerOptions" : {
	"target": "es6"
	"experimentalDecorators":true
}
````

In TS:
````
// decorator to a class
function Logger(constructor: Function) {// common tu see in uppercase
	console.log('Logging...');
}

@Logger()
class Person {
	name: 'Max';
	constructor() {
		console.log('Creating Person Object...')
	}
}

const pers = new Person();
````

No need to stanciate the class to work the decorator

### Working with Decorator Factories

Factories - Return a decoration function

````
function Logger(logString: string) {
	return function(constructor: Function) {
		console.log(logString);
		console.log(constructor);
	}
}

@Logger('LOGGING - PERSON')
class Person {
	name: 'Max';
	constructor() {
		console.log('Creating Person Object...')
	}
}

const pers = new Person();
````

### Building more Useful Decorators

Output an h1 when the class is deffined:
````
function WithTemplate(template:string,hookID:string) {
	return function(_: Function){ // dont use the constructor, put _
		const hookEl= document.getElementByID('hookedID')
		if (hookEl) {
			hookEl.innerHTML = template;
		}
	}
}

@WithTemplate(<h1>My Person Object<h1/>,'app')
class Person {
	name: 'Max';
	constructor() {
		console.log('Creating Person Object...')
	}
}

const pers = new Person();
````
To output the name:

````
function WithTemplate(template:string,hookID:string) {
	return function(constructor: Function){ 
		const p = new constructor();
		const hookEl= document.getElementByID('hookedID')
		if (hookEl) {
			hookEl.innerHTML = template;
			hookEl.querySelector('h1')!.textContent= p.name;
		}
	}
}

@WithTemplate(<h1>My Person Object<h1/>,'app')
class Person {
	name: 'Max';
	constructor() {
		console.log('Creating Person Object...')
	}
}

const pers = new Person();
````

### Adding Multiple Decorators

Can add more than one decorator

**What run first: if you have something outside the return the priority is from top to bottom, inside the return (decorator function) is the oposite**

### Diving into Property Decorators

````
function Log(target:any,propertyName:string|Symbol) {
	console.log('Property Decorator');
	console.log(target,propertyName); // target: prototipe or constructor of the object, propertyName: title
}

class Product {
	@Log
	title:string;
	_price:number;
	set price(val:number) {
		if (val>0) {
			this._price = val;
		}
	}
	constructor(t:string) {
		this.title = t;
		this._price = number;
	}
	getPriceWithTax(tax:number) {
		return this._price*(1+tax);
	}
}
````

### Accessor & Parameter Decorators

Decorator to Accessor:
````
function Log2(target: any, name:string, descriptor: PropertyDescriptor) {
	console.log(target); // target: prototipe or constructor of the object
	console.log(name); // name: name of the accesor, this case price
	console.log(descriptor);// descriptor: object with description of the accesor
}

class Product {
	@Log
	title:string;
	_price:number;
	@Log2
	set price(val:number) {
		if (val>0) {
			this._price = val;
		}
	}
	constructor(t:string) {
		this.title = t;
		this._price = number;
	}
	getPriceWithTax(tax:number) {
		return this._price*(1+tax);
	}
}
````
Decorator to Methods:

````
function Log3(target:any, name:string|Symbol, descriptor: PropertyDescriptor) {
}

@Log3
Method
````

Decorator to Parameters:
````
function Log3(target:any, name:string|Symbol, position: number) { // name: method, position: count the parameters and give a number
}

@Log3
Method(@Log4 Parameter) {}
````

### When Decorators Execute?

**Decorators all execute when the class is created**

### Returning (and Changing) a Class in a Class Decorator

We can have a return value inside the decorator function:

````
function WithTemplate(template:string,hookID:string) {
	return function<T extends {new(...args:any[]:{name:string})}>(originalConstructor: T){ 
		return class extends originalConstructor {
			constructor(..._:any[]) {
				super();
				const hookEl= document.getElementByID('hookedID')
				if (hookEl) {
					hookEl.innerHTML = template;
					hookEl.querySelector('h1')!.textContent= this.name;
				}
			}
		}
	}
}
````
With this you enhance the decorator to the class, and the name apper when you create an instance

### Other Decorator Return Types

Classes, Accessors and Methods are the three types you can have in return something else

Decorators on properties and parameters, TS will ignore the outcome

### Example Creating an Aoutbind Decorator

First he create a button
````
function Log3(target: any, name:string|Symbol, descriptor: PropertyDescriptor): PropertyDescriptor {
	return {}
}

class Printer {
	message = 'this works';

	showMessage() {
		console.log(this.message);
	}
}
const p = new Printer();

const button = document.querySelector('button')!;
button.addEventListener('click',p.showMessage); // if we click it shows undefined
button.addEventListener('click',p.showMessage.bind(this)); // common JS usage

// now use decorator

function Autobind (_: any, _: string|Symbol, descriptor: PropertyDescriptor) {
	const originalMethod = descriptor.value // point at the method
	const adjDescriptor: PropertyDescriptor = {
		configurable: true,
		enumerable: false,
		get() {
			const boundFn = originalMethod.bind(this); // point at the object that belongs
			return boundFn;
		}
	}
	return adjDescriptor;
}

class Printer {
	message = 'this works';

	@Autobind
	showMessage() {
		console.log(this.message);
	}
}
const p = new Printer();
button.addEventListener('click',p.showMessage);
````

### Validation with Decorators

In the example we want to validate the data from a fetch
````
class Course {
	title:string;
	price:number;
	constructor(t:string,p:number) {
		this.title=t;
		this.price:p;
	}
}

// we have a form with the data in htlm
const courseForm = document.querySelector('form')!;
courseForm.addEventListener('submit', event => {
	event.preventDefault();
	const titleEl = document.getElementById('title') as HTMLInputElement;
	const priceEl = document.getElementById('price') as HTMLInputElement;
	const title = titleEl.value;
	const price = +titleEl.price;// convert to a number
	const createdCourse = new Course(title,price);
});
````
Can create a curse also without values too

Need to include the validation in the course

````
interface ValidatorConfig {
	[property:string]: {
		[validatableProp:string]:string[]
	}
}

const registeredValidators: ValidatorConfig = {};

function Required(target: any, propName:string) {
	registeredValidators[target.constructor.name//point to Couse Class] = {
		...registeredValidators[target.constructor.name], // to have the key pairs of the other enters and not overwrite
		[propName]:[...registeredValidators[target.constructor.name][propName], 'required']
	}
}

function PositiveNumber() {
	registeredValidators[target.constructor.name//point to Course Class] = {
		...registeredValidators[target.constructor.name],
		[propName]:[...registeredValidators[target.constructor.name][propName], 'positive']
	}
}

function validate(obj: any) {
	const objValidatorConfig = registeredValidators[obj.constructor.name];
	if (!objValidatorConfig) {
		return true;
	}
	let isValid = true;
	for (const prop in objValidatorConfig) {
		for (const validator of objValidatorConfig[prop]){
			switch(validator) {
				case'required':
					isValid = isValid && !!obj[prop];
					break;
				case 'positive':
					isValid = isValid && obj[prop]>0;
					break;
			}
		}
	}
	return isValid;
}

class Course {
	@Required
	title:string;
	@PositiveNumber
	price:number;
	constructor(t:string,p:number) {
		this.title=t;
		this.price:p;
	}
}

const courseForm = document.querySelector('form')!;
courseForm.addEventListener('submit', event => {
	event.preventDefault();
	const titleEl = document.getElementById('title') as HTMLInputElement;
	const priceEl = document.getElementById('price') as HTMLInputElement;
	const title = titleEl.value;
	const price = +titleEl.price;// convert to a number
	const createdCourse = new Course(title,price);
	if (!validate(createdCourse)) {
		alert('Invalid Input');
	}
});
````

You can search for TS Class Validator on Google, to have a better experience

https://nestjs.com/

https://docs.angular.lat/docs

### Useful Resources & Links

Attached you find all the code snapshots for this module - you also find them attached to individual lectures throughout this module.

These links might also be interesting:

-   More on Decorators:  [https://www.typescriptlang.org/docs/handbook/decorators.html](https://www.typescriptlang.org/docs/handbook/decorators.html)

## Practice - Drag and Drop Project

`_` and `_2` where used in the autobind decorator to replace the two parameters that werent used

Tuple is an array

`?` in a property to be optional

Abstract Method need to be included in the inheritance

event.dataTransfer for drag and drop

More on Drag & Drop: [https://developer.mozilla.org/en-US/docs/Web/API/HTML_Drag_and_Drop_API](https://developer.mozilla.org/en-US/docs/Web/API/HTML_Drag_and_Drop_API)

## Modules & Namespaces

### Writing Modular Code

Two options:

 - Namespaces & File Bundling - Use namespace code syntax to group code and bundle the compilation
 - ES6 Import/Export -  Use ES6 Import/Export syntax and pre-file compilation but single script import. Building with third party tools is possible

### Working with Namespaces

New file for Drag & Drop Interfaces

In the file:
````
namespace DDInterfaces {
	interface Draggable {...}
	interace DragTarget {...}
}

````



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0ODE5ODc4NDYsMTE3ODg5ODI3MSwtOD
M5ODU2MDg3LC0xMzMyOTExMDg2LC0xMzk0MzYxNDEzLDIwNzA1
OTA5NjksODQ0NDE5Nzc2LDQ1MDQxOTMwOCwxMDcxMDcwMTIwLC
0xOTU4NTczOTYzLDEwMTM5MDUyMzcsMTcwNDQwMjgxNywxMTQ0
MzM2NzQzLC0zMjMxMTkwNTQsNjM1ODc5ODIxLDEwNjMzMTYzMz
ksMTczNDY3Mzc5MCw2NzA3OTA1OTIsMTYyMzYzNDQyNyw2Mzkx
NTUyMTRdfQ==
-->