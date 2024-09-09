# React Course

## Getting Started

React is a library for building interfaces - A JS Library

### React vs JS

React - Update the UI automatically
With React you define the target UI state - not the steps to get there

### Creating React Project

`react.new` in google -environment for React Projects

or use VSC 

or https://create-react-app.dev/

Need to install Vite to use React

## React Essentials

### Components

UI Building Blocks

Advantajes:

 - Reusable building blocks
 - HTML, CSS y JS code are stored togheter
 - Different component handle different data & logic
 - Simplify working with bigger apps

### JSX & React Component

JSX: Javascript Syntax Extension
Used to describe and create HTML elements in JS
Files with .jsx notation

React Component: is a function with two rules:

 - Name start with Uppercase character
 - Return renderable content

````
function  App() {
return (
	<div>
	<header>
	<img  src="src/assets/react-core-concepts.png"  alt="Stylized atom"  />
	<h1>React Essentials</h1>
	<p>
	Fundamental React concepts you will need for almost any app you are
going to build!
	</p>
	</header>
	<main>
	<h2>Time to get started!</h2>
	</main>
	</div>
);
}
````

### First Custom Component

````
function  Header() { // custom component
	return (
		<header>
		<img  src="src/assets/react-core-concepts.png"  		alt="Stylized atom"  /> // here need the / too
		<h1>React Essentials</h1>
		<p>
		Fundamental React concepts you will need for almost any app you are going to build!
		</p>
		</header>
	);
}

function  App() {
	return (
		<div>
		<Header  /> // need the / , the component is added here
		<main>
		<h2>Time to get started!</h2>
		</main>
		</div>
	);
}

export  default  App;
````
### Build a Component Tree

The index.jsx file doent content componets, it is the entry point for the htlm

````
// index.jsx
import  ReactDOM  from  "react-dom/client";
import  App  from  "./App.jsx";
import  "./index.css";

const  entryPoint  =  document.getElementById("root"); // root is a div
ReactDOM.createRoot(entryPoint).render(<App  />);
````

A tree of components : starts with App and you can add subcomponents

### Using and Outputting Dinamyc Values

````
const  reactDescriptions  = ["Fundamental", "Crucial", "Core"];

function  getRandomInt(max) {
	return  Math.floor(Math.random() * (max  +  1));
}

function  Header() {
	return (
		<header>
		<img  src="src/assets/react-core-concepts.png"  alt="Stylized atom"  />
		<h1>React Essentials</h1>
		<p>
			{reactDescriptions[getRandomInt(2)]} React concepts you will need for
almost any app you are going to build!
		</p>
		</header>
	);
}
````
Use {} to enter dinamyc Values

Also to make it leaner:

````
function  Header() {
	const description = reactDescriptions[getRandomInt(2)];
	return (
		<header>
		<img  src="src/assets/react-core-concepts.png"  alt="Stylized atom"  />
		<h1>React Essentials</h1>
		<p>
			{description} React concepts you will need for
almost any app you are going to build!
		</p>
		</header>
	);
}
````

### Setting HTLM Atribbutes Dynamically & Loading Image Files

How to load images:

````
import  reactImg  from  './assets/react-core-concepts.png';

function  Header() {
	const  description  =  reactDescriptions[getRandomInt(2)];
	return (
		<header>
		<img  src={reactImg}  alt="Stylized atom"  />
		<h1>React Essentials</h1>
		<p>
			{description} React concepts you will need for almost any app you are
going to build!
		</p>
		</header>
	);
}
````

### Component Reusable with Props

We can use component as we want and as many times as we want

How to reuse component with Props:

````
function  CoreConcept(props) {
	return (
		<li>
		<img  src={props.img}  alt={props.title}  />
		<h3>{props.title}</h3>
		<p>{props.description}</p>
		</li>
	);
}

function  App() {
	return (
		<div>
		<Header  />
		<main>
		<section  id="core-concepts">
		<h2>Core Concepts</h2>
		<ul>
		<CoreConcept
		title="Components"
		description="The core UI building block"
		img={componetsImg}
		/>
		<CoreConcept  />
		<CoreConcept  />
		<CoreConcept  />
		</ul>
		</section>
		</main>
		</div>
	);
}
````


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM2NTI4OTQ4MSwtOTIyMzk3MDAsMjA2Nz
AyODY4MywxMjYwNjE1NDI4LC02ODAzNzQ1OTAsLTEyODY3NzU3
MzQsLTExMTQ0MTA4ODQsODIyNTM0NTQsMTc0ODcxNTMxNywtMj
UxMzcyNDY5LDIxNDU2NzUwNzksMTkzMzUxMjc5OSwtOTE4NjE2
MDAyLDk0NjUyMzg0NSwtMTkzNDIxMjY5NiwxNDYyMzIwODQ0LC
01ODIxNzg1NzcsLTE3MjEwNTU1MjAsLTYyODM3OTAyNiwtOTk0
NjgwMjQ2XX0=
-->