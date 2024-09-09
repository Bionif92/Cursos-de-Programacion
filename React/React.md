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
import  ReactDOM  from  "react-dom/client";

  

import  App  from  "./App.jsx";

import  "./index.css";

  

const  entryPoint  =  document.getElementById("root");

ReactDOM.createRoot(entryPoint).render(<App  />);
````
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5NDEwNzkzMCw4MjI1MzQ1NCwxNzQ4Nz
E1MzE3LC0yNTEzNzI0NjksMjE0NTY3NTA3OSwxOTMzNTEyNzk5
LC05MTg2MTYwMDIsOTQ2NTIzODQ1LC0xOTM0MjEyNjk2LDE0Nj
IzMjA4NDQsLTU4MjE3ODU3NywtMTcyMTA1NTUyMCwtNjI4Mzc5
MDI2LC05OTQ2ODAyNDZdfQ==
-->