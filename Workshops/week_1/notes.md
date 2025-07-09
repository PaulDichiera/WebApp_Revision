In the first class we are essentially looking at Installation and set up, The full stack we are working with is:

Node.js
npm(node package manager)

to check these are installed or the versions we run these commands in terminal

node -v (the name of the application and -v call the version)
npm - v

We then create the appliaction which will set up our package manager using command 

npx create-next-app@latest my-app

within this we are able to set up parameter options

Typescript 
ESLint 
Tailwind CSS
src/ directory 
App Router

For the rest of the class we go over basic typescript skills, Type annotations, Interfaces and functions with types

Why so we need node and npm for a React development enviroment?

Node.js primarily serves as the JavaScript runtime enviroment that facilitates the entire dev workflow, Node.js provides
the tools and infrastructure for building, managing and deploying React applications.

NPM is used to manage package dependencies like React itself, libraries, frameworks and tools. 
npm will create your package.json automatically which lists all of the project dependecies and their versions 
to ensure a consistant set uo across different enviroments,.

lecture learnings and conversations:

Props
the use of destructing, when destructing in TS we are passing a prop into a function in doing so we define the prop name and define what type to expect
example:

const Greeting({name}: {name: string}){
 return <h1>hi my name is {name}</h1>;
}

this safegurads the inserted type for 'Greeting' function

we can also do it without deconstructing 
example:

const Greeting(props: {name: string}) {
    return <h1> hi my name is {props.name}</h2>;
}

** Use of brackets and returns in TS **

{} function bodies - code block 

This denotes a code block that will run it does not have a return it can just run the function and the work in the code block will apply in its enviroment
example: 

function myfunc() {
    console.log("hello)
}

{} arrow function - depends on return style

Implicit - an expression will be returned with no use of {}, the return is implied 
example:

const double = (x: number) => x * 2;

Explicit - an expression where we define explicitly what will be returned here we use the {} to define a codeblock and define a return. 
example:

const double = (x: number) => {
    return x * 2;
}

Returning an object -  an expression that returns an object we do this by wrapping our codeblock it in parenthesis
example:

const makeUser = () => ({ name: "Paul"});

**note if we do not have the parenthesis we have a codeblock 
example:

const makeUser = () => {name; "Paul"}; // this will not work, it is a codeblock and will not return anything as is and will not return an object.

Object literals - here we are defining an object outside of a function so it can be used in other processes
example:

const user = { name: "Paul", age: 39};

** Summary **

{name} in parameters,   Destructive object 
{name: string} in type, TypeScript object shape
{} in function body,    Code block 
() => ({name: "Paul"}), Returning object ( wrapped in () )
{name: "Paul"},         Object literal

Event Handlers

What is an event handler?

If we have a function for example Counter that counts the number of clicks, we want to within that have a useState that sets our count and alters it, within the function we have a function for example callec handleClick() that calls the setCount on our useState, the 'handleClick' is our event handler. the event is the click and and we handle it with the handle click function.

so handleing yhe event is the event of a click 
example:

function Counter() {

    const [ count, setCount] useState(0);

    const handleClick() {
        setCount[count + 1];
    }

    return <button onClick={handleClick}>Clicked {count} times </button>;
}

handleClick, is the event handler
onCLick={handleClick} is Reacts way of attaching it to the button

What is the DOM?

DOM = Document Object Model

The DOM is everything we see on the webpage

this:

<body>
    <h1>Hello</h1>
    <button>Click Me</button>
</body>

is the same as 

Document
|-- <body>
    |--<h1>Hello</h1>
    |--<button>Click Me</button>

Each element is a node Javascript can interact with, This is direct DOM manupulation

React has a virtual DOM, when changes are made react updates the virtual DOM, it compares it to the previous version and only updates the changed parts of the DOM

** Data Storage **

Aside using MySQL and a complete backend, LocalStorage can be used for certain features or in preliminary building for testing purposes only.

** Hooks **

useState, can set and retrieve a value

example:
const [state, setState] = useState(initalValue);

we define the use state it takes two variables a state and a setter we also have an inital value, setState is also called the state updater function

    - alternitively you can also invoke the state updater with a callback setState(prev => next) this will return the new state based on the previous
example:

setCount( prevCount => prevCount + 1);

or

setCount(prev => prev + 1);

Why use the callback?

Multiple updates in a row,          Prevents using a stale state
Updates depend on current value,    Guarantees Correctness
Inside setTimeout, event handlers,  State may not be fresh at that point, use callback

Practical example 

consr [count, setCount] useState(0);

function incrementFiveTimes {
    for(let 1 = 0; 1 < 5; i++>){
        setCount(prev => prev + 1);
    }
}

**Note**
It is the '=>' triggering the callback the parameter name can be anything when JS sees => used in this way 

setCount(value => value + 1), it interprits it as passing a function into setCount that returns the most recent state value.
This callback style is used within state updates.

This patterin is also useful in the following 

useState,           setState(prev => ...),                  Access latest state when updating 
useReducer,         dispatch(action) (with reducer logic),  For complex state logic
setTimeout,         setTimeout(() => {...}, 1000),          Not React specific but uses callback 
useEffect cleanup,  return () => {...},                     Runs on component unmount or re-run

Does not apply for 
Variables that arent stateful 
Props 
Direct expressions

This is due to there being nothing for React to 'track and update'

** Not used for vanilla JavaScript **

next session

- Forms in React 
- Conditional rendering of components
- Using NextJS Router




