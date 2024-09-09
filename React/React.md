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
function  Header() {
return (
<header>
<img  src="src/assets/react-core-concepts.png"  alt="Stylized atom"  />
<h1>React Essentials</h1>
<p>
Fundamental React concepts you will need for almost any app you are
going to build!
</p>
</header>
);
}
````
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk0NzQxMjI1NywyMTQ1Njc1MDc5LDE5Mz
M1MTI3OTksLTkxODYxNjAwMiw5NDY1MjM4NDUsLTE5MzQyMTI2
OTYsMTQ2MjMyMDg0NCwtNTgyMTc4NTc3LC0xNzIxMDU1NTIwLC
02MjgzNzkwMjYsLTk5NDY4MDI0Nl19
-->