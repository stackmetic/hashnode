# JavaScript Execution Context

**Execution context** (**EC**) is defined as the environment in which the JavaScript code is executed. By environment, I mean the value of `this`, *variables*, *objects*, and *functions* JavaScript code has access to at a particular time.

Execution context in JavaScript is of three types as:

1. **Global execution context** (**GEC**): This is the default execution context in which JS code start its execution when the file first loads in the browser. All of the global code i.e. code which is not inside any function or object is executed inside the global execution context. GEC cannot be more than one because only one global environment is possible for JS code execution as the JS engine is single threaded.
    
2. **Functional execution context** (**FEC**): Functional execution context is defined as the context created by the JS engine whenever it finds any function call. Each function has its own execution context. It can be more than one. Functional execution context has access to all the code of the global execution context though vice versa is not applicable. While executing the global execution context code, if JS engine finds a function call, it creates a new functional execution context for that function. In the browser context, if the code is executing in `strict` mode value of `this` is `undefined` else it is `window` object in the function execution context.
    
3. **Eval**: Execution context inside `eval` function.
    

**Execution context stack (ECS):** Execution context stack is a stack data structure, i.e. last in first out data structure, to store all the execution stacks created during the life cycle of the script. Global execution context is present by default in execution context stack and it is at the bottom of the stack. While executing the global execution context code, if JS engines find a function call, it creates a functional execution context for that function and pushes it on top of the execution context stack. JS engine executes the function whose execution context is at the top of the execution context stack. Once all the code of the function is executed, JS engines pop out that function’s execution context and start’s executing the function which is below it.

![A Complete Guide for JavaScript Execution Context](https://www.atatus.com/blog/content/images/size/w960/2022/02/JavaScript-Execution-Context.jpeg align="left")

From the standpoint of understanding and complexity of learning, the idea of execution context has been projected as an advanced JavaScript concept in several circumstances. Yes, if not mastered with the right examples in the proper order, this may appear complex. Every newcomer to JavaScript should understand how JavaScript works and why confidence in this fundamental concept is so vital.

The most fundamental aspect of the JavaScript programming language is the execution context. In this article, we'll take a closer look at this concept to see why it's not just important but also simple to grasp.

### What is Execution Context?

The concept of an execution context is used to describe how a code works inside. JavaScript execution context refers to the environment that allows JavaScript code to be executed. The execution context determines which code section has access to the code's functions, variables, and objects.

The specified code is parsed line by line during the execution context, and the variables and functions are saved in memory. The code is evaluated and then executed in an execution context, which is similar to a [container](https://www.atatus.com/glossary/container/) that contains variables. As a result, the execution context creates an environment in which the given code can run.

The more we go into this topic, the clearer it becomes what the environment is. For the time being, think of it as a box containing all of our code.

![](https://www.atatus.com/blog/content/images/2022/02/giphy.gif align="left")

A new execution context is produced each time your application HTML executes JavaScript functions. In recursive functions, a new execution context is created each time the function calls itself, so you can theoretically have an endless number of execution contexts.

Different forms of code exist in JavaScript. In the global context, there is code. There's also code that's contained within a function context. Within an eval function, there is also code. Each of these distinct categories of code is assessed in its execution context.

![](https://www.atatus.com/blog/content/images/2022/02/giphy--1-.gif align="left")

In a nutshell, the execution context (EC) is the environment in which JavaScript code is run. By environment, I mean the current value of this, variables, objects, and functions that JavaScript code has access to.

### Types of Execution Context

In JavaScript, there are three different types of execution contexts:

**#1 Global Execution Context**

After loading and parsing the JavaScript code, the JS engine enters the default execution environment. The window object and the ***this*** object are created in the global memory by default once the JS engine is inside the global execution environment.

The window object refers to or is connected to the global object, which is always created before the JS engine enters the global execution environment and contains properties and methods like localStorage, innerWidth, and event handlers, among others.

The ***this*** object (in the global execution context) is an object that points to or is hooked to the window object.

*So, what happens if the JavaScript code has declared variables and functions?*

It will search all of the code for all variable and function declarations (variables and functions that are not nested to any other function) and place them in the global memory alongside the window and ***this object***.

**#2 Local/Function Execution Context**

When a function is called or invoked, a new execution context for that function is formed. When the JS engine sees a function call, it creates a local execution context for that function. By default, the JS engine creates an arguments object, and a ***this*** object inside the local execution context.

A **key:value** pair of parameters anticipated inside a function is stored in the arguments object. It also has a default property called length, which counts how many parameters that function has. When the function's argument is empty, the argument object defaults to a **length: 0**.

Depending on how the function is invoked, the ***this*** object in the function execution context changes. If an object reference is used to call it, the value of this is set to that object. Otherwise, the value of this variable is set to the window object or *"undefined"*.

**#3 Eval Function Execution Context**

The eval function is a function that should be avoided at all costs. An execution context is constructed and pushed into the call stack whenever the JS engine encounters an **eval()** function. It evaluates a string that is passed as an argument.

As a result, if you mistakenly sent harmful code as an argument, or if a hostile party uses this area of your code, your website might be badly harmed. This function is not recommended because there are better alternatives.

### Execution Stack (Call Stack)

The stack is a data structure for storing values in a LIFO fashion (last in, first out). A JavaScript execution stack, on the other hand, is a stack that keeps track of all the execution contexts created over the script life cycle.

A JavaScript developer should be aware that JavaScript is single-threaded, meaning that it can only perform one task in the web browser at a time. As a result, a stack is established for other actions, functions, and events, which is known as the **Execution Stack**. The **Call Stack** is another name for the execution stack.

Global Execution Context (GEC) is located at the bottom of the execution stack, and it is included by default. So, when the JS engine looks for any function in the code (i.e., during Global Execution Context execution). It constructs a Function Execution Context (FEC) for that function and pushes it to the top of the execution context stack.

The JS engine will always execute the execution context that is available at the top of the execution context stack first. When all of the code has been executed, the JS engine pops out the function's execution context and moves on to the next, and so on. When a script loads in the browser (chrome), the global execution context is usually the first thing that appears.

However, when the execution of a function is identified, the execution context is produced and placed on top of the Global Execution Context. The procedure continues until the entire code has been executed.

Consider the following example to better understand how the execution stack works:

* The code is first loaded into the browser.
    
* The GEC is then pushed/inserted at the top of the execution stack by the JS engine.
    

![](https://www.atatus.com/blog/content/images/2022/02/Execution-Stack-1.png align="left")

* The JS engine creates a new FEC for the initial function call and adds it to the top of the current execution stack as soon as it is encountered.
    

![](https://www.atatus.com/blog/content/images/2022/02/Execution-Stack-2.png align="left")

* The invocation of the second function within the first function may then be seen. As a result, the JS engine creates a new FEC for the second function and adds it to the stack's top.
    

![](https://www.atatus.com/blog/content/images/2022/02/Execution-Stack-3.png align="left")

* When the second function is finished, the execution function is popped off of the stack, and the controls are moved to the next execution context in the stack, which is only the first function execution context.
    

![](https://www.atatus.com/blog/content/images/2022/02/Execution-Stack-2-1.png align="left")

* When the first function is fully performed, the first function's execution stack is popped out of the stack. As a result, control returns to the code's GEC.
    

![](https://www.atatus.com/blog/content/images/2022/02/Execution-Stack-1-1.png align="left")

Finally, when the full code has been executed, the JS engine removes the GEC from the current stack and JavaScript stops execution.

### Creating an Execution Context

First, an execution context must be created, and then it must be managed. There are two methods for establishing the execution context:

1. Creation Phase
    
2. Execution Phase
    

### #1 Creation Phase

The JS engine invokes a function but does not start its execution during the creation phase. The JS engine starts the compilation step in this phase and examines the function code for compiling but does not run it.

During the creation phase, two-state components are created:

1. Lexical Environment
    
2. Variable Environment
    

The following is a conceptual representation of the execution context:

```javascript
GlobalExecutionContext = {
    LexicalEnvironment: {},
    VariableEnvironment: {},
}
```

* A **Lexical Environment** component is a structure based on the lexical nesting structure of JavaScript code that defines the association of identifiers to the values of variables and functions. Binding is the process of associating an identifier with the values of variables and functions.
    
* A **Variable Environment** component is a Lexical Environment that defines the relationship between identifiers and the values of variables, but not functions.
    

The difference between these two is that the identifier is bounded in the variable. The Lexical Environment stores identifier bindings to the values of variables (let and const) and functions, whereas the Variable Environment simply stores identifier bindings to the values of the variable (var).

*What is the Lexical Environment made up of?*

![](https://www.atatus.com/blog/content/images/2022/02/giphy--2--1.gif align="left")

#### Environment Record

There is an Environment Record for each Lexical Environment. The identifier bindings that are established inside the scope of the lexical environment are recorded in the Environment Record.

A new Environment Record is created each time JavaScript code is evaluated (var/func declarations or assignments) to record the identifier bindings created by that code. In JavaScript, this environment is referred to as the scope.

The **\[\[OuterEnv\]\]** field of every Environment Record is either *null* or a reference to an outer Environment Record. The outer environment object is the reason why a child function gets access to its parent's scope.

When the JS engine encounters a variable inside a function, it will look in the current function's environment record for the variable's value (local memory).

If it can't find the variable within, it will search the outer scope (its parent environment record) all the way up to the global scope until it finds it. The scope chain is the name given to this lookup procedure. In future articles, we'll aim to go deeper into the scope chain.

Within the Environment Record, there are three types of subclasses:

1. **Declarative Environment Record**  
    Variables, classes, modules, and/or function declarations are all stored here, as the name implies. The collection of identifiers defined by the declarations contained inside the scope of a declarative Environment Record is bound.
    
2. **Object Environment Record**  
    The bindings for all built-in globals are stored in this environment record in the global execution context. The window object that refers to the global object is this one. Global variables and functions are added to the global execution context's object environment record, which is why global variables like a ***window.localStorage*** and ***window.var*** name can be accessed. The arguments object and ***this*** object make up the object environment record in the local/function execution context.
    
3. **Global Environment Record**  
    Although a global Environment Record is theoretically a single record, it is stated as a composite [encapsulating](https://www.atatus.com/glossary/encapsulation/) both an object and a declarative Environment Record. It has no exterior environment because it is **\[\[OuterEnv\]\]** is *null*.  
    It includes an associated global object whose properties offer some of the global environment's identifier bindings, and it may be prepopulated with identifier bindings. Additional attributes may be added to the global object as JavaScript code is executed, and the initial properties may be updated.
    

Let us now visualize the execution context within the Creation Phase conceptually. Examine the following JS code:

```javascript
var name = "Joe";
let input = "Hey!!!";

function broadcast(message) {
    return `${name} says ${message}`;
}
console.log(broadcast(input));
```

Note that when we say "conceptually," we don't mean that the pseudocode below is a tangible representation of the environment that the JS engine creates; rather, it's just a way to grasp the concept by visualizing it.

Using the code snippet above, let's try to walk through each stage of what happens during the Creation Phase:

1. Creates and pushes a global execution context into the call stack.
    
2. Create bindings between the window and global objects.
    
3. Make ***this*** objects bindings to the window object. ***this*** object binding will change based on how the function is called and whether the strict mode is enabled.
    
4. Creates an identifier ***name*** in global memory with the value *undefined* as its initial value. **Hoisting** is the term for this procedure.
    
5. Creates an identifier ***input*** in global memory that is not initialized or has no initial value.
    
6. Creates an identifier *broadcast* in global memory and stores the entire broadcast function specification in it. This is also a hoisted function.
    

After that, we'll discuss how the JavaScript code is performed.

### #2 Execution Phase

After you've completed the creation step, you'll move on to the execution phase. The JS engines scan over the function in the code one more time, updating the variable object with the values of the variables and then running the code, which is known as an execution phase.

Variable binding initializations, variable assignments, mutability and immutability checking, variable binding deletions, function call execution, and so on are all occurring during this phase.

Let's look at the execution stage for the example we just discussed:

1. Take the value of the variable ***name*** and bind it to the memory's identifier.
    
2. Take the value of the variable ***input*** and bind it to the memory's identifier.
    
3. When a console log method is encountered, the arguments are evaluated immediately.
    
4. When it encounters a *broadcast* function call, it constructs a new local execution context for it and pushes it to the top of the call stack.
    
5. The broadcast function execution context enters the Creation Phase.
    
6. Creates ***arguments*** object in the function's local memory with a length of 0 as its starting value.
    
7. To the first index of the arguments object, append the provided parameter ***message***.
    
8. Creates an identifier ***message*** and stores the value given to the function call's argument in the function's local memory.
    
9. Inside the function block, the return statement is evaluated.
    
10. When it sees a variable ***name***, it searches the function's local memory for that variable.
    
11. It couldn't find the identifier ***name*** in local memory, so it went to its parent scope (global memory) to look for it.
    
12. It locates the identifier name in global memory, then swaps the value to the variable reference.
    
13. When it sees a variable ***message***, it looks up that variable in the function's local memory.
    
14. It locates the identification ***message*** in local memory, then swaps the value to the variable reference.
    
15. The evaluated result of the broadcast function execution context is returned and the call stack is popped off.
    
16. With the returned result, pass the control to its caller context (the global execution context).
    
17. It displays in the console, **Joe says "Hey!!!"**
    
18. The JS engine ends after the global execution context is removed from the call stack.
    

That's a lot!

![](https://www.atatus.com/blog/content/images/2022/02/giphy--3--1.gif align="left")

There's a lot more going on in the Execution Phase, such as object mutability and immutability checks, but I tried to keep the processes simple so that the primary idea in this article wouldn't get lost.

```javascript
GlobalExecutionContext = {
    LexicalEnvironment: {
        EnvironmentRecord: {
            DeclarativeEnvironmentRecord: {
                input: "Hey!!!",
                broadcast: {
                    LocalExecutionContext: {
                        LexicalEnvironment: {
                            EnvironmentRecord: {
                                DeclarativeEnvironmentRecord: {
                                    message: "Hey!!!",
                                },
                                ObjectEnvironmentRecord: {
                                    arguments: {
                                        0: message,
                                        length: 1
                                    }
                                    this: < ref.to window obj. >
                                },
                            },
                            OuterEnv: < ref.to LexicalEnvironment of the GlobalExecutionContext > ,
                        },
                    },
                },
            },
            ObjectEnvironmentRecord: {
                window: < ref.to Global obj. > ,
                this: < ref.to window Obj. > ,
            },
            OuterEnv: < null > ,
        },
    },
    VariableEnvironment: {
        EnvironmentRecord: {
            DeclarativeEnvironmentRecord: {
                name: "Joe"
            },
        },
    },
}
```

However, if you want to learn more about JavaScript, you can go through the [JavaScript Spec](https://tc39.es/ecma262/#sec-executable-code-and-execution-contexts).

### Why is the Execution Context Concept Important?

According to some research, the human brain has the capacity to store as much information as the entire internet in its memory.

![](https://www.atatus.com/blog/content/images/2022/02/giphy--4--1.gif align="left")

*But isn't that something we shouldn't take for granted?*

As a result, a reasonable query may be, "Why is this topic important to learn?"

The Execution Context in JavaScript provides the foundation for comprehending many other essential concepts. We frequently encounter a great deal of misunderstanding in each of the following notions simply because we misunderstand the fact underlying Execution Context.

* [Hoisting](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting)
    
* [Scope](https://developer.mozilla.org/en-US/docs/Glossary/Scope)
    
* [Scope Chain](https://medium.com/@aastha6348/understanding-scopes-and-scope-chain-in-javascript-4d87f7a4b144#:~:text=Scope%20chains%20establish%20the%20scope,link%20is%20called%20the%20chain.)
    
* [Closure](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)
    
* [Event Loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop)
    

Once we have a thorough understanding of these ideas as JavaScript Developers, we will be able to introduce fewer errors into the source code, become boss at doing outstanding code reviews, have amazing eyes for debugging, and find easier solutions to deal with production issues