# What is Props in React?

**In ReactJS**, the **props** are a type of object where the value of attributes of a tag is stored.
The word “props” implies “properties”, and its working functionality is quite similar to
HTML attributes.

**Props are used to pass data and event handlers to the children components**

Basically, these props components are read-only components. In ReactJS, the data can be
passed from one component to another component using these props, similar to how the
arguments are passed in a function. Inside the component, we can add the attributes called
props; however, we cannot change or modify props inside the component as they are immutable.

eg: <CreateList title="India" />

  + In CreateList comp onent title is passed as a **PROPS** and inside CreateList component we
  will use pops.title to render value of title props "India" into **DOM**.



# What is State in React?

The **state** is a built-in React object that is used to contain data or information about the
component. A component’s state can change over time; whenever it changes, the component re-renders. The change in state can happen as a response to user action or system-generated events and these changes determine the behavior of the component and how it will render.

- **state** can be modified based on user action or network changes
- Every time the **state** of an object changes, React re-renders the component to the browser
- The **state** object is initialized in the constructor
- The **state** object can store multiple properties
- **this.setState()** is used to change the value of the state object
- **setState()** function performs a shallow merge between the new and the previous state


# State vs. Props | what is difference between State and Props in React?

|                  | Option | Description |
| ---------------  | ------ | ----------- |
| Use Case         | State is used to store the data of the components that have to be rendered to the view | Props are used to pass data and event handlers to the children components |
| Mutability       | State holds the data and can change over time | Props are immutable—once set, props cannot be changed |
| Component        | State can only be used in class components | Props can be used in both functional and class components |
| Updation         | Event handlers generally update state | The parent component sets props for the children components |


# What is React Hook ?

**React Hooks** are simple JavaScript functions that we can use to isolate the reusable part from a functional component. Hooks can be stateful and can manage side-effects.

With React Hooks, we can isolate stateful logic and side-effects from a functional component. Hooks are JavaScript functions that manage the state's behaviour and side effects by isolating them from a component.

So, we can now isolate all the stateful logic in hooks and use (compose them, as hooks are functions, too) into the components.


**Hooks** are used to give functional components an access to use the states and are used to manage side-effects in React. They were introduced **React 16.8**. They let developers use state and other React features without writing a class For example- State of a component It is important to note that hooks are not used inside the classes.

   **Note: Hooks cannot be used with class components**


# Why the need for Hooks?

There are multiple reasons responsible for the introduction of the Hooks which may vary depending upon the experience of developers in developing React product. Some of them are as follows:

   + **Use of ‘this’ keyword:** The first reason has to do more with javascript than with React itself. To work with classes one needs to understand how ‘this’ keyword works in javascript which is very different from how it works in other languages. It is easier to understand the concept of props, state, and uni-directional data flow but using ‘this’ keyword might lead to struggle while implementing class components. One also needs to bind event handlers to the class components. It is also observed by the React developers team also observed that classes don’t concise efficiently which leads to hot reloading being unreliable which can be solved using Hooks.
   + **Reusable stateful logics:** This reason touches advance topics in React such as Higher-order components(HOC) and the render props pattern. There is no particular way to reuse stateful component logic to React. Though this problem can be solved by the use of HOC and render props patterns it results in making the code base inefficient which becomes hard to follow as one ends up wrapping components in several other components to share the functionality. Hooks let us share stateful logic in a much better and cleaner way without changing the component hierarchy.
   + **Simplifying complex scenarios:** While creating components for complex scenarios such as data fetching and subscribing to events it is likely that all related code is not organized in one place are scattered among different life cycle methods.Hooks solve this problem by rather than forcing a split based on life-cycle method Hooks to let you split one component into smaller functions based on what pieces are related.


# Rules for using hooks

   + Only functional components can use hooks
   + Calling of hooks should always be done at top level of components
   + Hooks should not be inside conditional statements



# What are Built in Hooks in React?

React provides a bunch of standard in-built hooks:

   + **useState:** To manage states. Returns a stateful value and an updater function to update it.
   + **useEffect:** To manage side-effects like API calls, subscriptions, timers, mutations, and more.
   + useContext: To return the current value for a context.
   + **useReducer:** A useState alternative to help with complex state management.
   + **useCallback:** It returns a memorized version of a callback to help a child component not re-render unnecessarily.
   + **useMemo:** It returns a memoized value that helps in performance optimizations.
   + **useRef:** It returns a ref object with a .current property. The ref object is mutable. It is mainly used to access a child component imperatively.
   + **useLayoutEffect:** It fires at the end of all DOM mutations. It's best to use useEffect as much as possible over this one as the useLayoutEffect fires synchronously.
   + **useDebugValue:** Helps to display a label in React DevTools for custom hooks.



# What is the different categories based on use or work of hooks?

Bellow are some categories of hooks based on their work or behaviour

## State Hooks

State lets a component “remember” information like user input. For example, a form component can use state to store the input value, while an image gallery component can use state to store the selected image index.

To add state to a component, use one of these Hooks:
+ **useState** declares a state variable that you can update directly.
+ **useReducer** declares a state variable with the update logic inside a reducer function.

    function ImageGallery() {
    const [index, setIndex] = useState(0);
    // ...
    }

## Context Hooks

Context lets a component receive information from distant parents without passing it as props. For example, your app’s top-level component can pass the current UI theme to all components below, no matter how deep.

+ **useContext** reads and subscribes to a context.

    function Button() {
    const theme = useContext(ThemeContext);
    // ...
    }


## Ref Hooks

Refs let a component hold some information that isn’t used for rendering, like a DOM node or a timeout ID. Unlike with state, updating a ref does not re-render your component. Refs are an “escape hatch” from the React paradigm. They are useful when you need to work with non-React systems, such as the built-in browser APIs.

+ **useRef** declares a ref. You can hold any value in it, but most often it’s used to hold a DOM node.
+ **useImperativeHandle** lets you customize the ref exposed by your component. This is rarely used.

function Form() {
const inputRef = useRef(null);
// ...
}


## Effect Hooks

Effects let a component connect to and synchronize with external systems. This includes dealing with network, browser DOM, animations, widgets written using a different UI library, and other non-React code.

+ **useEffect** connects a component to an external system.

function ChatRoom({ roomId }) {
useEffect(() => {
    const connection = createConnection(roomId);
    connection.connect();
    return () => connection.disconnect();
}, [roomId]);
// ...
}

Effects are an “escape hatch” from the React paradigm. Don’t use Effects to orchestrate the data flow of your application. If you’re not interacting with an external system, you might not need an Effect.

There are two rarely used variations of useEffect with differences in timing:

+ **useLayoutEffect** fires before the browser repaints the screen. You can measure layout here.
+ **useInsertionEffect** fires before React makes changes to the DOM. Libraries can insert dynamic CSS here.


## Performance Hooks

A common way to optimize re-rendering performance is to skip unnecessary work. For example, you can tell React to reuse a cached calculation or to skip a re-render if the data has not changed since the previous render.

To skip calculations and unnecessary re-rendering, use one of these Hooks:

+ **useMemo** lets you cache the result of an expensive calculation.
+ **useCallback** lets you cache a function definition before passing it down to an optimized component.

function TodoList({ todos, tab, theme }) {
const visibleTodos = useMemo(() => filterTodos(todos, tab), [todos, tab]);
// ...
}

Sometimes, you can’t skip re-rendering because the screen actually needs to update. In that case, you can improve performance by separating blocking updates that must be synchronous (like typing into an input) from non-blocking updates which don’t need to block the user interface (like updating a chart).

To prioritize rendering, use one of these Hooks:

+ **useTransition** lets you mark a state transition as non-blocking and allow other updates to interrupt it.
+ **useDeferredValue** lets you defer updating a non-critical part of the UI and let other parts update first.



## Resource Hooks
Resources can be accessed by a component without having them as part of their state. For example, a component can read a message from a Promise or read styling information from a context.

To read a value from a resource, use this Hook:

use lets you read the value of a resource like a Promise or context.
function MessageComponent({ messagePromise }) {
const message = use(messagePromise);
const theme = use(ThemeContext);
// ...
}



## Other Hooks
These Hooks are mostly useful to library authors and aren’t commonly used in the application code.

+ **useDebugValue** lets you customize the label React DevTools displays for your custom Hook.
+ **useId** lets a component associate a unique ID with itself. Typically used with accessibility APIs.
+ **useSyncExternalStore** lets a component subscribe to an external store.


## Your own Hooks
You can also define your own **custom Hooks** as JavaScript functions.
