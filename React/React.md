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

Assure that you work with the latest available state
````
const [isEditing, setIsEditing] =  useState(false);

function  handleEditClick() {
	setIsEditing((editing) =>  !editing); // to the oposite
}
````

### User Input & Two-Way-Binding

````
const [playerName, setPlayerName] =  useState(initialName);

function  handleChange(event) {
	setPlayerName(event.target.value);
}

if (isEditing) {
	editablePlayerName  = (
		<input  type="text"  required  value={playerName}  onChange={handleChange}  />
	);
	buttonCaption  =  "Save";
}
````

### Update Object State Immutably

Object or Array: Create a copy and change this one

````
function  handleSelectSquare(rowIndex, colIndex) {
	setGameBoard((prevGameBoard) => {
		const  updatedBoard  = [...prevGameBoard.map(innerArray  => [...innerArray])]; // create a copy
		updatedBoard[rowIndex][colIndex] =  'X';
		return  updatedBoard;
	});
}
````

### Lifting State Up

Two component that need the state of the player simultaneously, how?

**Lifting the state up**
Need to get the state to the closest ancestor, this case, the app.jsx

### Avoid Merging States

Create a constant inside the state to se the other state

### Deriving State

Generate a state, here for the turns, and with that information, fill the information for the Gameboard without needing an own state for that

### Reducing State Managment & Identifiying Unnecesary State

See if all the components are related and use only once, state, then use the information of that state to update the information to the others

### Dissabling Buttons Conditionally

````
<button
onClick={() =>  onSelectSquare(rowIndex, colIndex)}
disabled={playerSymbol !== null} // the condition
>
````

### Why Immutability Matters

To restart the game, he need the original copy of the board, so we need to make a deep copy to play the game, and when restart make a copy again:

````
let  gameBoard  = [...initialGameBoard.map((array) => [...array])];
````

### Final Polishing

Gererate function ouside the main component if you can

Generate general variables like INITIAL_GAME_BOARD

## Practice Project

Change the value on the screen with the prop value
````
<input  type="number"  required  value={userInput.initialInvestment}  onChange={(event) =>  handleChange('initialInvestment',event.target.value)}/>
````

The value of an event is always a string, need to change it to number if you need to make mathematical operations:

````
function  handleChange(inputIdentifier, newValue) {
	setUserInput((prevUserInput) => {
		return {
			...prevUserInput,
			[inputIdentifier]:  +newValue, // transform to number 
		};
	});
}
````

## Styling React Components

### Splitting CSS code across multiple files

Vite identify the css file that you will use in the project

You can split the css files and put them next to the files that use it : need to put the import of the css into the component

### Props & Cons of using vanilla CSS

Advantajes:

 - CSS code is separated of JSX code
 - CSS code can be written by other develop with minimun access to JSX

Disadvantajes:

 - Need to kwon CSS
 - CSS rules may clash across components

### Vanilla CSS Styles are not scoped to components

The CSS are scoped globally to the page if they are not specific

### Styling React Apps with Inline Styles

Dynamically:
````
export  default  function  Header() {
	return (
		<header>
			<img  src={logo}  alt="A canvas"  />
			<h1>ReactArt</h1>
			<p style={{
				color: 'red',
				textAlign: 'left'
			}}>A community of artists and art-lovers.</p>
		</header>
	);
}
````
Apply only to the thing you put the style

Disadvantage: 

 - need to style every element individually
 - no separation between JSX & CSS

### Dynamic & Conditional Inline Styles

````
style={{
backgroundColor:  emailNotValid ? '#fed2d2' : '#d1d5db'
}}
````

### Dynamic & Conditional Styling with CSS Files & CSS Classes

Adding class dynamically
````
<label  className={`label ${emailNotValid ? 'invalid' : ''}`}>Email</label> // label is a permanent class, invalid is conditional
````

### Scoping CSS Rules with CSS Modules

CSS Modules: Vanilla CSS with file-specific scoping

`.module.css` needed

````
import  classes  from  "./Header.module.css";

export  default  function  Header() {
	return (
		<header>
			<img  src={logo}  alt="A canvas"  />
			<h1>ReactArt</h1>
			<p  className={classes.paragraph}>
			A community of artists and art-lovers.
			</p>
		</header>
	);
}
````

### Introducing Styled Components (Third-Party Package)

https://styled-components.com/

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#tagged_templates

````
// terminal
npm install styled-components

//.jsx
import { styled } from  'styled-components';

const  ControlContainer  =  styled.div` // important the tag
display: flex;
flex-direction: column;
gap: 0.5rem;
margin-bottom: 1.5rem;
`

return (
	<ControlContainer>
	</ControlContainer>
);
````

If you want you can import them like the components to use them wherever you want

### Creating Flexible Components with Styled Components

````
const  Label  =  styled.label`
display: block;
margin-bottom: 0.5rem;
font-size: 0.75rem;
font-weight: 700;
letter-spacing: 0.1em;
text-transform: uppercase;
color: #6b7280;
`;

<Label  className={`label ${emailNotValid ? "invalid" : ""}`}>
````

### Dynamic & Conditional Styling with Styled Components

````
const  Label  =  styled.label`
display: block;
margin-bottom: 0.5rem;
font-size: 0.75rem;
font-weight: 700;
letter-spacing: 0.1em;
text-transform: uppercase;
color: ${({ $invalid }) => ($invalid ? "#f87171" : "#6b7280")};
`;

<Label  $invalid={emailNotValid}>Email</Label>
````

````
const  Input  =  styled.input`
width: 100%;
padding: 0.75rem 1rem;
line-height: 1.5;
background-color: ${({ $invalid }) => ($invalid ? "#fed2d2" : "#d1d5db")};
color: ${({ $invalid }) => ($invalid ? "#ef4444" : "#374151")};
border-color: ${({ $invalid }) => ($invalid ? "#f73f3f" : "undefined")}
border: 1px solid transparent;
border-radius: 0.25rem;
box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
`;

<Input
	$invalid={passwordNotValid}
	type="email"
	onChange={(event) =>  handleInputChange("email", event.target.value)}
/>
````

Be careful, the $ is not to clash the props

### Styled Components: Pseudo Selectors, Nested Rules & Media Queries

````
const  StyleHeader  =  styled.header`

display: flex;
flex-direction: column;
align-items: center;
justify-content: center;
margin-top: 2rem;
margin-bottom: 2rem;

& img {
object-fit: contain;
margin-bottom: 2rem;
width: 11rem;
height: 11rem;
}

@media (min-width: 768px) {
	& {
	margin-bottom: 4rem;
	}
		& h1 {
		font-size: 2.25rem;
		}
		}

`;
````
For pseudo:
````
const  Button  =  styled.button`
padding: 1rem 2rem;
font-weight: 600;
text-transform: uppercase;
border-radius: 0.25rem;
color: #1f2937;
background-color: #f0b322;
border-radius: 6px;
border: none;

&:hover {
background-color: #f0920e;
}
`;
````

### Creating Reusable Components & Component Combinations

Put styled CSS into separated files, if they are related you can do this:

````
import { styled } from  "styled-components"

const  Label  =  styled.label`
...
`;

const  Input  =  styled.input`
...
`;

export default function  CustomInput ( {label, invalid, ...props} ) {
	return  <p>
		<Label  $invalid={invalid}>{label}</Label>
		<Input  $invalid={invalid}  {...props}/>
	</p>
}
````
If there is one thing to export you can use default:
`export default Button`

### Introducing Tailwind CSS For React App Styling

CSS Framework

Dont need to know CSS to use it

https://tailwindcss.com/docs/guides/vite

Inportant to see the Docs

````
//terminal
npm install -D tailwindcss postcss autoprefixernpx tailwindcss init -p

// tailwind.config.js
/** @type  {import('tailwindcss').Config} */
export  default {
content: [
"./index.html",
"./src/**/*.{js,ts,jsx,tsx}",
],
theme: {
extend: {},
},
plugins: [],
}

//index.css
@tailwind base;  
@tailwind components;  
@tailwind utilities;

// jsx
export  default  function  Header() {
	return (
		<header  className="flex flex-col items-center mt-8 mb-16">
			<img  src={logo}  alt="A canvas"  className="mb-8 w-44 h-44 object-contain"/>
			<h1  className="text-4xl font-semibold tracking-widest text-center uppercase text-amber-800">ReactArt</h1>
			<p>A community of artists and art-lovers.</p>
		</header>
	);
}
````

### Adding & Using Tailwind CSS In A React Project

Add an external font:

````
// tailwind.config.js
/** @type  {import('tailwindcss').Config} */
export  default {
content: [
"./index.html",
"./src/**/*.{js,ts,jsx,tsx}",
],
theme: {
extend: {
	fontFamily: {
		title: ['"Pacifico"', 'cursive']
	}
},
},
plugins: [],
}

You can use the font-title now
````

### Tailwind: Media Queries & Pseudo Selectors

Search Responsive Design to see the shortcuts to write them

`hover:class` inside the className

### Dynamic & Conditional Styling with Tailwind

````
export default function Input () {
let labelClasses = "classes1"

if(invalid) {
	lableClasses = "classes2"
}
	return(
	className= {labelClasses}
	)
}

````

### Tailwind CSS: Pros & Cons

Work really well with React because you can reuse the components with the classes

Dont have clashes between components because you dont define css rules

Cons:

 - Long class names values
 - Any style changes need editing JSX

## Debbuging React Apps

### Understanding React Error Messages

See the first message error, and where it get the error

### Using the Browser Debugger & Breakpoints

If it is a logical error, that doesnt make an output in the console:

Browser/ Sources Tab -  Set Breakpoints

### Understanding React's "Strict Mode"

````
// index.jsx
import { StrictMode } from 'react';

ReactDOM.createRoot(document.getElementById('root')).render(<StrictMode><App  /></StrictMode>);
````

Execute every component twice in development: make you see if there is a problem in the app

### Using the React DevTools

Extension React Devtool in chrome - already installed

Two new pages in the Borwser Dev Tool

For findinx and fixing performance issues

 - Component: can see your component tree

## Working with Ref & Portals

### Introducing Refs: Connecting & Accessing HTML Elements via Refs

Ref: object that can connect to jsx elements

````
import { useState, useRef } from 'react';

export default function Player() {
  const playerName = useRef();

  const [enteredPlayerName, setEnteredPlayerName] = useState(null);
  
  function handleClick() {
    setEnteredPlayerName(playerName.current.value); // with current you have the current status of the input object
  }

  return (
    <section id="player">
      <h2>Welcome {enteredPlayerName ?? 'unknown entity'} </h2> // output the same value
      <p>
        <input
          ref={playerName}
          type="text"
        />
        <button onClick={handleClick}>Set Name</button>
      </p>
    </section>
  );
}
````

### Manipulating the DOM via Refs

If you want to not change the dom, need to make a copy

### Refs vs State Values

Need state to make the conection to ref

State: causes component re evaluation when changed
Should be used for values that are directly reflected in the UI

Ref: Not cause a component re evaluation
Can be used to gain access to DOM elements

### Using Refs for More Than "DOM Element Connections"

````
import { useState, useRef } from 'react';

// let timer; // will be shared with all the components, not what we want

export default function TimerChallenge({ title, targetTime }) {
  const timer = useRef();

  const [timerStarted, setTimerStarted] = useState(false);
  const [timerExpired, setTimerExpired] = useState(false);

  function handleStart() {
    timer.current = setTimeout(() => {
      setTimerExpired(true);
    }, targetTime * 1000);

    setTimerStarted(true);
  }

  function handleStop() {
    clearTimeout(timer.current); // stop the timer
  }

  return (
    <section className="challenge">
      <h2>{title}</h2>
      {timerExpired && <p>You lost!</p>}
      <p className="challenge-time">
        {targetTime} second{targetTime > 1 ? 's' : ''}
      </p>
      <p>
        <button onClick={timerStarted ? handleStop : handleStart}>
          {timerStarted ? 'Stop' : 'Start'} Challenge
        </button>
      </p>
      <p className={timerStarted ? 'active' : undefined}>
        {timerStarted ? 'Time is running...' : 'Timer inactive'}
      </p>
    </section>
  );
}
````

### Forwarding Refs to Custom Components

To show the modal
````
// TimerChallenge.jsx
import { useState, useRef } from 'react';

import ResultModal from './ResultModal.jsx';

// let timer;

export default function TimerChallenge({ title, targetTime }) {
  const timer = useRef();
  const dialog = useRef();

  const [timerStarted, setTimerStarted] = useState(false);
  const [timerExpired, setTimerExpired] = useState(false);

  function handleStart() {
    timer.current = setTimeout(() => {
      setTimerExpired(true);
      dialog.current.showModal(); // browser feature
    }, targetTime * 1000);

    setTimerStarted(true);
  }

  function handleStop() {
    clearTimeout(timer.current);
  }

  return (
    <>
      <ResultModal ref={dialog} targetTime={targetTime} result="lost" /> // foward the ref
      <section className="challenge">
        <h2>{title}</h2>
        <p className="challenge-time">
          {targetTime} second{targetTime > 1 ? 's' : ''}
        </p>
        <p>
          <button onClick={timerStarted ? handleStop : handleStart}>
            {timerStarted ? 'Stop' : 'Start'} Challenge
          </button>
        </p>
        <p className={timerStarted ? 'active' : undefined}>
          {timerStarted ? 'Time is running...' : 'Timer inactive'}
        </p>
      </section>
    </>
  );
}

//Modal.jsx
import { forwardRef } from 'react'; // this 

const ResultModal = forwardRef(function ResultModal({ result, targetTime }, ref) { // ref outside the props
  return (
    <dialog ref={ref} className="result-modal">
      <h2>You {result}</h2>
      <p>
        The target time was <strong>{targetTime} seconds.</strong>
      </p>
      <p>
        You stopped the timer with <strong>X seconds left.</strong>
      </p>
      <form method="dialog">
        <button>Close</button>
      </form>
    </dialog>
  );
})

export default ResultModal;
````

### Exposing Component APIs via the useImperativeHandle Hook

Hook to define properties or method that can be used outside

````
import { forwardRef, useImperativeHandle, useRef } from 'react';

const ResultModal = forwardRef(function ResultModal({ result, targetTime }, ref) {
  const dialog = useRef();

  useImperativeHandle(ref, () => {
    return {
      open() {
        dialog.current.showModal();
      }
    };
  }); // use open() intead of showmodal() in the other component

  return (
    <dialog ref={dialog} className="result-modal">
      <h2>You {result}</h2>
      <p>
        The target time was <strong>{targetTime} seconds.</strong>
      </p>
      <p>
        You stopped the timer with <strong>X seconds left.</strong>
      </p>
      <form method="dialog">
        <button>Close</button>
      </form>
    </dialog>
  );
})

export default ResultModal;
````

### Introducing & Understanding "Portals"

Teleport an element in the dom, in this case the modal

````
import { forwardRef, useImperativeHandle, useRef } from 'react';
import { createPortal } from 'react-dom'; // this

const ResultModal = forwardRef(function ResultModal(
  { targetTime, remainingTime, onReset },
  ref
) {
  const dialog = useRef();

  const userLost = remainingTime <= 0;
  const formattedRemainingTime = (remainingTime / 1000).toFixed(2);
  const score = Math.round((1 - remainingTime / (targetTime * 1000)) * 100);

  useImperativeHandle(ref, () => {
    return {
      open() {
        dialog.current.showModal();
      },
    };
  });

  return createPortal(
    <dialog ref={dialog} className="result-modal">
      {userLost && <h2>You lost</h2>}
      {!userLost && <h2>Your Score: {score}</h2>}
      <p>
        The target time was <strong>{targetTime} seconds.</strong>
      </p>
      <p>
        You stopped the timer with{' '}
        <strong>{formattedRemainingTime} seconds left.</strong>
      </p>
      <form method="dialog" onSubmit={onReset}>
        <button>Close</button>
      </form>
    </dialog>,
    document.getElementById('modal')
  );
});

export default ResultModal;
````

## React Context API & useReducer - Advanced Stage Managment

### Understanding Prop Drilling & Project Overview

Prop Drilling: Passing shared data through multiple components layers

Cumbersome to use this way

### Prop Drilling: Component Composition as a Solution

Component Composition: move the content of the next component into a wrapper of the root component

````
 return (
    <>
      <Header
        cart={shoppingCart}
        onUpdateCartItemQuantity={handleUpdateCartItemQuantity}
      />
      <Shop> // get rid of the prop
        {DUMMY_PRODUCTS.map((product) => (
          <li key={product.id}>
            <Product {...product} onAddToCart={handleAddItemToCart} /> // this part
          </li>
        ))}
      </Shop>
    </>
  );
}
````
Need to modify the imports too and use the wrapper as a children in the next component

### Introducing the Context API

Shared data between component more easily

Create a Cart Context that wrap all components, and we can use the State

### Creating & Providing The Context

Create `store` Foulder:

````
// shopping-cart-context.jsx
import { createContext } from 'react';

export const CartContext = createContext({
  items: []
});

// App.jsx
import { CartContext } from './store/shopping-cart-context.jsx';

return (
    <CartContext.Provider> // the wrapper
      <Header
        cart={shoppingCart}
        onUpdateCartItemQuantity={handleUpdateCartItemQuantity}
      />
      <Shop>
        {DUMMY_PRODUCTS.map((product) => (
          <li key={product.id}>
            <Product {...product} onAddToCart={handleAddItemToCart} />
          </li>
        ))}
      </Shop>
    </CartContext.Provider>
  );
````

### Consuming the Context

````
// Cart.jsx
import { useContext } from 'react';
import { CartContext } from '../store/shopping-cart-context.jsx';

export default function Cart({ onUpdateItemQuantity }) { // get rid of the item prop
  const { items } = useContext(CartContext); // establish the connection, destructure the constant

  const totalPrice = items.reduce(
    (acc, item) => acc + item.price * item.quantity,
    0
  );
  const formattedTotalPrice = `$${totalPrice.toFixed(2)}`;

  return (
    <div id="cart">
      {items.length === 0 && <p>No items in cart!</p>}
      {items.length > 0 && (
        <ul id="cart-items">
          {items.map((item) => {
            const formattedPrice = `$${item.price.toFixed(2)}`;

            return (
              <li key={item.id}>
                <div>
                  <span>{item.name}</span>
                  <span> ({formattedPrice})</span>
                </div>
                <div className="cart-item-actions">
                  <button onClick={() => onUpdateItemQuantity(item.id, -1)}>
                    -
                  </button>
                  <span>{item.quantity}</span>
                  <button onClick={() => onUpdateItemQuantity(item.id, 1)}>
                    +
                  </button>
                </div>
              </li>
            );
          })}
        </ul>
      )}
      <p id="cart-total-price">
        Cart Total: <strong>{formattedTotalPrice}</strong>
      </p>
    </div>
  );
}

// App.jsx
return (
    <CartContext.Provider value={{ items: [] }}> // add this
      <Header
        cart={shoppingCart}
        onUpdateCartItemQuantity={handleUpdateCartItemQuantity}
      />
      <Shop>
        {DUMMY_PRODUCTS.map((product) => (
          <li key={product.id}>
            <Product {...product} onAddToCart={handleAddItemToCart} />
          </li>
        ))}
      </Shop>
    </CartContext.Provider>
  );
````

### Linking the Context to State

````
// App.jsx
function App() {
  const [shoppingCart, setShoppingCart] = useState({
    items: [],
  });
    const ctxValue = {
    items: shoppingCart.items,
    addItemToCart: handleAddItemToCart // add functions for use in the components
  };
	return (
    <CartContext.Provider value={ctxValue}>
      <Header
        cart={shoppingCart}
        onUpdateCartItemQuantity={handleUpdateCartItemQuantity}
      />
      <Shop>
        {DUMMY_PRODUCTS.map((product) => (
          <li key={product.id}>
            <Product {...product} onAddToCart={handleAddItemToCart} />
          </li>
        ))}
      </Shop>
    </CartContext.Provider>
  );
}

// Product.jsx
import { useContext } from 'react';

import { CartContext } from '../store/shopping-cart-context.jsx';

export default function Product({ id, image, title, price, description }) { // delete the addproduct from prop
  const { addItemToCart } = useContext(CartContext); // if you want autocomplition, put the function in the original file of context

  return (
    <article className="product">
      <img src={image} alt={title} />
      <div className="product-content">
        <div>
          <h3>{title}</h3>
          <p className="product-price">${price}</p>
          <p>{description}</p>
        </div>
        <p className="product-actions">
          <button onClick={() => addItemToCart(id)}>Add to Cart</button>
        </p>
      </div>
    </article>
  );
}
````

### A Different Way Of Consuming Context

CartContext.Consumer

Other way of writting the code
It is more harder to read

### What Happens When Context Values Change?

The context will re execute when it changes, also the things inside the context

### Outsourcing Context & State Into a Separate Provider Component

Take the things inside the app like functions and constants to the context to make it leaner:

Useful when you have more context in a bigger app

````
// shopping-cart-context.jsx
import { createContext, useState } from 'react';

import { DUMMY_PRODUCTS } from '../dummy-products.js';

export const CartContext = createContext({
  items: [],
  addItemToCart: () => {},
  updateItemQuantity: () => {},
});

export default function CartContextProvider({children}) {
  const [shoppingCart, setShoppingCart] = useState({
    items: [],
  });

  function handleAddItemToCart(id) {
    setShoppingCart((prevShoppingCart) => {
      const updatedItems = [...prevShoppingCart.items];

      const existingCartItemIndex = updatedItems.findIndex(
        (cartItem) => cartItem.id === id
      );
      const existingCartItem = updatedItems[existingCartItemIndex];

      if (existingCartItem) {
        const updatedItem = {
          ...existingCartItem,
          quantity: existingCartItem.quantity + 1,
        };
        updatedItems[existingCartItemIndex] = updatedItem;
      } else {
        const product = DUMMY_PRODUCTS.find((product) => product.id === id);
        updatedItems.push({
          id: id,
          name: product.title,
          price: product.price,
          quantity: 1,
        });
      }

      return {
        items: updatedItems,
      };
    });
  }

  function handleUpdateCartItemQuantity(productId, amount) {
    setShoppingCart((prevShoppingCart) => {
      const updatedItems = [...prevShoppingCart.items];
      const updatedItemIndex = updatedItems.findIndex(
        (item) => item.id === productId
      );

      const updatedItem = {
        ...updatedItems[updatedItemIndex],
      };

      updatedItem.quantity += amount;

      if (updatedItem.quantity <= 0) {
        updatedItems.splice(updatedItemIndex, 1);
      } else {
        updatedItems[updatedItemIndex] = updatedItem;
      }

      return {
        items: updatedItems,
      };
    });
  }

  const ctxValue = {
    items: shoppingCart.items,
    addItemToCart: handleAddItemToCart,
    updateItemQuantity: handleUpdateCartItemQuantity,
  };

  return <CartContext.Provider value={ctxValue}> // need to add this return
    {children}
  </CartContext.Provider>
}

// App.jsx
import Header from './components/Header.jsx';
import Shop from './components/Shop.jsx';
import Product from './components/Product.jsx';
import { DUMMY_PRODUCTS } from './dummy-products.js';
import CartContextProvider from './store/shopping-cart-context.jsx';

function App() {
  return (
    <CartContextProvider>
      <Header />
      <Shop>
        {DUMMY_PRODUCTS.map((product) => (
          <li key={product.id}>
            <Product {...product} />
          </li>
        ))}
      </Shop>
    </CartContextProvider>
  );
}

export default App;
````

### Introducing the useReducer Hook

Reducer: A hook to reduce multiple tasks to a function that can be call depending of type of action we need

```` context.jsx
-- import { createContext, useState, useReducer } from 'react';

import { DUMMY_PRODUCTS } from '../dummy-products.js';

export const CartContext = createContext({
  items: [],
  addItemToCart: () => {},
  updateItemQuantity: () => {},
});

-- function shoppingCartReducer(state, action) { // this function has not to be recreated when re execute
  return state;
}

export default function CartContextProvider({ children }) {
  -- const [shoppingCartState, shoppingCartDispatch] = useReducer(
    shoppingCartReducer,
    {
      items: [],
    } // initial state
  );

  const [shoppingCart, setShoppingCart] = useState({
    items: [],
  });

  function handleAddItemToCart(id) {
    setShoppingCart((prevShoppingCart) => {
      const updatedItems = [...prevShoppingCart.items];

      const existingCartItemIndex = updatedItems.findIndex(
        (cartItem) => cartItem.id === id
      );
      const existingCartItem = updatedItems[existingCartItemIndex];

      if (existingCartItem) {
        const updatedItem = {
          ...existingCartItem,
          quantity: existingCartItem.quantity + 1,
        };
        updatedItems[existingCartItemIndex] = updatedItem;
      } else {
        const product = DUMMY_PRODUCTS.find((product) => product.id === id);
        updatedItems.push({
          id: id,
          name: product.title,
          price: product.price,
          quantity: 1,
        });
      }

      return {
        items: updatedItems,
      };
    });
  }

  function handleUpdateCartItemQuantity(productId, amount) {
    setShoppingCart((prevShoppingCart) => {
      const updatedItems = [...prevShoppingCart.items];
      const updatedItemIndex = updatedItems.findIndex(
        (item) => item.id === productId
      );

      const updatedItem = {
        ...updatedItems[updatedItemIndex],
      };

      updatedItem.quantity += amount;

      if (updatedItem.quantity <= 0) {
        updatedItems.splice(updatedItemIndex, 1);
      } else {
        updatedItems[updatedItemIndex] = updatedItem;
      }

      return {
        items: updatedItems,
      };
    });
  }

  const ctxValue = {
    -- items: shoppingCartState.items,
    addItemToCart: handleAddItemToCart,
    updateItemQuantity: handleUpdateCartItemQuantity,
  };

  return (
    <CartContext.Provider value={ctxValue}>{children}</CartContext.Provider>
  );
}
````

### Dispatching Actions & Editing State with useReducer

````
import { createContext, useReducer } from 'react';

import { DUMMY_PRODUCTS } from '../dummy-products.js';

export const CartContext = createContext({
  items: [],
  addItemToCart: () => {},
  updateItemQuantity: () => {},
});

--function shoppingCartReducer(state, action) { // we will have the latest state action
  if (action.type === 'ADD_ITEM') {
    const updatedItems = [...state.items];

    const existingCartItemIndex = updatedItems.findIndex(
      (cartItem) => cartItem.id === action.payload
    );
    const existingCartItem = updatedItems[existingCartItemIndex];

    if (existingCartItem) {
      const updatedItem = {
        ...existingCartItem,
        quantity: existingCartItem.quantity + 1,
      };
      updatedItems[existingCartItemIndex] = updatedItem;
    } else {
      const product = DUMMY_PRODUCTS.find(
        (product) => product.id === action.payload
      );
      updatedItems.push({
        id: action.payload,
        name: product.title,
        price: product.price,
        quantity: 1,
      });
    }

    return {
      ...state, // not needed here because we have only one value
      items: updatedItems,
    };
  }

  if (action.type === 'UPDATE_ITEM') {
    const updatedItems = [...state.items];
      const updatedItemIndex = updatedItems.findIndex(
        (item) => item.id === action.payload.productId
      );

      const updatedItem = {
        ...updatedItems[updatedItemIndex],
      };

      updatedItem.quantity += action.payload.amount;

      if (updatedItem.quantity <= 0) {
        updatedItems.splice(updatedItemIndex, 1);
      } else {
        updatedItems[updatedItemIndex] = updatedItem;
      }

      return {
        ...state,
        items: updatedItems,
      };
  }
  return state;
}

export default function CartContextProvider({ children }) {
  const [shoppingCartState, shoppingCartDispatch] = useReducer(
    shoppingCartReducer,
    {
      items: [],
    }
  );

 -- function handleAddItemToCart(id) {
    shoppingCartDispatch({
      type: 'ADD_ITEM',
      payload: id,
    });
  }

  -- function handleUpdateCartItemQuantity(productId, amount) {
    shoppingCartDispatch({
      type: 'UPDATE_ITEM',
      payload: {
        productId,
        amount
      }
    });
  }

  const ctxValue = {
    -- items: shoppingCartState.items,
    addItemToCart: handleAddItemToCart,
    updateItemQuantity: handleUpdateCartItemQuantity,
  };

  return (
    <CartContext.Provider value={ctxValue}>{children}</CartContext.Provider>
  );
}
````
See project 4 to understand it more how to use it

With this, you dont have to write the (prevState => ....) function everytime, you will have the state updated

Can use Reducer without Context

## Handling Side Effects & Working with the useEffect() Hook

### What's a "Side Effect"? A Thorough Example

Are tasks that dont impact the current component render cycle

````
// App.jsx
navigator.geolocation.getCurrentPosition((position) => {
      const sortedPlaces = sortPlacesByDistance(
        AVAILABLE_PLACES,
        position.coords.latitude,
        position.coords.longitude
      );
````
This is a side effect because we need it, but no to render the jsx code

### A Potential Problem with Side Effects: An Infinite Loop

````
const [availablePlaces, setAvailablePlaces] = useState([]);

navigator.geolocation.getCurrentPosition((position) => {
      const sortedPlaces = sortPlacesByDistance(
        AVAILABLE_PLACES,
        position.coords.latitude,
        position.coords.longitude
      );

      setAvailablePlaces(sortedPlaces);
    });

return (
<Places
          title="Available Places"
          --places={availablePlaces}
          fallbackText="Sorting places by distance..."
          onSelectPlace={handleSelectPlace}
        />
      </main>
)
````

This will cause an infinte loop, because it will change the state when it finish to get the location

### Using useEffect for Handling (Some) Side Effects

````
--import { useRef, useState, useEffect } from 'react';

 useEffect(() => {
    navigator.geolocation.getCurrentPosition((position) => {
      const sortedPlaces = sortPlacesByDistance(
        AVAILABLE_PLACES,
        position.coords.latitude,
        position.coords.longitude
      );

      setAvailablePlaces(sortedPlaces);
    });
  }, []); // second argument - array of dependencies

<Places
          title="Available Places"
          places={availablePlaces}
          fallbackText="Sorting places by distance..." // fallback text while waiting for the data
          onSelectPlace={handleSelectPlace}
        />
````

With this the function will be executed after the execution of all the component function

If the array of dependecies changes, it re execute the function

### Not All Side Effects Need useEffect

````
function handleSelectPlace(id) {
    setPickedPlaces((prevPickedPlaces) => {
      if (prevPickedPlaces.some((place) => place.id === id)) {
        return prevPickedPlaces;
      }
      const place = AVAILABLE_PLACES.find((place) => place.id === id);
      return [place, ...prevPickedPlaces];
    });

   -- const storedIds = JSON.parse(localStorage.getItem('selectedPlaces')) || []; // to store the changes
    if (storedIds.indexOf(id) === -1) {
      localStorage.setItem(
        'selectedPlaces',
        JSON.stringify([id, ...storedIds])
      );
    }
  }
````

This storage can be a side effect, but it is only executed when you add an image to the selected place

Also you cant use hooks inside nested functions

**If there is no promise, no need to use side effect because the data you get will be instantly**

**If you need to update the state to have the first value, an use the function, you can use side effect to run it after you have the first data**

### Understanding Effect Dependencies

Are props or state, and also could be fuctions or context that depedent on props or state

````
import { useRef, useEffect } from 'react';
import { createPortal } from 'react-dom';

function Modal({ open, children, onClose }) {
  const dialog = useRef();

  --useEffect(() => {
    if (open) {
      dialog.current.showModal();
    } else {
      dialog.current.close();
    }
  }, [open]); // open is the dependency

  return createPortal(
    <dialog className="modal" ref={dialog} onClose={onClose}>
      {children}
    </dialog>,
    document.getElementById('modal')
  );
}

export default Modal;
````

###  Introducing useEffect's Cleanup Function

````
import { useEffect } from 'react';

export default function DeleteConfirmation({ onConfirm, onCancel }) {
  useEffect(() => {
    console.log('TIMER SET');
    const timer = setTimeout(() => {
      onConfirm();
    }, 3000);

    --return () => { // cleaner
      console.log('Cleaning up timer');
      clearTimeout(timer);
    };
  }, []); // need dependecy

  return (
    <div id="delete-confirmation">
      <h2>Are you sure?</h2>
      <p>Do you really want to remove this place?</p>
      <div id="confirmation-actions">
        <button onClick={onCancel} className="button-text">
          No
        </button>
        <button onClick={onConfirm} className="button">
          Yes
        </button>
      </div>
    </div>
  );
}
````

### The Problem with Object & Function Dependencies

The previous lecture need a dependecy, in that case was a function

The side effect will re execute when the function change
Function are object, and will re execute when the component run
Two look alike objects are not the same

### The useCallback Hook

You dont re create the function with useCallback, when passing functions to a dependency of sideeffect

````
import { useRef, useState, useEffect, useCallback } from 'react';

const handleRemovePlace = useCallback(function handleRemovePlace() {
    setPickedPlaces((prevPickedPlaces) =>
      prevPickedPlaces.filter((place) => place.id !== selectedPlace.current)
    );
    setModalIsOpen(false);

    const storedIds = JSON.parse(localStorage.getItem('selectedPlaces')) || [];
    localStorage.setItem(
      'selectedPlaces',
      JSON.stringify(storedIds.filter((id) => id !== selectedPlace.current))
    );
  }, []); // dependecies needed too if they have
````

### useEffect's Cleanup Function: Another Example

````
import { useEffect, useState } from 'react';

const TIMER = 3000;

export default function DeleteConfirmation({ onConfirm, onCancel }) {
  const [remainingTime, setRemainingTime] = useState(TIMER);

  useEffect(() => {
    const interval = setInterval(() => {
      console.log('INTERVAL');
      setRemainingTime((prevTime) => prevTime - 10);
    }, 10);

    return () => {
      clearInterval(interval);
    };
  }, []);

  useEffect(() => {
    console.log('TIMER SET');
    const timer = setTimeout(() => {
      onConfirm();
    }, TIMER);

    return () => {
      console.log('Cleaning up timer');
      clearTimeout(timer);
    };
  }, [onConfirm]);

  return (
    <div id="delete-confirmation">
      <h2>Are you sure?</h2>
      <p>Do you really want to remove this place?</p>
      <div id="confirmation-actions">
        <button onClick={onCancel} className="button-text">
          No
        </button>
        <button onClick={onConfirm} className="button">
          Yes
        </button>
      </div>
      --<progress value={remainingTime} max={TIMER} />
    </div>
  );
}
````

### Optimizing State Updates

The state of the previous bar is better to put it in a different component, not to re execute all the root component, and get slower

## Project : Building a Quiz App

**Important: to restart the QuestionTimer you need to use the prop key and set it to a different value everytime**

Avoid the use of useEffect as possible in your project

**To shuffle the answers he made a new component and give a key prop to re shuffle**

**He group the component that need a key into a bigger component with only one key, because react doesnt like more than one unique key**

Cannot use key as a prop

Update the timer of the bar if the answer was selected

**Index is better key than the answer because if you skipped an answer twice, you have two keys with the same value. Is not recommended if you swap the result because the index will be the same for that question**

## Look Behind the Scenes of React & Optimization Techniques

### How React Works Behind The Scenes

React creates a tree of components

### Analyzing Component Function Executions via React's DevTools Profiler

React Dev Tool - Profiler: can see the execution of every component while are changing

### Avoiding Component Function Executions with memo()

Not to re render all the component only for a single thing, use memo

Memo will look at the props and if the new is the same as the old, it not re render
````
--import { useState, memo, useCallback, useMemo } from 'react';

import IconButton from '../UI/IconButton.jsx';
import MinusIcon from '../UI/Icons/MinusIcon.jsx';
import PlusIcon from '../UI/Icons/PlusIcon.jsx';
import CounterOutput from './CounterOutput.jsx';
import { log } from '../../log.js';

function isPrime(number) {
  log('Calculating if is prime number', 2, 'other');

  if (number <= 1) {
    return false;
  }

  const limit = Math.sqrt(number);

  for (let i = 2; i <= limit; i++) {
    if (number % i === 0) {
      return false;
    }
  }

  return true;
}

--const Counter = memo(function Counter({ initialCount }) {
  log('<Counter /> rendered', 1);

  const initialCountIsPrime = useMemo(() => isPrime(initialCount), [initialCount]);

  const [counter, setCounter] = useState(initialCount);

  const handleDecrement = useCallback(function handleDecrement() {
    setCounter((prevCounter) => prevCounter - 1);
  }, []);

  const handleIncrement = useCallback(function handleIncrement() {
    setCounter((prevCounter) => prevCounter + 1);
  }, []);

  return (
    <section className="counter">
      <p className="counter-info">
        The initial counter value was <strong>{initialCount}</strong>. It{' '}
        <strong>is {initialCountIsPrime ? 'a' : 'not a'}</strong> prime number.
      </p>
      <p>
        <IconButton icon={MinusIcon} onClick={handleDecrement}>
          Decrement
        </IconButton>
        <CounterOutput value={counter} />
        <IconButton icon={PlusIcon} onClick={handleIncrement}>
          Increment
        </IconButton>
      </p>
    </section>
  );
});

--export default Counter;
````

Dont overuse memo: Use it as high in the component as possible
Checking props with memo cost performance
Dont use it in component where props will change frecuently

### Avoiding Component Function Executions with Clever Structuring

Try to move the thing that changes everytime to a component

### Understanding the useCallback() Hook

If you have functions in the component, it will re render the function and memo will not work

Use useCallback to not re render a function

### Understanding the useMemo() Hook

UseMemo to not re render normal functions inside de component function
The function will only re execute if one of the dependencies change
````
import { useState, memo, useCallback, useMemo } from 'react';

//Inside component
const initialCountIsPrime = useMemo(() => isPrime(initialCount), [initialCount]);
````

**`useMemo`  caches the return value of a function.  `useCallback`  caches the function definition itself.**

### React Uses A Virtual DOM

Only update the things that are changed
See the snapshot of the tree, and the things that are changed, it change the dom

### Why Keys Matter When Managing State!

If you copy a component, the state is scoped to each component, they dont share it

React tracks state by component type & position in the tree

With key you map the state to a concrete instance, use the reference to key to something that not change, like id

### More Reasons For Why Keys Matter

If you dont use key, they will re render all the items every time

### Using Keys For Resetting Components

To re render a component you can use a key that changes when the value is changed

### State Scheduling & Batching

The state is updated is scheduled, that why you use prevState in the function to update it one after the other

If you have more than one change of state on a function, they are batched, it will lead to an only run of the component

### Optimizing React with MillionJS

https://million.dev/

Can make react faster

Use automatic mode

````
//bash
npm install million

Change the vite file with the script they made
````

## Class Based Components

Alternative to functions
Class based components cant use hooks

### Adding a First Class-based Component

````
import { Component } from 'react';

class User extends Component {
  render() {
    return <li className={classes.user}>{this.props.name}</li>;
  } 
}

export default User;
````
Render the same as result in function component

### Working with State & Events

````
import { Component } from 'react';

class Users extends Component {
  constructor() {
    super();
    this.state = { // always an object
      showUsers: true,
      more: 'Test',
    };
  }

  toggleUsersHandler() { // update the state
    // this.state.showUsers = false; // NOT!
    this.setState((curState) => {
      return { showUsers: !curState.showUsers };
    });
  }

  render() {
    const usersList = (
      <ul>
        {DUMMY_USERS.map((user) => (
          <User key={user.id} name={user.name} />
        ))}
      </ul>
    );

    return (
      <div className={classes.users}>
        <button onClick={this.toggleUsersHandler.bind(this)}>
          {this.state.showUsers ? 'Hide' : 'Show'} Users
        </button>
        {this.state.showUsers && usersList}
      </div>
    );
  }
}

export default Users;
````

### The Component Lifecycle

LifeCycle methods overwrite the hooks in class based components

Equivalents:
componentDidMount() -- UseEffect() with no dependecies 
componentDidUpdate() -- UseEffect() with dependecies 
componentWillUnmount() -- clean up function of UseEffect

### Lifecycle Methods In Action

````
import { Fragment, useState, useEffect, Component } from 'react';

import Users from './Users';
import classes from './UserFinder.module.css';

const DUMMY_USERS = [
  { id: 'u1', name: 'Max' },
  { id: 'u2', name: 'Manuel' },
  { id: 'u3', name: 'Julie' },
];

class UserFinder extends Component {
  constructor() {
    super();
    this.state = {
      filteredUsers: [],
      searchTerm: '',
    };
  }

  componentDidMount() {
    // Send http request...
    this.setState({ filteredUsers: DUMMY_USERS });
  }

  componentDidUpdate(prevProps, prevState) {
    if (prevState.searchTerm !== this.state.searchTerm) {
      this.setState({
        filteredUsers: DUMMY_USERS.filter((user) =>
          user.name.includes(this.state.searchTerm)
        ),
      });
    }
  }

  searchChangeHandler(event) {
    this.setState({ searchTerm: event.target.value });
  }

  render() {
    return (
      <Fragment>
        <div className={classes.finder}>
          <input type='search' onChange={this.searchChangeHandler.bind(this)} />
        </div>
        <Users users={this.state.filteredUsers} />
      </Fragment>
    );
  }
}

export default UserFinder;
````

### Class-based Components & Context

Less flexible, one context for one component
````
//context.js
import React from 'react';

const UsersContext = React.createContext({
  users: []
});

export default UsersContext;

// Component
import { Fragment, useState, useEffect, Component } from 'react';

import Users from './Users';
import classes from './UserFinder.module.css';
import UsersContext from '../store/users-context';

class UserFinder extends Component {
 -- static contextType = UsersContext;

  constructor() {
    super();
    this.state = {
      filteredUsers: [],
      searchTerm: '',
    };
  }

  componentDidMount() {
    // Send http request...
    this.setState({ filteredUsers: this.context.users });
  }

  componentDidUpdate(prevProps, prevState) {
    if (prevState.searchTerm !== this.state.searchTerm) {
      this.setState({
        filteredUsers: this.context.users.filter((user) =>
          user.name.includes(this.state.searchTerm)
        ),
      });
    }
  }

  searchChangeHandler(event) {
    this.setState({ searchTerm: event.target.value });
  }

  render() {
    return (
      <Fragment>
        <div className={classes.finder}>
          <input type='search' onChange={this.searchChangeHandler.bind(this)} />
        </div>
        <Users users={this.state.filteredUsers} />
      </Fragment>
    );
  }
}
````

### Introducing  Errors Boundaries

If you want to generate an error to have the information 
To catch the error and not to crash the application
````
//errorboundary.js
import { Component } from 'react';

class ErrorBoundary extends Component {
  constructor() {
    super();
    this.state = { hasError: false };
  }

  componentDidCatch(error) {
    console.log(error);
    this.setState({ hasError: true });
  }

  render() {
    if (this.state.hasError) {
      return <p>Something went wrong!</p>;
    }
    return this.props.children;
  }
}

export default ErrorBoundary;

// userfinder.js
import { Fragment, useState, useEffect, Component } from 'react';

import Users from './Users';
import classes from './UserFinder.module.css';
import UsersContext from '../store/users-context';
--import ErrorBoundary from './ErrorBoundary';

class UserFinder extends Component {
  static contextType = UsersContext;

  constructor() {
    super();
    this.state = {
      filteredUsers: [],
      searchTerm: '',
    };
  }

  componentDidMount() {
    // Send http request...
    this.setState({ filteredUsers: this.context.users });
  }

  componentDidUpdate(prevProps, prevState) {
    if (prevState.searchTerm !== this.state.searchTerm) {
      this.setState({
        filteredUsers: this.context.users.filter((user) =>
          user.name.includes(this.state.searchTerm)
        ),
      });
    }
  }

  searchChangeHandler(event) {
    this.setState({ searchTerm: event.target.value });
  }

  render() {
    return (
      <Fragment>
        <div className={classes.finder}>
          <input type='search' onChange={this.searchChangeHandler.bind(this)} />
        </div>
        --<ErrorBoundary>
          <Users users={this.state.filteredUsers} />
        </ErrorBoundary>
      </Fragment>
    );
  }
}

export default UserFinder;
````

## Sending HTTP Requests

### How (Not) To Connect To A Database

You can not directly access to a database because of security issues

Need a Backend, and you connect to that with http request

### Sending HTTP Requests (GET Request) via useEffect

Cant use async in components of React
````
import { useState, useEffect } from 'react';

import Places from './Places.jsx';

export default function AvailablePlaces({ onSelectPlace }) {
  const [availablePlaces, setAvailablePlaces] = useState([]);

  useEffect(() => {
    fetch('http://localhost:3000/places')
      .then((response) => {
        return response.json();
      })
      .then((resData) => {
        setAvailablePlaces(resData.places);
      });
  }, []);

  return (
    <Places
      title="Available Places"
      places={availablePlaces}
      fallbackText="No places available."
      onSelectPlace={onSelectPlace}
    />
  );
}
````
This for the images to render
````
export default function Places({ title, places, fallbackText, onSelectPlace }) {
  console.log(places);
  return (
    <section className="places-category">
      <h2>{title}</h2>
      {places.length === 0 && <p className="fallback-text">{fallbackText}</p>}
      {places.length > 0 && (
        <ul className="places">
          {places.map((place) => (
            <li key={place.id} className="place-item">
              <button onClick={() => onSelectPlace(place)}>
                --<img src={`http://localhost:3000/${place.image.src}`} alt={place.image.alt} />
                <h3>{place.title}</h3>
              </button>
            </li>
          ))}
        </ul>
      )}
    </section>
  );
}
````

### Using async / await

````
useEffect(() => {
	async function fetchPlaces() {
		const response = await fetch('http://localhost:3000/places');
		const resData = await response.json();
		setAvailablePlaces(resData.places);
	}
	fetchPlaces();
}, []);
````

### Handling Loading States

Create fallbacks with the props

Also managing loading stage:

````
import { useState, useEffect } from 'react';

import Places from './Places.jsx';
import Error from './Error.jsx';

export default function AvailablePlaces({ onSelectPlace }) {
  --const [isFetching, setIsFetching] = useState(false);
  const [availablePlaces, setAvailablePlaces] = useState([]);
  const [error, setError] = useState();

  useEffect(() => {
    async function fetchPlaces() {
      --setIsFetching(true);

      try {
        const response = await fetch('http://localhost:3000/places');
        const resData = await response.json();

        if (!response.ok) {
          throw new Error('Failed to fetch places');
        }

        setAvailablePlaces(resData.places);
      } catch (error) {
        setError({
          message:
            error.message || 'Could not fetch places, please try again later.',
        });
      }

      --setIsFetching(false);
    }

    fetchPlaces();
  }, []);

  if (error) {
    return <Error title="An error occurred!" message={error.message} />;
  }

  return (
    <Places
      title="Available Places"
      places={availablePlaces}
      --isLoading={isFetching}
      --loadingText="Fetching place data..."
      fallbackText="No places available."
      onSelectPlace={onSelectPlace}
    />
  );
}
````

### Handling HTTP Errors

````
import { useState, useEffect } from 'react';

import Places from './Places.jsx';
import Error from './Error.jsx';

export default function AvailablePlaces({ onSelectPlace }) {
  const [isFetching, setIsFetching] = useState(false);
  const [availablePlaces, setAvailablePlaces] = useState([]);
 -- const [error, setError] = useState();

  useEffect(() => {
    async function fetchPlaces() {
      setIsFetching(true);

      --try {
        const response = await fetch('http://localhost:3000/places');
        const resData = await response.json();

        if (!response.ok) { // ok is a property
          throw new Error('Failed to fetch places');
        }

        setAvailablePlaces(resData.places);
      } --catch (error) {
        setError({
          message:
            error.message || 'Could not fetch places, please try again later.',
        });
      }

      setIsFetching(false);
    }

    fetchPlaces();
  }, []);

  if (error) {
    return <Error title="An error occurred!" message={error.message} />;
  }

  return (
    <Places
      title="Available Places"
      places={availablePlaces}
      isLoading={isFetching}
      loadingText="Fetching place data..."
      fallbackText="No places available."
      onSelectPlace={onSelectPlace}
    />
  );
}
````

### Transforming Fetched Data

Using the position of the user also
````
useEffect(() => {
    async function fetchPlaces() {
      setIsFetching(true);

      try {
        const places = await fetchAvailablePlaces();

        --navigator.geolocation.getCurrentPosition((position) => {
          const sortedPlaces = sortPlacesByDistance(
            places,
            position.coords.latitude,
            position.coords.longitude
          );
          setAvailablePlaces(sortedPlaces);
          setIsFetching(false); // double 
        });
      } catch (error) {
        setError({
          message:
            error.message || 'Could not fetch places, please try again later.',
        });
        setIsFetching(false); // double, because of the outcome
      }
    }

    fetchPlaces();
  }, []);
````

### Extracting Code & Improving Code Structure

Can put the fetch data code into a new file

### Sending Data with POST Requests

````
export async function updateUserPlaces(places) {
  const response = await fetch('http://localhost:3000/user-places', {
    method: 'PUT',
    body: JSON.stringify({ places }), // shorten notation for places: places
    headers: {
      'Content-Type': 'application/json',
    },
  });

  const resData = await response.json();

  if (!response.ok) {
    throw new Error('Failed to update user data.');
  }

  return resData.message;
}
````
In the app.js
````
async function handleSelectPlace(selectedPlace) {
    setUserPlaces((prevPickedPlaces) => {
      if (!prevPickedPlaces) {
        prevPickedPlaces = [];
      }
      if (prevPickedPlaces.some((place) => place.id === selectedPlace.id)) {
        return prevPickedPlaces;
      }
      return [selectedPlace, ...prevPickedPlaces];
    });

    --try {
      await updateUserPlaces([selectedPlace, ...userPlaces]);
    } catch (error) {
      // ...
    }
  }
````

### Using Optimistic Updating

Can update the state and at the same time sending the http request

````
const [errorUpdatingPlaces, setErrorUpdatingPlaces] = useState();

async function handleSelectPlace(selectedPlace) {
    // await updateUserPlaces([selectedPlace, ...userPlaces]);

    setUserPlaces((prevPickedPlaces) => {
      if (!prevPickedPlaces) {
        prevPickedPlaces = [];
      }
      if (prevPickedPlaces.some((place) => place.id === selectedPlace.id)) {
        return prevPickedPlaces;
      }
      return [selectedPlace, ...prevPickedPlaces];
    });

    try {
      await updateUserPlaces([selectedPlace, ...userPlaces]);
    } catch (error) {
      setUserPlaces(userPlaces); // if crash go back to the previous state
      setErrorUpdatingPlaces({
        message: error.message || 'Failed to update places.',
      });
    }
  }
````

### Deleting Data (via DELETE HTTP Requests)

````
 const handleRemovePlace = useCallback(
    async function handleRemovePlace() {
      setUserPlaces((prevPickedPlaces) =>
        prevPickedPlaces.filter(
          (place) => place.id !== selectedPlace.current.id
        )
      );

      try {
        await updateUserPlaces(
          userPlaces.filter((place) => place.id !== selectedPlace.current.id)
        );
      } catch (error) {
        setUserPlaces(userPlaces);
        setErrorUpdatingPlaces({
          message: error.message || 'Failed to delete place.',
        });
      }

      setModalIsOpen(false);
    },
    [userPlaces]
  );
````

### Fetching User Data

````
//http.js
export async function updateUserPlaces(places) {
  const response = await fetch('http://localhost:3000/user-places', {
    method: 'PUT',
    body: JSON.stringify({ places }),
    headers: {
      'Content-Type': 'application/json',
    },
  });

  const resData = await response.json();

  if (!response.ok) {
    throw new Error('Failed to update user data.');
  }

  return resData.message;
}
````
````
//app.js
import { useRef, useState, useCallback, useEffect } from 'react';

import Places from './components/Places.jsx';
import Modal from './components/Modal.jsx';
import DeleteConfirmation from './components/DeleteConfirmation.jsx';
import logoImg from './assets/logo.png';
import AvailablePlaces from './components/AvailablePlaces.jsx';
import { fetchUserPlaces, updateUserPlaces } from './http.js';
import Error from './components/Error.jsx';

function App() {
  const selectedPlace = useRef();

  const [userPlaces, setUserPlaces] = useState([]);
  --const [isFetching, setIsFetching] = useState(false);
  --const [error, setError] = useState();

  const [errorUpdatingPlaces, setErrorUpdatingPlaces] = useState();

  const [modalIsOpen, setModalIsOpen] = useState(false);

  --useEffect(() => {
    async function fetchPlaces() {
      setIsFetching(true);
      try {
        const places = await fetchUserPlaces();
        setUserPlaces(places);
      } catch (error) {
        setError({ message: error.message || 'Failed to fetch user places.' });
      }

      setIsFetching(false);
    }

    fetchPlaces();
  }, []);

  function handleStartRemovePlace(place) {
    setModalIsOpen(true);
    selectedPlace.current = place;
  }

  function handleStopRemovePlace() {
    setModalIsOpen(false);
  }

  async function handleSelectPlace(selectedPlace) {
    // await updateUserPlaces([selectedPlace, ...userPlaces]);

    setUserPlaces((prevPickedPlaces) => {
      if (!prevPickedPlaces) {
        prevPickedPlaces = [];
      }
      if (prevPickedPlaces.some((place) => place.id === selectedPlace.id)) {
        return prevPickedPlaces;
      }
      return [selectedPlace, ...prevPickedPlaces];
    });

    try {
      await updateUserPlaces([selectedPlace, ...userPlaces]);
    } catch (error) {
      setUserPlaces(userPlaces);
      setErrorUpdatingPlaces({
        message: error.message || 'Failed to update places.',
      });
    }
  }

  const handleRemovePlace = useCallback(
    async function handleRemovePlace() {
      setUserPlaces((prevPickedPlaces) =>
        prevPickedPlaces.filter(
          (place) => place.id !== selectedPlace.current.id
        )
      );

      try {
        await updateUserPlaces(
          userPlaces.filter((place) => place.id !== selectedPlace.current.id)
        );
      } catch (error) {
        setUserPlaces(userPlaces);
        setErrorUpdatingPlaces({
          message: error.message || 'Failed to delete place.',
        });
      }

      setModalIsOpen(false);
    },
    [userPlaces]
  );

  function handleError() {
    setErrorUpdatingPlaces(null);
  }

  return (
    <>
      <Modal open={errorUpdatingPlaces} onClose={handleError}>
        {errorUpdatingPlaces && (
          <Error
            title="An error occurred!"
            message={errorUpdatingPlaces.message}
            onConfirm={handleError}
          />
        )}
      </Modal>

      <Modal open={modalIsOpen} onClose={handleStopRemovePlace}>
        <DeleteConfirmation
          onCancel={handleStopRemovePlace}
          onConfirm={handleRemovePlace}
        />
      </Modal>

      <header>
        <img src={logoImg} alt="Stylized globe" />
        <h1>PlacePicker</h1>
        <p>
          Create your personal collection of places you would like to visit or
          you have visited.
        </p>
      </header>
      <main>
        --{error && <Error title="An error occurred!" message={error.message} />}
        {!error && (
          <Places
            title="I'd like to visit ..."
            fallbackText="Select the places you would like to visit below."
            --isLoading={isFetching}
            --loadingText="Fetching your places..."
            places={userPlaces}
            onSelectPlace={handleStartRemovePlace}
          />
        )}

        <AvailablePlaces onSelectPlace={handleSelectPlace} />
      </main>
    </>
  );
}

export default App;
````

## Building Custom React Hooks

Rules of Hooks:

 - Only inside components
 - Call them on the top level

With the first one, it is more flexible than that

### Creating a Custom Hook

Foulder Hooks

The function need to start with `use`
````
import { useEffect, useState } from 'react';

export function useFetch(fetchFn, initialValue) {
  const [isFetching, setIsFetching] = useState();
  const [error, setError] = useState();
  const [fetchedData, setFetchedData] = useState(initialValue); // this one is the generic 

  useEffect(() => {
    async function fetchData() {
      setIsFetching(true);
      try {
        const data = await fetchFn();
        setFetchedData(data);
      } catch (error) {
        setError({ message: error.message || 'Failed to fetch data.' });
      }

      setIsFetching(false);
    }

    fetchData();
  }, [fetchFn]);

  return {
    isFetching,
    fetchedData,
    error
  }
}
````
Use useFetch() wherever you need
Delete the state on the component
Use object destructuring to have the return state
Can rename the destructuring with allias `{fetch: places}`

### Exposing Nested Functions From The Custom Hook

Cannot use function that change the state that is inside the custom hook, how to solve it: **add them into the return of the custom hook**

### Using A Custom Hook in Multiple Components

Thats the idea

### Creating Flexible Custom Hooks

Converting a non promise to a promise:

````
async function fetchSortedPlaces() {
  const places = await fetchAvailablePlaces();

  return new Promise((resolve) => {
    navigator.geolocation.getCurrentPosition((position) => {
      const sortedPlaces = sortPlacesByDistance(
        places,
        position.coords.latitude,
        position.coords.longitude
      );

      resolve(sortedPlaces);
    });
  });
}
````
This one goes to the custom hook


## Working with Forms & User Input

### What Are Forms & What's Tricky About Them?

Need:

 - Form Submission : relatively easy , can use state or ref, or via FormData
 - Input Validation : this one is tricky

### Handling Form Submission

By default buttons in form make an http request when clicked
````
export default function Login() {
  function handleSubmit(event) {
    event.preventDefault();
    console.log('Submitted!');
  }

  return (
    <form onSubmit={handleSubmit}> // need it here 
      <h2>Login</h2>

      <div className="control-row">
        <div className="control no-margin">
          <label htmlFor="email">Email</label>
          <input id="email" type="email" name="email" />
        </div>

        <div className="control no-margin">
          <label htmlFor="password">Password</label>
          <input id="password" type="password" name="password" />
        </div>
      </div>

      <p className="form-actions">
        <button className="button button-flat">Reset</button>
        <button className="button">
          Login
        </button>
      </p>
    </form>
  );
}
````
How to prevent the submit:
With type="button" in htlm
Or preventDafault()

### Managing & Getting User Input via State & Generic Handlers

````
import { useState } from 'react';

export default function Login() {
  // const [enteredEmail, setEnteredEmail] = useState('');
  // const [enteredPassword, setEnteredPassword] = useState('');
  const [enteredValues, setEnteredValues] = useState({
    email: '',
    password: '',
  });

  function handleSubmit(event) {
    event.preventDefault();

    console.log(enteredValues);
  }

  function handleInputChange(identifier, value) {
    setEnteredValues((prevValues) => ({
      ...prevValues,
      [identifier]: value, // dymanically enter
    }));
  }

  // function handleEmailChange(event) {
  //   setEnteredEmail(event.target.value);
  // }

  // function handlePasswordChange(event) {
  //   setEnteredPassword(event.target.value);
  // }

  return (
    <form onSubmit={handleSubmit}>
      <h2>Login</h2>

      <div className="control-row">
        <div className="control no-margin">
          <label htmlFor="email">Email</label>
          <input
            id="email"
            type="email"
            name="email"
            onChange={(event) => handleInputChange('email', event.target.value)}
            value={enteredValues.email}
          />
        </div>

        <div className="control no-margin">
          <label htmlFor="password">Password</label>
          <input
            id="password"
            type="password"
            name="password"
            onChange={(event) =>
              handleInputChange('password', event.target.value)
            }
            value={enteredValues.password}
          />
        </div>
      </div>

      <p className="form-actions">
        <button className="button button-flat">Reset</button>
        <button className="button">Login</button>
      </p>
    </form>
  );
}
````

### Getting User Input via Refs

````
import { useRef } from 'react';

export default function Login() {
  const email = useRef();
  const password = useRef();

  function handleSubmit(event) {
    event.preventDefault();

    const enteredEmail = email.current.value;
    const enteredPassword = password.current.value;

    console.log(enteredEmail, enteredPassword);
  }

  return (
    <form onSubmit={handleSubmit}>
      <h2>Login</h2>

      <div className="control-row">
        <div className="control no-margin">
          <label htmlFor="email">Email</label>
          <input id="email" type="email" name="email" ref={email} />
        </div>

        <div className="control no-margin">
          <label htmlFor="password">Password</label>
          <input id="password" type="password" name="password" ref={password} />
        </div>
      </div>

      <p className="form-actions">
        <button className="button button-flat">Reset</button>
        <button className="button">Login</button>
      </p>
    </form>
  );
}
````
Require less code than with state

### Getting Values via FormData & Native Browser APIs

Native build in feature
Need name prop in all the things you want to control
````
export default function Signup() {
  function handleSubmit(event) {
    event.preventDefault();

    const fd = new FormData(event.target);
    const acquisitionChannel = fd.getAll('acquisition'); // this for the multiple data entry
    const data = Object.fromEntries(fd.entries()); // all entries less the multiple data
    data.acquisition = acquisitionChannel;
    console.log(data);
  }

  return (
    <form onSubmit={handleSubmit}>
      <h2>Welcome on board!</h2>
      <p>We just need a little bit of data from you to get you started 🚀</p>

      <div className="control">
        <label htmlFor="email">Email</label>
        <input id="email" type="email" name="email" />
      </div>

      <div className="control-row">
        <div className="control">
          <label htmlFor="password">Password</label>
          <input id="password" type="password" name="password" />
        </div>

        <div className="control">
          <label htmlFor="confirm-password">Confirm Password</label>
          <input
            id="confirm-password"
            type="password"
            name="confirm-password"
          />
        </div>
      </div>

      <hr />

      <div className="control-row">
        <div className="control">
          <label htmlFor="first-name">First Name</label>
          <input type="text" id="first-name" name="first-name" />
        </div>

        <div className="control">
          <label htmlFor="last-name">Last Name</label>
          <input type="text" id="last-name" name="last-name" />
        </div>
      </div>

      <div className="control">
        <label htmlFor="phone">What best describes your role?</label>
        <select id="role" name="role">
          <option value="student">Student</option>
          <option value="teacher">Teacher</option>
          <option value="employee">Employee</option>
          <option value="founder">Founder</option>
          <option value="other">Other</option>
        </select>
      </div>

      <fieldset>
        <legend>How did you find us?</legend>
        <div className="control">
          <input
            type="checkbox"
            id="google"
            name="acquisition"
            value="google"
          />
          <label htmlFor="google">Google</label>
        </div>

        <div className="control">
          <input
            type="checkbox"
            id="friend"
            name="acquisition"
            value="friend"
          />
          <label htmlFor="friend">Referred by friend</label>
        </div>

        <div className="control">
          <input type="checkbox" id="other" name="acquisition" value="other" />
          <label htmlFor="other">Other</label>
        </div>
      </fieldset>

      <div className="control">
        <label htmlFor="terms-and-conditions">
          <input type="checkbox" id="terms-and-conditions" name="terms" />I
          agree to the terms and conditions
        </label>
      </div>

      <p className="form-actions">
        <button type="reset" className="button button-flat">
          Reset
        </button>
        <button type="submit" className="button">
          Sign up
        </button>
      </p>
    </form>
  );
}
````

### Resetting Forms

Button type reset
Or reset with the state
With ref you do `ref.current.value = ""`
With FormData `event.target.reset()`

### Validating Input on Every Keystroke via State

Print a message below the input, but it appears at the begging of the typing, not what we want
````
const emailIsInvalid =
    enteredValues.email !== '' && !enteredValues.email.includes('@');

return(
<div className="control-row">
        <div className="control no-margin">
          <label htmlFor="email">Email</label>
          <input
            id="email"
            type="email"
            name="email"
            onChange={(event) => handleInputChange('email', event.target.value)}
            value={enteredValues.email}
          />
          <div className="control-error">
            {emailIsInvalid && <p>Please enter a valid email address.</p>}
          </div>
        </div>
)
````

### Validating Input Upon Lost Focus (Blur)

With blur is like user was using the input and then he change to other input
````
import { useState } from 'react';

export default function Login() {
  // const [enteredEmail, setEnteredEmail] = useState('');
  // const [enteredPassword, setEnteredPassword] = useState('');
  const [enteredValues, setEnteredValues] = useState({
    email: '',
    password: '',
  });

 -- const [didEdit, setDidEdit] = useState({
    email: false,
    password: false,
  });

  --const emailIsInvalid = didEdit.email && !enteredValues.email.includes('@');

  function handleSubmit(event) {
    event.preventDefault();

    console.log(enteredValues);
  }

  function handleInputChange(identifier, value) {
    setEnteredValues((prevValues) => ({
      ...prevValues,
      [identifier]: value,
    }));
    setDidEdit((prevEdit) => ({
      ...prevEdit,
      [identifier]: false, // important when user start writing, delete the warning
    }));
  }

 -- function handleInputBlur(identifier) {
    setDidEdit((prevEdit) => ({
      ...prevEdit,
      [identifier]: true,
    }));
  }

  // function handleEmailChange(event) {
  //   setEnteredEmail(event.target.value);
  // }

  // function handlePasswordChange(event) {
  //   setEnteredPassword(event.target.value);
  // }

  return (
    <form onSubmit={handleSubmit}>
      <h2>Login</h2>

      <div className="control-row">
        <div className="control no-margin">
          <label htmlFor="email">Email</label>
          <input
            id="email"
            type="email"
            name="email"
            --onBlur={() => handleInputBlur('email')}
            onChange={(event) => handleInputChange('email', event.target.value)}
            value={enteredValues.email}
          />
          <div className="control-error">
            {emailIsInvalid && <p>Please enter a valid email address.</p>}
          </div>
        </div>

        <div className="control no-margin">
          <label htmlFor="password">Password</label>
          <input
            id="password"
            type="password"
            name="password"
            onChange={(event) =>
              handleInputChange('password', event.target.value)
            }
            value={enteredValues.password}
          />
        </div>
      </div>

      <p className="form-actions">
        <button className="button button-flat">Reset</button>
        <button className="button">Login</button>
      </p>
    </form>
  );
}
````

### Validating Input Upon Form Submission

````
import { useRef, useState } from 'react';

export default function Login() {
  -- const [emailIsInvalid, setEmailIsInvalid] = useState(false);

  const email = useRef();
  const password = useRef();

 -- function handleSubmit(event) {
    event.preventDefault();

    const enteredEmail = email.current.value;
    const enteredPassword = password.current.value;

    const emailIsValid = enteredEmail.includes('@');

    if (!emailIsValid) {
      setEmailIsInvalid(true);
      return;
    }

    setEmailIsInvalid(false);

    console.log('Sending HTTP request...');
  }

  return (
    <form onSubmit={handleSubmit}>
      <h2>Login</h2>

      <div className="control-row">
        <div className="control no-margin">
          <label htmlFor="email">Email</label>
          <input id="email" type="email" name="email" ref={email} />
          --<div className="control-error">
            {emailIsInvalid && <p>Please enter a valid email address.</p>}
          </div>
        </div>

        <div className="control no-margin">
          <label htmlFor="password">Password</label>
          <input id="password" type="password" name="password" ref={password} />
        </div>
      </div>

      <p className="form-actions">
        <button className="button button-flat">Reset</button>
        <button className="button">Login</button>
      </p>
    </form>
  );
}
````

### Validating Input via Built-in Validation Props

With this life is more easier
Use props defined to validate
````
export default function Signup() {
  function handleSubmit(event) {
    event.preventDefault();

    const fd = new FormData(event.target);
    const acquisitionChannel = fd.getAll('acquisition');
    const data = Object.fromEntries(fd.entries());
    data.acquisition = acquisitionChannel;
    console.log(data);
  }

  return (
    <form onSubmit={handleSubmit}>
      <h2>Welcome on board!</h2>
      <p>We just need a little bit of data from you to get you started 🚀</p>

      <div className="control">
        <label htmlFor="email">Email</label>
        --<input id="email" type="email" name="email" required /> // required and with the type needed
      </div>

      <div className="control-row">
        <div className="control">
          <label htmlFor="password">Password</label>
          <input
            id="password"
            type="password"
            name="password"
            --required
            --minLength={6}
          />
        </div>

        <div className="control">
          <label htmlFor="confirm-password">Confirm Password</label>
          <input
            id="confirm-password"
            type="password"
            name="confirm-password"
            required
          />
        </div>
      </div>

      <hr />

      <div className="control-row">
        <div className="control">
          <label htmlFor="first-name">First Name</label>
          <input type="text" id="first-name" name="first-name" required />
        </div>

        <div className="control">
          <label htmlFor="last-name">Last Name</label>
          <input type="text" id="last-name" name="last-name" required />
        </div>
      </div>

      <div className="control">
        <label htmlFor="phone">What best describes your role?</label>
        <select id="role" name="role" required>
          <option value="student">Student</option>
          <option value="teacher">Teacher</option>
          <option value="employee">Employee</option>
          <option value="founder">Founder</option>
          <option value="other">Other</option>
        </select>
      </div>

      <fieldset>
        <legend>How did you find us?</legend>
        <div className="control">
          <input
            type="checkbox"
            id="google"
            name="acquisition"
            value="google"
          />
          <label htmlFor="google">Google</label>
        </div>

        <div className="control">
          <input
            type="checkbox"
            id="friend"
            name="acquisition"
            value="friend"
          />
          <label htmlFor="friend">Referred by friend</label>
        </div>

        <div className="control">
          <input type="checkbox" id="other" name="acquisition" value="other" />
          <label htmlFor="other">Other</label>
        </div>
      </fieldset>

      <div className="control">
        <label htmlFor="terms-and-conditions">
          <input
            type="checkbox"
            id="terms-and-conditions"
            name="terms"
            required
          />
          I agree to the terms and conditions
        </label>
      </div>

      <p className="form-actions">
        <button type="reset" className="button button-flat">
          Reset
        </button>
        <button type="submit" className="button">
          Sign up
        </button>
      </p>
    </form>
  );
}
````

### Mixing Custom & Built-in Validation Logic

Some validation need to write them, here to confirm the sama password
````
 const [passwordsAreNotEqual, setPasswordsAreNotEqual] = useState(false);

function handleSubmit(event) {
    event.preventDefault();

    const fd = new FormData(event.target);
    const acquisitionChannel = fd.getAll('acquisition');
    const data = Object.fromEntries(fd.entries());
    data.acquisition = acquisitionChannel;

    --if (data.password !== data['confirm-password']) {
      setPasswordsAreNotEqual(true);
      return;
    }

    console.log(data);
  }
````

### Building & Using a Reusable Input Component

Create a component of the Input 

````
export default function Input({ label, id, error, ...props }) {
  return (
    <div className="control no-margin">
      <label htmlFor={id}>{label}</label>
      <input id={id} {...props} />
      <div className="control-error">{error && <p>{error}</p>}</div>
    </div>
  );
}
````

### Outsourcing Validation Logic

Validation in other folder
````
export function isEmail(value) {
  return value.includes('@');
}

export function isNotEmpty(value) {
  return value.trim() !== '';
}

export function hasMinLength(value, minLength) {
  return value.length >= minLength;
}

export function isEqualsToOtherValue(value, otherValue) {
  return value === otherValue;
}
````

### Creating a Custom useInput Hook

````
import { useState } from 'react';

export function useInput(defaultValue, validationFn) {
  const [enteredValue, setEnteredValue] = useState(defaultValue);
  const [didEdit, setDidEdit] = useState(false);

  const valueIsValid = validationFn(enteredValue);

  function handleInputChange(event) {
    setEnteredValue(event.target.value);
    setDidEdit(false);
  }

  function handleInputBlur() {
    setDidEdit(true);
  }

  return {
    value: enteredValue,
    handleInputChange,
    handleInputBlur,
    hasError: didEdit && !valueIsValid
  };
}
````
````
export default function Login() {
  const { // for email
    value: emailValue,
    handleInputChange: handleEmailChange,
    handleInputBlur: handleEmailBlur,
    hasError: emailHasError,
  } = useInput('', (value) => isEmail(value) && isNotEmpty(value));
  const { for password
    value: passwordValue,
    handleInputChange: handlePasswordChange,
    handleInputBlur: handlePasswordBlur,
    hasError: passwordHasError,
  } = useInput('', (value) => hasMinLength(value, 6));

  function handleSubmit(event) {
    event.preventDefault();

    if (emailHasError || passwordHasError) {
      return;
    }

    console.log(emailValue, passwordValue);
  }

  return (...
````

### Using Third-Party Form Libraries

Libraries

https://react-hook-form.com/

## Practice Project: Food Order

Setting a prop convert it automatically to true

UseReducer and UseContext used togheter to spread the state

If you close the modal or checkout with esc key, need to put a onClose prop with the function of closing the modal or checkout

````
onClose={userProgressCtx.progress === "cart" ? handleCloseCart : null}
````

## Diving into Redux

Third Party React Library

### Another Look At State In React Apps

Redux: A state managment system for cross-component or app-wide state

There are three types of state:

 - Local State: single component - useState or useReducer
 - Cross-Component State: affecting multiple components - React Context or Redux
 - App-wide State: affecting entire app - React Context or Redux

### Redux vs React Context

Context potencial disadvantages:

 - Complex setup & managment
 - Deeply nested providers
 - Performance, high frecuency changes

### How Redux Works

Having a Central Data (State) Store
Use it on the components, with a subscription
Component **never** directly manipule the store 
We have Reducer function that changes the data in the store
Component dispatch actions (the operation) and forwarded to the reducer function, and then it changes the state in the central store

### Exploring The Core Redux Concepts

````
//terminal
npm init
npm install redux

//redux-demo.js
const redux = require('redux');

const counterReducer = (state = {counter: 0}, action) => {
	return {
		counter: state.counter + 1,
	};
};

const store = redux.createStore(counterReducer);

const counterSubscriber = () => {
	const latestState = store.getState(); // latest state
};

store.subscribe(counterSubscriber);
````

Reducer will recieve two inputs: old state + dispatch action and return a new state object

After this:
````
// terminal
node redux-demo.js

//redux-demo.js
store.dispatch({type:'increment'}); // the action
````
With that you run the reducer and change the state

### More Redux Basics

Condition of the action
````
const counterReducer = (state = {counter: 0}, action) => {
	if(action.type === 'increment') {
		return {
			counter: state.counter + 1,
		};
	}
	return state;
};
````

### Preparing a new Project

To make redux work with react easier
````
//terminal
npm install redux react-redux
````

### Creating a Redux Store for React

````
// src/store index.js

import { createStore } from 'redux';

const counterReducer = (state = { counter: 0 }, action) => {
  if (action.type === 'increment') {
    return {
      counter: state.counter + 1,
    };
  }

  if (action.type === 'decrement') {
    return {
      counter: state.counter - 1,
    };
  }

  return state;
};

const store = createStore(counterReducer);

export default store;
````
We need to provide our store once

### Providing the Store

````
//index,js
import React from 'react';
import ReactDOM from 'react-dom/client';
--import { Provider } from 'react-redux';

import './index.css';
import App from './App';
--import store from './store/index';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  --<Provider store={store}>
    <App />
  </Provider>
);
````

### Using Redux Data in React Components

````
--import { useSelector } from 'react-redux'; // select a part of the state of the store

import classes from './Counter.module.css';

const Counter = () => {
  --const counter = useSelector(state => state.counter); // extract the part of the state you need

  const toggleCounterHandler = () => {};

  return (
    <main className={classes.counter}>
      <h1>Redux Counter</h1>
      --<div className={classes.value}>{counter}</div> // give the state initial, 0
      <button onClick={toggleCounterHandler}>Toggle Counter</button>
    </main>
  );
};

export default Counter;
````
You will have the latest state with useSelector

### Dispatching Actions From Inside Components

````
--import { useSelector, useDispatch } from 'react-redux';

import classes from './Counter.module.css';

const Counter = () => {
  --const dispatch = useDispatch();
  const counter = useSelector(state => state.counter);

  --const incrementHandler = () => {
    dispatch({ type: 'increment' });
  };

  --const decrementHandler = () => {
    dispatch({ type: 'decrement' });
  };

  const toggleCounterHandler = () => {};

  return (
    <main className={classes.counter}>
      <h1>Redux Counter</h1>
      <div className={classes.value}>{counter}</div>
      <div>
        --<button onClick={incrementHandler}>Increment</button>
        --<button onClick={decrementHandler}>Decrement</button>
      </div>
      <button onClick={toggleCounterHandler}>Toggle Counter</button>
    </main>
  );
};

export default Counter;
````

### Redux with Class-based Components

````
import { Component } from 'react';
import { connect } from 'react-redux';


// class Counter extends Component {
//   incrementHandler() {
//     this.props.increment();
//   }

//   decrementHandler() {
//     this.props.decrement();
//   }

//   toggleCounterHandler() {}

//   render() {
//     return (
//       <main className={classes.counter}>
//         <h1>Redux Counter</h1>
//         <div className={classes.value}>{this.props.counter}</div>
//         <div>
//           <button onClick={this.incrementHandler.bind(this)}>Increment</button>
//           <button onClick={this.decrementHandler.bind(this)}>Decrement</button>
//         </div>
//         <button onClick={this.toggleCounterHandler}>Toggle Counter</button>
//       </main>
//     );
//   }
// }

// const mapStateToProps = state => {
//   return {
//     counter: state.counter
//   };
// }

// const mapDispatchToProps = dispatch => {
//   return {
//     increment: () => dispatch({ type: 'increment' }),
//     decrement: () => dispatch({ type: 'decrement' }),
//   }
// };

// export default connect(mapStateToProps, mapDispatchToProps)(Counter);
````

### Attaching Payloads to Actions

Adding values to the actions
````
//Counter,js
import { useSelector, useDispatch } from 'react-redux';

import classes from './Counter.module.css';

const Counter = () => {
  const dispatch = useDispatch();
  const counter = useSelector((state) => state.counter);

  const incrementHandler = () => {
    dispatch({ type: 'increment' });
  };

 -- const increaseHandler = () => {
    dispatch({ type: 'increase', amount: 10 });
  };

  const decrementHandler = () => {
    dispatch({ type: 'decrement' });
  };

  const toggleCounterHandler = () => {};

  return (
    <main className={classes.counter}>
      <h1>Redux Counter</h1>
      <div className={classes.value}>{counter}</div>
      <div>
        <button onClick={incrementHandler}>Increment</button>
        --<button onClick={increaseHandler}>Increase by 10</button>
        <button onClick={decrementHandler}>Decrement</button>
      </div>
      <button onClick={toggleCounterHandler}>Toggle Counter</button>
    </main>
  );
};

export default Counter;

// store
import { createStore } from 'redux';

const counterReducer = (state = { counter: 0 }, action) => {
  if (action.type === 'increment') {
    return {
      counter: state.counter + 1,
    };
  }

  --if (action.type === 'increase') {
    return {
      counter: state.counter + action.amount, // it is dinamic
    };
  }

  if (action.type === 'decrement') {
    return {
      counter: state.counter - 1,
    };
  }

  return state;
};

const store = createStore(counterReducer);

export default store;
````

### Working with Multiple State Properties

````
//store
import { createStore } from 'redux';

const initialState = { counter: 0, showCounter: true };

const counterReducer = (state = initialState, action) => {
  if (action.type === 'increment') {
    return {
      counter: state.counter + 1,
      showCounter: state.showCounter
    };
  }

  if (action.type === 'increase') {
    return {
      counter: state.counter + action.amount,
      showCounter: state.showCounter
    };
  }

  if (action.type === 'decrement') {
    return {
      counter: state.counter - 1,
      showCounter: state.showCounter
    };
  }

 --if (action.type === 'toggle') {
    return {
      showCounter: !state.showCounter,
      counter: state.counter
    };
  }

  return state;
};

const store = createStore(counterReducer);

export default store;
````
````
//counter,js
import { useSelector, useDispatch } from 'react-redux';

import classes from './Counter.module.css';

const Counter = () => {
  const dispatch = useDispatch();
  const counter = useSelector((state) => state.counter);
  --const show = useSelector((state) => state.showCounter);

  const incrementHandler = () => {
    dispatch({ type: 'increment' });
  };

  const increaseHandler = () => {
    dispatch({ type: 'increase', amount: 10 });
  };

  const decrementHandler = () => {
    dispatch({ type: 'decrement' });
  };

  --const toggleCounterHandler = () => {
    dispatch({ type: 'toggle' });
  };

  return (
    <main className={classes.counter}>
      <h1>Redux Counter</h1>
      --{show && <div className={classes.value}>{counter}</div>}
      <div>
        <button onClick={incrementHandler}>Increment</button>
        <button onClick={increaseHandler}>Increase by 10</button>
        <button onClick={decrementHandler}>Decrement</button>
      </div>
      --<button onClick={toggleCounterHandler}>Toggle Counter</button>
    </main>
  );
};

export default Counter;
````

### How To Work With Redux State Correctly

The state is overwritten
Need to set all the states when we update a piece of state

````
if (action.type === 'increment') {
    return {
      counter: state.counter + 1, // not state.counter++
      showCounter: state.showCounter,
    };
````

### Redux Challenges & Introducing Redux Toolkit

Redux toolKit: package to be the standard way of writing Redux

### Adding State Slices

````
//terminal
npm install @reduxjs/toolkit
````
````
--import { createSlice, configureStore } from '@reduxjs/toolkit';

const initialState = { counter: 0, showCounter: true };

--const counterSlice = createSlice({
  name: 'counter',
  initialState,
  reducers: {
    increment(state) {
      state.counter++; // here it is allowed with this package
    },
    decrement(state) {
      state.counter--;
    },
    increase(state, action) {
      state.counter = state.counter + action.payload;
    },
    toggleCounter(state) {
      state.showCounter = !state.showCounter;
    }
  }
});

const store = configureStore({
  reducer: counterSlice.reducer
});

export const counterActions = counterSlice.actions;

export default store;
````

### Migrating Everything To Redux Toolkit

````
//counter.js
import { useSelector, useDispatch } from 'react-redux';

--import { counterActions } from '../store/index';
import classes from './Counter.module.css';

const Counter = () => {
  const dispatch = useDispatch();
  const counter = useSelector((state) => state.counter);
  const show = useSelector((state) => state.showCounter);

  const incrementHandler = () => {
    dispatch(counterActions.increment());
  };

  const increaseHandler = () => {
    dispatch(counterActions.increase(10)); // { type: SOME_UNIQUE_IDENTIFIER, payload: 10 } Value inside is always the payload
  };

  const decrementHandler = () => {
    dispatch(counterActions.decrement());
  };

  const toggleCounterHandler = () => {
    dispatch(counterActions.toggleCounter());
  };

  return (
    <main className={classes.counter}>
      <h1>Redux Counter</h1>
      {show && <div className={classes.value}>{counter}</div>}
      <div>
        <button onClick={incrementHandler}>Increment</button>
        <button onClick={increaseHandler}>Increase by 10</button>
        <button onClick={decrementHandler}>Decrement</button>
      </div>
      <button onClick={toggleCounterHandler}>Toggle Counter</button>
    </main>
  );
};

export default Counter;
````

### Working with Multiple Slices

````
import { createSlice, configureStore } from '@reduxjs/toolkit';

const initialCounterState = { counter: 0, showCounter: true };

const counterSlice = createSlice({
  name: 'counter',
  initialState: initialCounterState,
  reducers: {
    increment(state) {
      state.counter++;
    },
    decrement(state) {
      state.counter--;
    },
    increase(state, action) {
      state.counter = state.counter + action.payload;
    },
    toggleCounter(state) {
      state.showCounter = !state.showCounter;
    },
  },
});

--const initialAuthState = {
  isAuthenticated: false,
};

--const authSlice = createSlice({
  name: 'authentication',
  initialState: initialAuthState,
  reducers: {
    login(state) {
      state.isAuthenticated = true;
    },
    logout(state) {
      state.isAuthenticated = false;
    },
  },
});

const store = configureStore({
  reducer: { counter: counterSlice.reducer, auth: authSlice.reducer },
});

export const counterActions = counterSlice.actions;
export const authActions = authSlice.actions;

export default store;
````

````
// counter
const counter = useSelector((state) => state.counter.counter); // change when you have more slices
  const show = useSelector((state) => state.counter.showCounter);
````

### Reading & Dispatching From A New Slice

````
//app.js
import { Fragment } from 'react';
import { useSelector } from 'react-redux';

import Counter from './components/Counter';
import Header from './components/Header';
import Auth from './components/Auth';
import UserProfile from './components/UserProfile';


function App() {
  const isAuth = useSelector(state => state.auth.isAuthenticated);

  return (
    <Fragment>
      <Header />
      {!isAuth && <Auth />}
      {isAuth && <UserProfile />}
      <Counter />
    </Fragment>
  );
}

export default App;

//header.js
import { useSelector, useDispatch } from 'react-redux';

import classes from './Header.module.css';
import { authActions } from '../store/index';

const Header = () => {
  const dispatch = useDispatch();
  const isAuth = useSelector((state) => state.auth.isAuthenticated);

  const logoutHandler = () => {
    dispatch(authActions.logout());
  };

  return (
    <header className={classes.header}>
      <h1>Redux Auth</h1>
      {isAuth && (
        <nav>
          <ul>
            <li>
              <a href='/'>My Products</a>
            </li>
            <li>
              <a href='/'>My Sales</a>
            </li>
            <li>
              <button onClick={logoutHandler}>Logout</button>
            </li>
          </ul>
        </nav>
      )}
    </header>
  );
};

export default Header;
````

### Splitting Our Code

Store foulder, split the slices
````
//auth.js
import { createSlice } from '@reduxjs/toolkit';

const initialAuthState = {
  isAuthenticated: false,
};

const authSlice = createSlice({
  name: 'authentication',
  initialState: initialAuthState,
  reducers: {
    login(state) {
      state.isAuthenticated = true;
    },
    logout(state) {
      state.isAuthenticated = false;
    },
  },
});

export const authActions = authSlice.actions;

export default authSlice.reducer;
````
````
//counter.js
import { createSlice } from '@reduxjs/toolkit';

const initialCounterState = { counter: 0, showCounter: true };

const counterSlice = createSlice({
  name: 'counter',
  initialState: initialCounterState,
  reducers: {
    increment(state) {
      state.counter++;
    },
    decrement(state) {
      state.counter--;
    },
    increase(state, action) {
      state.counter = state.counter + action.payload;
    },
    toggleCounter(state) {
      state.showCounter = !state.showCounter;
    },
  },
});

export const counterActions = counterSlice.actions;

export default counterSlice.reducer;
````
````
//index.js merge all the slices
import { configureStore } from '@reduxjs/toolkit';

import counterReducer from './counter';
import authReducer from './auth';


const store = configureStore({
  reducer: { counter: counterReducer, auth: authReducer },
});

export default store;
````

## Advanced Redux

### Redux & Side Effects (and Asynchronous Code)

Reducer must be pure, syde effect free, and synchronous functions

Where to put side effects and async code:

 - Inside Component
 - Inside the action creators

### Backend

He use Firebase as a backend for this lecture, you can use it with a google account

### Frontend Code vs Backend Code

Depending on the backend, you need to transform and send data or just send it

### Where To Put Our Logic

Synchronous, side effect free code - Put code in Reducers
Async Code or code with side-effects - Put code in action creators or components

### Using useEffect with Redux

We can let the front end change the state and then send the information

````
//App.js
import { useEffect } from 'react';
import { useSelector } from 'react-redux';

import Cart from './components/Cart/Cart';
import Layout from './components/Layout/Layout';
import Products from './components/Shop/Products';

function App() {
  --const showCart = useSelector((state) => state.ui.cartIsVisible);
  --const cart = useSelector((state) => state.cart);

  --useEffect(() => {
    fetch('https://react-http-6b4a6.firebaseio.com/cart.json', {
      method: 'PUT',
      body: JSON.stringify(cart),
    });
  }, [cart]);

  return (
    <Layout>
      {showCart && <Cart />}
      <Products />
    </Layout>
  );
}

export default App;
````

### Handling Http States & Feedback with Redux
````
// ui-slice.js/store
import { createSlice } from '@reduxjs/toolkit';

const uiSlice = createSlice({
  name: 'ui',
  --initialState: { cartIsVisible: false, notification: null },
  reducers: {
    toggle(state) {
      state.cartIsVisible = !state.cartIsVisible;
    },
    --showNotification(state, action) {
      state.notification = {
        status: action.payload.status,
        title: action.payload.title,
        message: action.payload.message,
      };
    },
  },
});

export const uiActions = uiSlice.actions;

export default uiSlice;
````
````
//App.js
import { Fragment, useEffect } from 'react';
import { useSelector, useDispatch } from 'react-redux';

import Cart from './components/Cart/Cart';
import Layout from './components/Layout/Layout';
import Products from './components/Shop/Products';
import { uiActions } from './store/ui-slice';
import Notification from './components/UI/Notification';

let isInitial = true; // not to send it when refresh

function App() {
  const dispatch = useDispatch();
  const showCart = useSelector((state) => state.ui.cartIsVisible);
  const cart = useSelector((state) => state.cart);
  const notification = useSelector((state) => state.ui.notification);

  useEffect(() => {
    const sendCartData = async () => {
      dispatch(
        uiActions.showNotification({
          status: 'pending',
          title: 'Sending...',
          message: 'Sending cart data!',
        })
      );
      const response = await fetch(
        'https://react-http-6b4a6.firebaseio.com/cart.json',
        {
          method: 'PUT',
          body: JSON.stringify(cart),
        }
      );

      if (!response.ok) {
        throw new Error('Sending cart data failed.');
      }

      dispatch(
        uiActions.showNotification({
          status: 'success',
          title: 'Success!',
          message: 'Sent cart data successfully!',
        })
      );
    };

    if (isInitial) { // when start application dont overwrite with nothing in the cart
      isInitial = false;
      return;
    }

    sendCartData().catch((error) => {
      dispatch(
        uiActions.showNotification({
          status: 'error',
          title: 'Error!',
          message: 'Sending cart data failed!',
        })
      );
    });
  }, [cart, dispatch]);

  return (
    <Fragment>
     -- {notification && (
        <Notification // other component created to make a notification
          status={notification.status}
          title={notification.title}
          message={notification.message}
        />
      )}
      <Layout>
        {showCart && <Cart />}
        <Products />
      </Layout>
    </Fragment>
  );
}

export default App;
````

### Using an Action Creator Thunk

Thunk: function that delays an action until later

````
//cart-slice.js in the store foulder
import { createSlice } from '@reduxjs/toolkit';

import { uiActions } from './ui-slice';

const cartSlice = createSlice({
  name: 'cart',
  initialState: {
    items: [],
    totalQuantity: 0,
  },
  reducers: {
    replaceCart(state, action) {
      state.totalQuantity = action.payload.totalQuantity;
      state.items = action.payload.items;
    },
    addItemToCart(state, action) {
      const newItem = action.payload;
      const existingItem = state.items.find((item) => item.id === newItem.id);
      state.totalQuantity++;
      if (!existingItem) {
        state.items.push({
          id: newItem.id,
          price: newItem.price,
          quantity: 1,
          totalPrice: newItem.price,
          name: newItem.title,
        });
      } else {
        existingItem.quantity++;
        existingItem.totalPrice = existingItem.totalPrice + newItem.price;
      }
    },
    removeItemFromCart(state, action) {
      const id = action.payload;
      const existingItem = state.items.find((item) => item.id === id);
      state.totalQuantity--;
      if (existingItem.quantity === 1) {
        state.items = state.items.filter((item) => item.id !== id);
      } else {
        existingItem.quantity--;
      }
    },
  },
});

--export const sendCartData = (cart) => {
  return async (dispatch) => {
    dispatch(
      uiActions.showNotification({
        status: 'pending',
        title: 'Sending...',
        message: 'Sending cart data!',
      })
    );

    const sendRequest = async () => {
      const response = await fetch(
        'https://react-http-6b4a6.firebaseio.com/cart.json',
        {
          method: 'PUT',
          body: JSON.stringify(cart),
        }
      );

      if (!response.ok) {
        throw new Error('Sending cart data failed.');
      }
    };

    try {
      await sendRequest();

      dispatch(
        uiActions.showNotification({
          status: 'success',
          title: 'Success!',
          message: 'Sent cart data successfully!',
        })
      );
    } catch (error) {
      dispatch(
        uiActions.showNotification({
          status: 'error',
          title: 'Error!',
          message: 'Sending cart data failed!',
        })
      );
    }
  };
};

export const cartActions = cartSlice.actions;

export default cartSlice;
````
````
//App.js
import { Fragment, useEffect } from 'react';
import { useSelector, useDispatch } from 'react-redux';

import Cart from './components/Cart/Cart';
import Layout from './components/Layout/Layout';
import Products from './components/Shop/Products';
import Notification from './components/UI/Notification';
import { sendCartData } from './store/cart-slice';

let isInitial = true;

function App() {
  const dispatch = useDispatch();
  const showCart = useSelector((state) => state.ui.cartIsVisible);
  const cart = useSelector((state) => state.cart);
  const notification = useSelector((state) => state.ui.notification);

  useEffect(() => {
    if (isInitial) {
      isInitial = false;
      return;
    }

    dispatch(sendCartData(cart));
  }, [cart, dispatch]);

  return (
    <Fragment>
      {notification && (
        <Notification
          status={notification.status}
          title={notification.title}
          message={notification.message}
        />
      )}
      <Layout>
        {showCart && <Cart />}
        <Products />
      </Layout>
    </Fragment>
  );
}

export default App;
````

### Getting Started with Fetching Data

He create a file for the actions
He create another thrunk for fetching the data

### Finalizing the Fetching Logic

Problem with fetching the initial data we get from server:
Put on initialState a prop `changed:false` and change it to true when add and remove

When we try to fetch the data, if we dont have items, need to tweek the code to accept empty object
````
 try {
      const cartData = await fetchData();
      dispatch(
        cartActions.replaceCart({
          items: cartData.items || [], 
          totalQuantity: cartData.totalQuantity,
        })
      );
````

### Exploring the Redux DevTools

Debbugin easier
Search repository of Redux Devtools - and install them
Devtools/Redux

## Single Page Application Routing

### What is Routing?

Different URL path load different content on the screen

Only one initial HTML, and the page changes handled by React Code
Visible content is changed without fetching a new HTML file

### Project Setup & Installing React Router

````
//terminal
npm install react-router-dom
````

### Defining Routes

````
//App.js
import { createBrowserRouter, RouterProvider } from 'react-router-dom';

import HomePage from './pages/Home';

const router = createBrowserRouter([
  { path: '/', element: <HomePage /> }, // route obhect
]);

function App() {
  return <RouterProvider router={router} />;
}

export default App;
````

````
//pages/Home.js
function HomePage() {
  return <h1>My Home Page</h1>;
}

export default HomePage;
````

### Adding a Second Route

````
//pages/Product.js
function ProductsPage() {
  return <h1>The Products Page</h1>;
}

export default ProductsPage;
````
````
//App.js
import {createBrowserRouter,RouterProvider,} from 'react-router-dom';

import HomePage from './pages/Home';
import ProductsPage from './pages/Products';

const router = createBrowserRouter([
  { path: '/', element: <HomePage /> },
  { path: '/products', element: <ProductsPage /> },
]);

function App() {
  return <RouterProvider router={router} />;
}

export default App;
````

### Exploring an Alternative Way of Defining Routes

Not so used, more in the past
````
import {
  createBrowserRouter,
  // createRoutesFromElements,
  RouterProvider,
  // Route,
} from 'react-router-dom';

import HomePage from './pages/Home';
import ProductsPage from './pages/Products';

// const routeDefinitions = createRoutesFromElements(
//   <Route>
//     <Route path="/" element={<HomePage />} />
//     <Route path="/products" element={<ProductsPage />} />
//   </Route>
// );

const router = createBrowserRouter([
  { path: '/', element: <HomePage /> },
  { path: '/products', element: <ProductsPage /> },
]);

// const router = createBrowserRouter(routeDefinitions);

function App() {
  return <RouterProvider router={router} />;
}

export default App;
````

### Navigating between Pages with Links

````
import { Link } from 'react-router-dom';

function HomePage() {
  return (
    <>
      <h1>My Home Page</h1>
      <p>
        Go to <Link to="/products">the list of products</Link>.
      </p>
    </>
  );
}

export default HomePage;
````

### Layouts & Nested Routes

Outlet is the render of the children
````
//component/navigation.js
import { Link } from 'react-router-dom';

import classes from './MainNavigation.module.css';

function MainNavigation() {
  return (
    <header className={classes.header}>
      <nav>
        <ul className={classes.list}>
          <li>
            <Link to="/">Home</Link>
          </li>
          <li>
            <Link to="/products">Products</Link>
          </li>
        </ul>
      </nav>
    </header>
  );
}

export default MainNavigation;
````
````
//App.js
import {
  createBrowserRouter,RouterProvider,} from 'react-router-dom';

import HomePage from './pages/Home';
import ProductsPage from './pages/Products';
import RootLayout from './pages/Root';

const router = createBrowserRouter([
  {
    path: '/',
    element: <RootLayout />,
    children: [
      { path: '/', element: <HomePage /> },
      { path: '/products', element: <ProductsPage /> },
    ],
  }
]);

function App() {
  return <RouterProvider router={router} />;
}

export default App;
````
````
//pages/root.js
import { Outlet } from 'react-router-dom';

import MainNavigation from '../components/MainNavigation';
import classes from './Root.module.css';

function RootLayout() {
  return (
    <>
      <MainNavigation />
      <main className={classes.content}>
        <Outlet />
      </main>
    </>
  );
}

export default RootLayout;
````

### Showing Error Pages with errorElement

Prepare a default error page
````
//pages/error.js
import MainNavigation from '../components/MainNavigation';

function ErrorPage() {
  return (
    <>
      <MainNavigation />
      <main>
        <h1>An error occurred!</h1>
        <p>Could not find this page!</p>
      </main>
    </>
  );
}

export default ErrorPage;
````
````
//App.js
import ErrorPage from './pages/Error';

const router = createBrowserRouter([
  {
    path: '/',
    element: <RootLayout />,
    errorElement: <ErrorPage />,
    children: [
      { path: '/', element: <HomePage /> },
      { path: '/products', element: <ProductsPage /> },
    ],
  }
]);
````

### Working with Navigation Links (NavLink)

The link css is an `a`
````
// navigation css
.list a:hover,
.list a.active {
  color: var(--color-primary-800);
  text-decoration: underline;
}
````
````
//navigation.js
import { NavLink } from 'react-router-dom'; // changed

import classes from './MainNavigation.module.css';

function MainNavigation() {
  return (
    <header className={classes.header}>
      <nav>
        <ul className={classes.list}>
          <li>
            <NavLink
              to="/"
              className={({ isActive }) =>
                isActive ? classes.active : undefined
              }
              // style={({ isActive }) => ({
              //   textAlign: isActive ? 'center' : 'left',
              // })}
              end // prop, '/' is the end of the link
            >
              Home
            </NavLink>
          </li>
          <li>
            <NavLink
              to="/products"
              className={({ isActive }) =>
                isActive ? classes.active : undefined
              }
            >
              Products
            </NavLink>
          </li>
        </ul>
      </nav>
    </header>
  );
}

export default MainNavigation;
````

### Navigating Programmatically

````
//pages/home.js
import { Link, useNavigate } from 'react-router-dom';

function HomePage() {
  const navigate = useNavigate();

  function navigateHandler() {
    navigate('/products');
  }

  return (
    <>
      <h1>My Home Page</h1>
      <p>
        Go to <Link to="/products">the list of products</Link>.
      </p>
      <p>
        <button onClick={navigateHandler}>Navigate</button>
      </p>
    </>
  );
}

export default HomePage;
````

### Defining & Using Dynamic Routes

````
//App.js
import ProductDetailPage from './pages/ProductDetail';

const router = createBrowserRouter([
  {
    path: '/',
    element: <RootLayout />,
    errorElement: <ErrorPage />,
    children: [
      { path: '/', element: <HomePage /> },
      { path: '/products', element: <ProductsPage /> },
      { path: '/products/:productId', element: <ProductDetailPage /> } // is dinamyc with the :
    ],
  }
]);
````
Extracting the ID and show it in a paragraph
````
//pages/productdetail.js
import { useParams } from 'react-router-dom';

function ProductDetailPage() {
  const params = useParams();

  return (
    <>
      <h1>Product Details!</h1>
      <p>{params.productId}</p>
    </>
  );
}

export default ProductDetailPage;
````
````
//pages/product.js
import { Link } from 'react-router-dom';

const PRODUCTS = [
  { id: 'p1', title: 'Product 1' },
  { id: 'p2', title: 'Product 2' },
  { id: 'p3', title: 'Product 3' },
];

function ProductsPage() {
  return (
    <>
      <h1>The Products Page</h1>
      <ul>
        {PRODUCTS.map((prod) => (
          <li key={prod.id}>
            <Link to={`/products/${prod.id}`}>{prod.title}</Link>
          </li>
        ))}
      </ul>
    </>
  );
}

export default ProductsPage;
````

### Understanding Relative & Absolute Paths

Absolute path is in the previous exercises
Relative Path:
````
const router = createBrowserRouter([
  {
    path: '/',
    element: <RootLayout />,
    errorElement: <ErrorPage />,
    children: [
      { path: '', element: <HomePage /> },
      { path: 'products', element: <ProductsPage /> },
      { path: 'products/:productId', element: <ProductDetailPage /> }
    ],
  }
]);

````

The `..` make you up to the root
If you want to go up one path, need to put `relative='path'`

### Working with Index Routes

````
const router = createBrowserRouter([
  {
    path: '/',
    element: <RootLayout />,
    errorElement: <ErrorPage />,
    children: [
      { index: true, element: <HomePage /> }, // become index route, the default
      { path: 'products', element: <ProductsPage /> },
      { path: 'products/:productId', element: <ProductDetailPage /> }
    ],
  }
]);
````

### Data Fetching with a loader()

We want the fetching data before the component render

````
//App.js
import { RouterProvider, createBrowserRouter } from 'react-router-dom';

import EditEventPage from './pages/EditEvent';
import EventDetailPage from './pages/EventDetail';
import EventsPage from './pages/Events';
import EventsRootLayout from './pages/EventsRoot';
import HomePage from './pages/Home';
import NewEventPage from './pages/NewEvent';
import RootLayout from './pages/Root';

const router = createBrowserRouter([
  {
    path: '/',
    element: <RootLayout />,
    children: [
      { index: true, element: <HomePage /> },
     -- {
        path: 'events',
        element: <EventsRootLayout />,
        children: [
          {
            index: true,
            element: <EventsPage />,
            loader: async () => {
              const response = await fetch('http://localhost:8080/events');

              if (!response.ok) {
                // ...
              } else {
                const resData = await response.json();
                return resData.events;
              }
            },
          },
          { path: ':eventId', element: <EventDetailPage /> },
          { path: 'new', element: <NewEventPage /> },
          { path: ':eventId/edit', element: <EditEventPage /> },
        ],
      },
    ],
  },
]);

function App() {
  return <RouterProvider router={router} />;
}

export default App;
````

### Using Data From A Loader In The Route Component

````
//event.js
--import { useLoaderData } from 'react-router-dom';

import EventsList from '../components/EventsList';

function EventsPage() {
  const events = useLoaderData();

  return <EventsList events={events} />;
}

export default EventsPage;
````

### More loader() Data Usage

Could use it direcly in the component of before `<EventList />`
Cannot use it in a higher route level, but you can in lower levels

### Where Should loader() Code Be Stored?

Put the loader as a function in the page you need it and export it to the app.js file

### When Are loader() Functions Executed?

Execute right when we start navigating to that page

### Reflecting The Current Navigation State in the UI

Give user a feedback that something is trying to render?

````
--import { Outlet, useNavigation } from 'react-router-dom';

import MainNavigation from '../components/MainNavigation';

--function RootLayout() {
   const navigation = useNavigation();

  return (
    <>
      <MainNavigation />
      <main>
        --{navigation.state === 'loading' && <p>Loading...</p>}
        <Outlet />
      </main>
    </>
  );
}

export default RootLayout;
````
We will see a better way in the next lectures

### Returning Responses in loader()s

You can return any kind of data on the loader

````
import { useLoaderData } from 'react-router-dom';

import EventsList from '../components/EventsList';

function EventsPage() {
  const data = useLoaderData();
  --const events = data.events; // now you can extract the events here

  return <EventsList events={events} />;
}

export default EventsPage;

export async function loader() {
  const response = await fetch('http://localhost:8080/events');

  if (!response.ok) {
    // ...
  } else {
    --return response; // any kind of data can return
  }
}
````
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDExNjMwNTAxLDc4MjA3OTQ3NywtMTMwMD
MyODU3MCwtMTIzNjE0MTg0OCw5NzI3MzI1MywtMTI5MzU4MTQz
NSwtMTcyOTcyOTI1MSwxMDIwMTM2MzMsNjEzNTExNTI5LC0xND
I0NDE0NjY3LC0xMDEzNDkxODE0LC0xMDMzNzIyMjQ0LDcyMDQ3
Mjg1OCwyMTAwNDA5MTA3LC0xODc1ODA0Nzk2LC0xMDkzNTc1MT
UyLDQwOTY1MjE0OCwyODcxNTg3ODIsODE0Njc1NDQyLDE5MzQ2
NTE2NjddfQ==
-->