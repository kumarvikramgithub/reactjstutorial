# Q1. what is useState?

**useState** is a React Hook that lets you add a state variable to your component.

    Eg: const [state, setState] = useState(initialState);

   ## 1.1. useState(initialState)
The convention is to name state variables like **[something, setSomething]** using **array destructuring.**

   ## 1.1.1. Parameters
   + **initialState:** The value you want the state to be initially. It can be a value of any type, but there is a special behavior for functions. This argument is ignored after the initial render.
    
    + If you pass a function as initialState, it will be treated as an initializer function. It should be pure, should take no arguments, and should return a value of any type. React will call your initializer function when initializing the component, and store its return value as the initial state. See an example below.

   ## 1.1.2. Returns
   + **useState** returns an array with exactly two values:

        + The current state. During the first render, it will match the initialState you have passed.
        + The set function that lets you update the state to a different value and trigger a re-render.


## Note:
   + useState is a Hook, so you can only call it at the top level of your component or your own Hooks. You can’t call it inside loops or conditions. If you need that, extract a new component and move the state into it.
    
   + In Strict Mode, React will call your initializer function twice in order to help you find accidental impurities. This is development-only behavior and does not affect production. If your initializer function is pure (as it should be), this should not affect the behavior. The result from one of the calls will be ignored.


    ## 1.2. set functions, like setSomething(nextState) 

    The set function returned by **useState** lets you update the state to a different value and trigger a re-render. You can pass the next state directly, or a function that calculates it from the previous state:

        Eg:
            const [name, setName] = useState('Edward');

            function handleClick() {
            setName('Taylor');
            setAge(a => a + 1);
            // ...

            }

 
   ## 1.2.1. Parameters 
   + **nextState:** The value that you want the state to be. It can be a value of any type, but there is a special behavior for functions.

       + If you pass a function as nextState, it will be treated as an updater function. It must be pure, should take the pending state as its only argument, and should return the next state. React will put your updater function in a queue and re-render your component. During the next render, React will calculate the next state by applying all of the queued updaters to the previous state. See an example below.


   ## 1.2.2. Returns 

   set functions do not have a return value.

   ## Note: 

   + The **set** function **only updates the state variable for the next render**. If you read the state variable after calling the set function, you will still get the old value that was on the screen before your call.

   + If the new value you provide is identical to the current state, as determined by an Object.is comparison, React will skip re-rendering the component and its children. This is an optimization. Although in some cases React may still need to call your component before skipping the children, it shouldn’t affect your code.

   + React **batches state updates**. It updates the screen after all the event handlers have run and have called their set functions. This prevents multiple re-renders during a single event. In the rare case that you need to force React to update the screen earlier, for example to access the DOM, you can use **flushSync**.

   + Calling the set function during rendering is only allowed from within the currently rendering component. React will discard its output and immediately attempt to render it again with the new state. This pattern is rarely needed, but you can use it to store information from the previous renders. See an example below.

   + In Strict Mode, React will call your updater function twice in order to help you find accidental impurities. This is development-only behavior and does not affect production. If your updater function is pure (as it should be), this should not affect the behavior. The result from one of the calls will be ignored.