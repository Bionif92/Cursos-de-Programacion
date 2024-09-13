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

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwOTY0NjU4ODQsMjA4NTA5OTI4LDM1Nz
k1MzkwNCwxOTM5Mjc5MjY1LDEzNzU3NzkwNzgsLTcwOTg1MDg2
LDE4MTY2NTQzNDYsMTgzODg1NDc2Niw4OTA4MDIwNDIsLTQ2Nj
AxNzc3NiwxOTExNTEyNjQ3LC03MzUxODUyMTYsLTg1NDgyMzAw
Nyw1MjQ0ODE2MzEsLTExMjU4NTg0ODAsOTc4NzU2NjY1LC02OD
AwMzU0NjIsODY0MDgwMjU1LDEyMzI1NjE5ODksNTg4MjIwMzkw
XX0=
-->