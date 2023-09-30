# What is Props in React?

**In ReactJS**, the **props** are a type of object where the value of attributes of a tag is stored.
The word “props” implies “properties”, and its working functionality is quite similar to
HTML attributes.

** Props are used to pass data and event handlers to the children components **

Basically, these props components are read-only components. In ReactJS, the data can be
passed from one component to another component using these props, similar to how the
arguments are passed in a function. Inside the component, we can add the attributes called
props; however, we cannot change or modify props inside the component as they are immutable.

eg: <CreateList title="India" />

    In CreateList component title is passed as a **PROPS** and inside CreateList component we
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
