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

### Alternative Props Syntaxes

Can bring an import with the component with all the structures inside

````
<CoreConcept
title={CORE_CONCEPTS[0].title}
description={CORE_CONCEPTS[0].description}
img={CORE_CONCEPTS[0].image}
/>
````
This is cumbersome if you have to do it multiple times, do this instead:

````
<CoreConcept  {...CORE_CONCEPTS[0]} />
````

There is other way to write the component:
````
function  CoreConcept(props) {
	return (
		<li>
		<img  src={props.image}  alt={props.title}  />
		<h3>{props.title}</h3>
		<p>{props.description}</p>
		</li>
	);
}

// other way
function  CoreConcept({image, title, description}) {
	return (
		<li>
		<img  src={image}  alt={title}  />
		<h3>{title}</h3>
		<p>{description}</p>
		</li>
	);
}
````

### More Prop Syntaxes

Beyond the various ways of setting and extracting props about which you learned in the previous lecture, there are  **even more ways of dealing**  with props.

But no worries, you'll see all these different features & syntaxes in action throughout the course!

**Passing a Single Prop Object**

If you got data that's already organized as a JavaScript object, you can pass that object as a single prop value instead of splitting it across multiple props.

I.e., instead of

1.  <CoreConcept
2.    title={CORE_CONCEPTS[0].title}
3.    description={CORE_CONCEPTS[0].description}  
4.    image={CORE_CONCEPTS[0].image}  />

or

1.  <CoreConcept
2.   {...CORE_CONCEPTS[0]} />

you could also pass a single  `concept`  (or any name of your choice) prop to the  `CoreConcept`  component:

1.  <CoreConcept
2.    concept={CORE_CONCEPTS[0]}  />

In the  `CoreConcept`  component, you would then get that one single prop:

1.  export  default  function  CoreConcept({  concept  })  {
2.    // Use concept.title, concept.description etc.
3.    // Or destructure the concept object: const { title, description, image } = concept;
4.  }

It is entirely up to you which syntax & approach you prefer.

**Grouping Received Props Into a Single Object**

You can also pass multiple props to a component and then, in the component function, group them into a single object via JavaScript's  ["Rest Property"](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#rest_property)  syntax.

I.e., if a component is used like this:

1.  <CoreConcept
2.    title={CORE_CONCEPTS[0].title}
3.    description={CORE_CONCEPTS[0].description}  
4.    image={CORE_CONCEPTS[0].image}  />

You could group the received props into a single object like this:

1.  export  default  function  CoreConcept({  ...concept  })  {  
2.    // ...concept groups multiple values into a single object
3.    // Use concept.title, concept.description etc.
4.    // Or destructure the concept object: const { title, description, image } = concept;
5.  }

If that syntax is a bit confusing - worry not! You'll also see concrete examples for this syntax (and for why you might want to use it in certain situations) throughout the course!

**Default Prop Values**

Sometimes, you'll build components that may receive an optional prop. For example, a custom  `Button`  component may receive a  `type`  prop.

So the Button component should be usable either with a type being set:

1.  <Button  type="submit"  caption="My Button"  />

Or without it:

1.  <Button  caption="My Button"  />

To make this component work, you might want to set a default value for the  `type`  prop - in case it's not passed.

This can easily be achieved since JavaScript supports default values when using object destructuring:

1.  export  default  function  Button({ caption, type =  "submit"  })  {  
2.    // caption has no default value, type has a default value of "submit"
3.  }

### Best Practice: Storing Components in Files

Use a foulder to store components, and import them

### Storing Component Style files next to Components

Want to split the CSS file into the components

Put CSS of the component into a file next to it and import it to the component

**The CSS styles are scoped for everything not only the component**

Create a foulder with the .jsx and .css of the component

### Component Composition: The Special children Prop

Children: Prop set by react, is not an atribbute, it refer to the content between the component tags

````
export  default  function  TabButton(props) {
	return (
		<li><button>{props.children}</button></li>
	)
}

// app.jsx

<section  id="examples">
	<h2>Examples</h2>
	<menu>
		<TabButton>Component<TabButton/> // Component Button
	</menu>
</section>
````

Also you can:

````
export  default  function  TabButton({label}) {
	return (
		<li><button>{label}</button></li>
	)
}

// app.jsx

<section  id="examples">
	<h2>Examples</h2>
	<menu>
		<TabButton label='Components'/>
	</menu>
</section>
````

### Reacting to Events

````
export  default  function  TabButton(props) {
	function  handleClick() {
		console.log('Hello World');
	}

	return (
		<li>
			<button  onClick={handleClick}>{props.children}</button> // only point to the function
		</li>
	);
}
````

### Passing Functions as Values to Props

To add dynamic content to different clicks:
````
//button.jsx
export  default  function  TabButton({ children, onSelect }) {
	return (
		<li>
			<button  onClick={onSelect}>{children}</button>
		</li>
		);
}

// app.jsx
function  App() {
	function  handleSelect() {
	console.log('Hello World');
	}
	return (
	...
		<section  id="examples">
		<h2>Examples</h2>
			<menu>
				<TabButton  onSelect={handleSelect}>Component</TabButton>
				<TabButton  onSelect={handleSelect}>JSX</TabButton>
				<TabButton  onSelect={handleSelect}>Props</TabButton>
				<TabButton  onSelect={handleSelect}>State</TabButton>
			</menu>
		</section>
	</main>
	</div>
	);
}
````

### Passing Custom Arguments to Event Functions

````
function  App() {
function  handleSelect(selectedButton) {
console.log(selectedButton);
}
return (
...
<section  id="examples">
<h2>Examples</h2>
	<menu>
		<TabButton  onSelect={() =>  handleSelect("Component")}>
		Component
		</TabButton>
		<TabButton  onSelect={() =>  handleSelect("JSX")}>JSX</TabButton>
		<TabButton  onSelect={() =>  handleSelect("Props")}>Props</TabButton>
		<TabButton  onSelect={() =>  handleSelect("State")}>State</TabButton>
	</menu>
</section>
</main>
</div>
);
}
````

### How not to update UI

By default, react components execute only once, need to say if you want to execute more than once

### Managing State & Using Hooks

State: registering variables

Rules of hooks:

 - Only work inside components
 - Only calls on top level

````
import { useState } from  'react'; // react hooks

function  App() {

const [selectedTopic, setSelectedTopic] =  useState("Please Click a button"); // need to call in the top level

function  handleSelect(selectedButton) {
setSelectedTopic(selectedButton);
}

return (
...
<section  id="examples">
	<h2>Examples</h2>
	<menu>
		<TabButton  onSelect={() =>  handleSelect("Component")}>
		Component
		</TabButton>
		<TabButton  onSelect={() =>  handleSelect("JSX")}>JSX</TabButton>
		<TabButton  onSelect={() =>  handleSelect("Props")}>Props</TabButton>
		<TabButton  onSelect={() =>  handleSelect("State")}>State</TabButton>
	</menu>
	{selectedTopic} // inserted dinamically
</section>
</main>
</div>
);
}
````
Manage State:
````
const [ counter, setCounter] =  userState(0);
counter: Current State Value, may change when component is executed again
userState(0): initial state value
setCounter: State updating function, update the stored value and tell react to re execute
````

**The component execute the stage at the end**

### Deriving & Outputting Data Based on Stage

````
// dinamic entry
<div  id="tab-content">
	<h3>{EXAMPLES[selectedTopic].title}</h3>
	<p>{EXAMPLES[selectedTopic].description}</p>
	<pre>
		<code>{EXAMPLES[selectedTopic].code}</code>
	</pre>
</div>
````

### Rendering Content Conditionally

````
{!selectedTopic ? (<p>Please select a Topic</p>
) : (
<div  id="tab-content">
	<h3>{EXAMPLES[selectedTopic].title}</h3>
	<p>{EXAMPLES[selectedTopic].description}</p>
	<pre>
		<code>{EXAMPLES[selectedTopic].code}</code>
	</pre>
</div>
)}
````

There is two other ways to do it, search them if you need it, most common is to write an if statement before the component, and set the variable in the component

### CSS Styling & Dynamic  Styling

Selected tab highlighted

````
// button.jsx
export  default  function  TabButton({ children, onSelect, isSelected }) {
	return (
		<li>
		<button  className={isSelected ? "active" : ""}  onClick={onSelect}>
		{children}
		</button>
		</li>
		);
}

// app.jsx
<menu>
<TabButton
isSelected={selectedTopic === "Component"}
onSelect={() =>  handleSelect("Component")}
>Component</TabButton>
<TabButton
isSelected={selectedTopic === "JSX"}
onSelect={() =>  handleSelect("JSX")}
>JSX</TabButton>
<TabButton
isSelected={selectedTopic === "Props"}
onSelect={() =>  handleSelect("Props")}
>Props</TabButton>
<TabButton
isSelected={selectedTopic === "State"}
onSelect={() =>  handleSelect("State")}
>State</TabButton>
````

### Output List Data Dinamically

If the data is change, potentially can break the page
Put the cuantity of elements dynamically
````
Instead of:
<CoreConcept  {...CORE_CONCEPTS[0]}  />
<CoreConcept  {...CORE_CONCEPTS[1]}  />
<CoreConcept  {...CORE_CONCEPTS[2]}  />
<CoreConcept  {...CORE_CONCEPTS[3]}  />

Change to this:
{CORE_CONCEPTS.map((conceptItem) =>  <CoreConcept  key={conceptItem.title}  {...conceptItem}  />)} // generate dinynamically depending the amount of elements
````

## React Deep Dive

### You dont have to use JSX

Can write code without making the components:
````
Instead of:
ReactDOM.createRoot(entryPoint).render(<App />);

Can change it to:
import React from 'react';
ReactDOM.createRoot(entryPoint).render(React.createElement(App));
````

### Working with fragements

JSX components has to have an element parent
The return of the function has to have only one element

Use Fractent to wrap the sibling components:

Instead of `<div>` only use `<>`

### When you should split comments

In this case, the two component of main, interact with the refresher and we dont want to, so we have to split

### Splitting Components by Feature & State

The CoreConcepts and the example into different jsx files

The app file look like this now:
````
function  App() {
	return (
		<>
			<Header  />
			<main>
				<CoreConcepts  />
				<Examples  />
			</main>
		</>
	);
}
````

Now example is executed when you clic but not components

### Problem: Props are not Forwarded to Inner Elements

When you are setting props on a custom component those settings are not automatically forwarded to the jsx code inside

### Forwarding Props to Wrapped Elements

All extra props are set to the component
````
export  default  function  Section({ title, children, ...props }) {
	return (
		<section  {...props}>
			<h2>{title}</h2>
			{children}
		</section>
		);
}
````

Also with the onClick, put ...props in the component, and change the prop to OnClick

### Working with Multiple JSX Slots

Use like a blue print:
````
export  default  function  Tabs({ children, buttons }) {
	return (
		<>
		<menu>{buttons}</menu>
		{children}
		</>
	);
}
Then adjust the Example.jsx with this blue print
````

### Setting Component Types Dynamically

Use different wrappers dynamically in the component

````
	export  default  function  Tabs({ children, buttons, ButtonsContainer }) { // uppercase needed
	return (
		<>
		<ButtonsContainer>{buttons}</ButtonsContainer>
		{children}
		</>
		);
}

The put ButtonsContainer = 'menu' in the example
````

### Setting Default Prop Values

````
xport  default  function  Tabs({ children, buttons, ButtonsContainer='menu'}) // default 
	return (
		<>
		<ButtonsContainer>{buttons}</ButtonsContainer>
		{children}
		</>
		);
}
````

### Not all content must go into components

If you have static data, you can put it right on the HTML

````
<body>
	<header> // static data
		<img  src="game-logo.png"  alt="Hand-Drawn Tic Tac Toe game board"  />
		<h1>Tic-Tac-Toe</h1>
	</header>
	<div  id="root"></div>
	<script  type="module"  src="/src/index.jsx"></script>
</body>
````

### Closer Look: public/ vs assets/ for Image Storage

#### The public/ Folder

As shown in the previous lecture you can store images in the  `public/`  folder and then  **directly reference**  them from inside your  `index.html`  or  `index.css`  files.

The reason for that is that images (or, in general: files) stored in  `public/` are made  **publicly available**  by the underlying project development server & build process. Just like  `index.html`, those files can directly be visited from inside the browser and can therefore also be requested by other files.

If you try loading  `localhost:5173/some-image.jpg`, you'll be able to see that image (if it exists in the  `public/`  folder, of course).

#### The src/assets/ Folder

You can also store images in the  `src/assets/`  folder (or, actually, anywhere in the  `src`  folder).

So what's the difference compared to  `public/`?

Any files (of any format) stored in  `src`  (or subfolders like  `src/assets/`) are  **not made available to the public**. They can't be accessed by website visitors. If you try loading  `localhost:5173/src/assets/some-image.jpg`, you'll get an error.

Instead, files stored in  `src/`  (and subfolders) can be used in your code files. Images imported into code files are then picked up by the underlying build process, potentially optimized, and kind of  _"injected"_  into the  `public/`  folder right before serving the website. Links to those images are automatically generated and used in the places where you referenced the imported images.

#### Which Folder Should You Use?

You should use the  `public/`  folder for any images that should  **not be handled by the build process**  and that should be  **generally available**. Good candidates are images used directly in the  `index.html`  file or favicons.

On the other hand, images that are used  **inside of components**  should typically be stored in the  `src/`  folder (e.g., in  `src/assets/`).

### Component work in isolation	

If you reuse a component, only the component you try to change, make the change

### Updating State Base on Old Stage





<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg1Mzk4Mjk3NiwtMTY2OTQwNjcwNSwxOT
I1NDcwMjE0LDg5MTc4MzEwLDExMjUzNjI3OTAsMjA1ODUwOTg5
MCwtNDk1MjMxNjQ0LC0zMjYxMTE4OTQsLTE3NzIyNDE4LDE5MT
g2MTY1MTAsMjEwMDMwOTg5NywtNDcxMTc3MTk3LDE5OTg2NzQ4
MDAsLTE5OTAyOTk1NjMsMTc0MjA4MzQxNCwtNDM3NDY4NTQ5LD
gzODU2NzQ5NywtNDE1MTA3OTY4LC00ODExNjk1MTMsMTc3ODY2
MjVdfQ==
-->