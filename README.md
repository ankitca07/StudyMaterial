Okay, here is a question bank with over 50 questions suitable for a Node.js and React.js fresher interview, covering fundamental concepts.

**I. JavaScript Fundamentals (Prerequisite for Both)**

1.  **Q: What's the difference between `var`, `let`, and `const`?**
    **A:**
    *   `var`: Function-scoped (or globally scoped if declared outside a function). Can be re-declared and updated. Hoisted (declaration moved to top, initialized with `undefined`). Generally discouraged in modern JS.
    *   `let`: Block-scoped (`{}`). Can be updated but not re-declared within the same scope. Hoisted but not initialized (Temporal Dead Zone). Preferred for variables that need reassignment.
    *   `const`: Block-scoped. Cannot be updated or re-declared. Must be initialized during declaration. Hoisted but not initialized (Temporal Dead Zone). Preferred for variables that shouldn't be reassigned (note: for objects/arrays, the *contents* can still be changed, just not the variable's reference).

2.  **Q: Explain Arrow Functions (`=>`). How do they differ from regular functions regarding `this`?**
    **A:** Arrow functions provide a shorter syntax for writing functions. The key difference is how they handle the `this` keyword. Arrow functions do *not* have their own `this` context; they inherit `this` from the surrounding (lexical) scope where they are defined. Regular functions get their own `this` value depending on how they are called (e.g., object method, standalone function, constructor).

3.  **Q: What are JavaScript data types? Differentiate between primitive and non-primitive types.**
    **A:**
    *   **Primitive Types:** Immutable values. `string`, `number`, `bigint`, `boolean`, `undefined`, `symbol`, `null`.
    *   **Non-Primitive Type:** `object` (includes arrays, functions, regular objects). Objects are mutable and are reference types (variables hold a reference/address to the object in memory).

4.  **Q: What are truthy and falsy values in JavaScript? Give examples.**
    **A:** In contexts where a boolean is expected (like an `if` statement), JavaScript coerces values.
    *   **Falsy Values:** `false`, `0`, `-0`, `0n` (BigInt zero), `""` (empty string), `null`, `undefined`, `NaN`.
    *   **Truthy Values:** Any value that is not falsy. Examples: `"hello"`, `123`, `true`, `[]` (empty array), `{}` (empty object), `function() {}`.

5.  **Q: Explain the purpose of `map()`, `filter()`, and `reduce()` array methods.**
    **A:**
    *   `map()`: Creates a *new* array by calling a provided function on every element in the original array. Returns an array of the same length with transformed elements.
    *   `filter()`: Creates a *new* array containing only the elements from the original array that pass a test (return `true`) implemented by the provided function.
    *   `reduce()`: Executes a reducer function on each element of the array, resulting in a single output value (e.g., sum, combined object). It takes an accumulator and the current element as arguments.

6.  **Q: What is asynchronous JavaScript? Explain Callbacks, Promises, and Async/Await.**
    **A:** Asynchronous JavaScript allows operations (like network requests or file reading) to happen without blocking the main thread.
    *   **Callbacks:** Functions passed as arguments to other functions, to be executed later when an async operation completes. Can lead to "Callback Hell" (deeply nested callbacks).
    *   **Promises:** Objects representing the eventual completion (or failure) of an asynchronous operation and its resulting value. They have states (pending, fulfilled, rejected) and methods like `.then()` (for success), `.catch()` (for error), and `.finally()`. Improve readability over callbacks.
    *   **Async/Await:** Syntactic sugar built on top of Promises. `async` makes a function return a Promise. `await` pauses the execution of an `async` function until a Promise settles (resolves or rejects), making asynchronous code look more synchronous and easier to read/write. Must be used inside an `async` function.

7.  **Q: What is JSON?**
    **A:** JSON (JavaScript Object Notation) is a lightweight data-interchange format. It's easy for humans to read and write and easy for machines to parse and generate. It's commonly used for transmitting data between a server and a web application (e.g., in APIs).

8.  **Q: What does the `===` operator do? How is it different from `==`?**
    **A:**
    *   `===` (Strict Equality): Compares both value and type *without* performing type coercion. Generally preferred.
    *   `==` (Loose Equality): Compares values after performing type coercion if the types are different. Can lead to unexpected results.

9.  **Q: What is hoisting in JavaScript?**
    **A:** Hoisting is JavaScript's default behavior of moving declarations (of variables declared with `var` and function declarations) to the top of their current scope (function or global) before code execution. Note that only the declaration is hoisted, not the initialization (for `var`, it's initialized with `undefined`). `let` and `const` are hoisted but not initialized, leading to a Temporal Dead Zone.

10. **Q: What is a Closure?**
    **A:** A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). In other words, a closure gives you access to an outer function's scope from an inner function, even after the outer function has finished executing.

**II. Node.js**

11. **Q: What is Node.js?**
    **A:** Node.js is a JavaScript runtime environment built on Chrome's V8 JavaScript engine. It allows you to execute JavaScript code *outside* of a web browser, primarily used for building server-side applications, APIs, command-line tools, etc.

12. **Q: Explain the concept of Node.js being single-threaded and using non-blocking I/O.**
    **A:** Node.js uses a single main thread to execute JavaScript code. However, for I/O operations (like reading files, network requests, database queries), it uses a non-blocking, event-driven architecture. Instead of waiting for an I/O operation to complete, Node.js registers a callback and continues executing other code. When the I/O operation finishes, the callback is placed in an event queue and processed by the event loop when the main thread is free. This allows Node.js to handle many concurrent connections efficiently without needing multiple threads for each connection.

13. **Q: What is the Event Loop in Node.js?**
    **A:** The event loop is the core mechanism that enables Node.js's non-blocking I/O. It constantly checks if the call stack is empty. If it is, it checks the event queue (containing callbacks for completed async operations). If there are callbacks in the queue, it dequeues them one by one and pushes them onto the call stack for execution.

14. **Q: What is NPM (or Yarn)? What is its purpose?**
    **A:** NPM (Node Package Manager) is the default package manager for Node.js. Yarn is an alternative popular package manager. Their purposes are:
    *   Managing project dependencies (libraries/packages your project uses).
    *   Installing, updating, and removing packages.
    *   Running scripts defined in `package.json`.
    *   Publishing your own packages.

15. **Q: What is the `package.json` file? What are some key properties?**
    **A:** `package.json` is a metadata file located in the root of a Node.js project. It contains information about the project, such as:
    *   `name`: Project name.
    *   `version`: Project version.
    *   `description`: Project description.
    *   `main`: The entry point file for the application (e.g., `index.js`).
    *   `scripts`: Defines command aliases (e.g., `npm start`, `npm test`).
    *   `dependencies`: Packages required for the application to run in production.
    *   `devDependencies`: Packages needed only for development (e.g., testing libraries, build tools).
    *   `license`, `author`, `repository`, etc.

16. **Q: What is the difference between `dependencies` and `devDependencies`?**
    **A:**
    *   `dependencies`: Packages required for the application to run correctly in production. They get installed when someone runs `npm install` on the project.
    *   `devDependencies`: Packages used only during development and testing (e.g., linters, testing frameworks, bundlers like Webpack). They are typically not needed for the production deployment. Installed via `npm install --save-dev` or `yarn add --dev`.

17. **Q: What is the `node_modules` folder?**
    **A:** This folder contains the actual code for all the project's dependencies (both `dependencies` and `devDependencies`) downloaded by NPM or Yarn. It should typically *not* be committed to version control (like Git) because it can be large and can be regenerated using `npm install` based on `package.json` and `package-lock.json`.

18. **Q: What is the purpose of `package-lock.json` (or `yarn.lock`)?**
    **A:** This file records the *exact* versions of dependencies (and their sub-dependencies) that were installed. It ensures that every installation (`npm install`) results in the exact same `node_modules` tree, providing consistency across different environments (developer machines, CI/CD, production) and preventing unexpected issues due to dependency version changes. It *should* be committed to version control.

19. **Q: How do you import modules in Node.js? (CommonJS vs ES Modules)**
    **A:**
    *   **CommonJS (Traditional):** Uses `require()` to import modules and `module.exports` or `exports` to export them. Example: `const fs = require('fs'); module.exports = myFunction;`
    *   **ES Modules (Modern):** Uses `import` to import modules and `export` (or `export default`) to export them. Requires either using the `.mjs` file extension or setting `"type": "module"` in `package.json`. Example: `import fs from 'fs'; export default myFunction;` Freshers should be aware of both, especially `require` which is still very common in older Node codebases.

20. **Q: Name some built-in Node.js modules you have used or know of.**
    **A:** Common examples:
    *   `fs` (File System): For interacting with the file system (reading, writing files).
    *   `http` / `https`: For creating HTTP/HTTPS servers and clients.
    *   `path`: For handling and transforming file paths in a platform-independent way.
    *   `os`: Provides operating system-related utility methods.
    *   `events`: Used for handling events (Node's event-driven architecture core).
    *   `url`: For URL parsing and resolution.

21. **Q: How would you create a simple HTTP server in Node.js?**
    **A:** Using the built-in `http` module:
    ```javascript
    const http = require('http');

    const server = http.createServer((req, res) => {
      res.writeHead(200, { 'Content-Type': 'text/plain' });
      res.end('Hello World!\n');
    });

    const port = 3000;
    server.listen(port, () => {
      console.log(`Server running at http://localhost:${port}/`);
    });
    ```

22. **Q: What are environment variables (`process.env`) used for in Node.js?**
    **A:** Environment variables are used to store configuration settings (like database credentials, API keys, port numbers) outside the application code. This improves security (sensitive data isn't hardcoded) and flexibility (configuration can be changed for different environments like development, staging, production without code changes). Accessed via the `process.env` object (e.g., `process.env.PORT`).

23. **Q: How do you handle errors in asynchronous Node.js code?**
    **A:**
    *   **Callbacks:** Typically use an "error-first" convention where the first argument to the callback function is reserved for an error object (or `null` if no error occurred).
    *   **Promises:** Use the `.catch()` method on the Promise chain.
    *   **Async/Await:** Use standard `try...catch` blocks around `await` calls.

24. **Q: What is middleware (in the context of frameworks like Express)?**
    **A:** Middleware functions are functions that have access to the request object (`req`), the response object (`res`), and the `next` function in the application's request-response cycle. They can execute code, make changes to `req` and `res`, end the cycle, or call the `next` middleware in the stack. Used for tasks like logging, authentication, data validation, compression, etc. (Even if not asked about Express specifically, understanding the concept is good).

25. **Q: What is RESTful API?**
    **A:** REST (Representational State Transfer) is an architectural style for designing networked applications. A RESTful API is an API that adheres to REST principles. Key characteristics include:
    *   Statelessness (server doesn't store client state between requests).
    *   Client-Server architecture.
    *   Cacheability.
    *   Use of standard HTTP methods (GET, POST, PUT, DELETE, PATCH).
    *   Resources identified by URIs (e.g., `/users`, `/products/123`).
    *   Often uses JSON for data exchange.

**III. React.js**

26. **Q: What is React? What problem does it solve?**
    **A:** React is a JavaScript library (developed by Facebook) for building user interfaces (UIs), particularly single-page applications. It allows developers to create reusable UI components and efficiently update the UI in response to data changes. It primarily solves the problem of keeping complex UIs in sync with underlying data.

27. **Q: What is the Virtual DOM? How does it help performance?**
    **A:** The Virtual DOM (VDOM) is a programming concept where a virtual representation of the UI is kept in memory and synced with the "real" DOM (the browser's Document Object Model). When a component's state changes, React first updates the VDOM. Then, it compares the updated VDOM with the previous VDOM version (this process is called "diffing"). Finally, it calculates the most efficient way to make these changes in the real DOM, updating only the parts of the actual DOM that have changed, minimizing direct DOM manipulation which is often slow.

28. **Q: What is JSX?**
    **A:** JSX (JavaScript XML) is a syntax extension for JavaScript recommended for use with React. It looks similar to HTML and allows you to write UI structures declaratively within your JavaScript code. JSX is not understood by browsers directly; it needs to be transpiled (usually by tools like Babel) into regular JavaScript function calls (`React.createElement()`).

29. **Q: What is a React Component? Differentiate between Functional and Class Components.**
    **A:** Components are the building blocks of a React application. They are independent, reusable pieces of UI.
    *   **Functional Components:** Modern standard. Defined as JavaScript functions. They accept `props` as an argument and return JSX. State and lifecycle features are handled using Hooks (like `useState`, `useEffect`).
    *   **Class Components:** Older way. Defined as ES6 classes extending `React.Component`. They have a `render()` method that returns JSX. State is managed using `this.state` and lifecycle methods (like `componentDidMount`, `componentDidUpdate`). Functional components with Hooks are generally preferred now for new development due to simpler syntax and better composability.

30. **Q: What are Props in React?**
    **A:** Props (short for properties) are read-only objects used to pass data *down* from a parent component to a child component. They allow components to be configured and customized. Props should not be modified directly by the child component (they are immutable from the child's perspective).

31. **Q: What is State in React?**
    **A:** State is an object that holds data specific to a component, which can change over time (usually due to user interaction or network responses). When a component's state changes, React re-renders the component and its children to reflect the new data. In functional components, state is managed using the `useState` Hook.

32. **Q: Explain the difference between State and Props.**
    **A:**
    *   **Origin:** Props are passed *into* a component from its parent. State is managed *within* the component itself.
    *   **Mutability:** Props are read-only for the receiving component. State can be updated by the component itself (using `this.setState` in class components or the setter function from `useState` in functional components).
    *   **Flow:** Data flows down via props (unidirectional data flow). State changes trigger re-renders within the component where the state resides.

33. **Q: What are React Hooks? Why were they introduced?**
    **A:** Hooks are functions (like `useState`, `useEffect`, `useContext`) that let you "hook into" React state and lifecycle features from functional components. They were introduced in React 16.8 to allow developers to use state and other React features without writing class components, leading to more reusable stateful logic and simpler component structures.

34. **Q: Explain the `useState` Hook.**
    **A:** `useState` is a Hook that allows you to add state to functional components.
    *   It takes the initial state value as an argument.
    *   It returns an array containing two elements:
        1.  The current state value.
        2.  A function to update that state value.
    *   Example: `const [count, setCount] = useState(0);`

35. **Q: Explain the `useEffect` Hook. What is the dependency array used for?**
    **A:** `useEffect` is a Hook that lets you perform side effects in functional components. Side effects include data fetching, subscriptions, timers, logging, and manually changing the DOM.
    *   It takes a function (the effect) as the first argument. This function runs after the component renders.
    *   It optionally takes a second argument: a dependency array.
        *   If omitted, the effect runs after *every* render.
        *   If an empty array (`[]`), the effect runs only *once* after the initial render (like `componentDidMount`).
        *   If it contains variables (`[propA, stateB]`), the effect runs only when any of those dependency values change between renders.
    *   It can optionally return a cleanup function, which runs before the component unmounts or before the effect runs again.

36. **Q: How do you handle events (like clicks) in React?**
    **A:** You attach event handlers (like `onClick`, `onChange`, `onSubmit`) directly to JSX elements, similar to HTML, but using camelCase naming. The event handler is typically a function defined within your component.
    *   Example: `<button onClick={handleClick}>Click Me</button>` where `handleClick` is a function in the component's scope.

37. **Q: How do you render lists of items in React? What is the importance of the `key` prop?**
    **A:** You typically use array methods like `map()` to iterate over an array of data and return a JSX element for each item.
    *   **`key` Prop:** When rendering a list, React requires you to provide a unique `key` prop to each list item element (`<li key={item.id}>`). Keys help React identify which items have changed, been added, or been removed, allowing for efficient updates of the list in the DOM. The key should be a stable, unique identifier (like an ID from your data) for each item within that list. Using the array index as a key is generally discouraged if the list can change order, be filtered, or have items inserted/deleted.

38. **Q: Explain conditional rendering in React.**
    **A:** Conditional rendering allows you to render different JSX elements based on certain conditions (like component state or props). Common ways to achieve this:
    *   **`if` statements:** Can be used outside the JSX, preparing variables to hold the JSX to be rendered.
    *   **Ternary Operator (`condition ? exprIfTrue : exprIfFalse`):** Useful for simple inline conditional rendering.
    *   **Logical `&&` Operator (`condition && expression`):** Renders the `expression` only if the `condition` is truthy. Useful for rendering an element only if a condition is met, otherwise rendering nothing.
    *   Storing JSX in variables and rendering those variables.

39. **Q: How can a child component communicate with its parent component?**
    **A:** The standard way is for the parent component to pass a callback function down to the child component via props. The child component can then call this function (passing data as arguments if needed) when an event occurs, effectively sending information back up to the parent.

40. **Q: What is Prop Drilling?**
    **A:** Prop drilling is the process of passing props down through multiple layers of nested components, even if intermediate components don't need the props themselves, just to get them to a deeply nested child that *does* need them. It can make code harder to maintain and refactor. (Awareness of the problem is key for a fresher).

41. **Q: What is the Context API? When might you use it?**
    **A:** The Context API is a React feature designed to solve the prop drilling problem. It provides a way to pass data through the component tree without having to pass props down manually at every level. You might use it for "global" data that many components need, such as theme data (light/dark mode), user authentication status, or language preferences.

42. **Q: What are Controlled Components in React forms?**
    **A:** A controlled component is an input form element (like `<input>`, `<textarea>`, `<select>`) whose value is controlled by React state. The component's state is the "single source of truth" for the input's value. Changes are handled by an `onChange` handler that updates the state.

43. **Q: What is React Router? What is its purpose?**
    **A:** React Router is a popular third-party library used for handling routing in React applications. It allows you to define different "pages" or views in your single-page application and navigate between them based on the URL, without causing a full page refresh.

44. **Q: Briefly explain the concept of component lifecycle (or its equivalent with Hooks).**
    **A:** Component lifecycle refers to the different phases a component goes through from its creation to its removal from the DOM.
    *   **Mounting:** Component is created and inserted into the DOM. (Hooks equivalent: `useEffect` with `[]` dependency array for setup).
    *   **Updating:** Component re-renders due to changes in props or state. (Hooks equivalent: `useEffect` with dependencies, code within the component body).
    *   **Unmounting:** Component is removed from the DOM. (Hooks equivalent: Cleanup function returned from `useEffect`).

45. **Q: What is `create-react-app` (or Vite for React)?**
    **A:** `create-react-app` (CRA) is an officially supported toolchain for creating new React projects with a pre-configured development setup (including Babel, Webpack, Jest, ESLint) with zero configuration needed initially. Vite is a newer, faster build tool and dev server alternative that is gaining popularity for creating React (and other framework) projects. They handle the complex build setup, allowing developers to focus on writing React code.

**IV. General / Web Concepts**

46. **Q: What are common HTTP methods, and what are they typically used for?**
    **A:**
    *   `GET`: Retrieve data from a specified resource.
    *   `POST`: Submit data to be processed to a specified resource (often causing a change in state or side effects on the server, like creating a new resource).
    *   `PUT`: Replace the entire target resource with the request payload.
    *   `DELETE`: Delete the specified resource.
    *   `PATCH`: Apply partial modifications to a resource.

47. **Q: What is Git? Why is version control important?**
    **A:** Git is a distributed version control system (VCS). It tracks changes to files over time, allowing developers to collaborate, revert to previous versions, manage different features in parallel (branches), and understand the history of a project. Version control is crucial for teamwork, preventing data loss, managing code complexity, and enabling CI/CD pipelines.

48. **Q: Briefly describe the request/response cycle in a web application.**
    **A:**
    1.  **Client Request:** The user's browser (client) sends an HTTP request to a server's URL (e.g., typing an address, clicking a link, submitting a form). The request includes a method (GET, POST, etc.), headers, and potentially a body (data).
    2.  **Server Processing:** The server (e.g., a Node.js application) receives the request, processes it (e.g., reads data from a database, performs calculations, interacts with other services), often using routing to determine how to handle the specific request path and method.
    3.  **Server Response:** The server sends an HTTP response back to the client. The response includes a status code (e.g., 200 OK, 404 Not Found, 500 Internal Server Error), headers, and usually a body (e.g., HTML, JSON data).
    4.  **Client Rendering:** The browser receives the response and renders the content (e.g., displays the HTML page, uses JavaScript to update the UI based on JSON data).

49. **Q: How do you debug Node.js applications?**
    **A:** Common methods include:
    *   Using `console.log()` statements (simple but effective for basic checks).
    *   Using the built-in Node.js debugger (`node inspect your_script.js`).
    *   Using the debugger integrated into code editors like VS Code (setting breakpoints, stepping through code, inspecting variables).
    *   Using browser developer tools (e.g., Chrome DevTools) by running Node with the `--inspect` flag.

50. **Q: How do you debug React applications?**
    **A:** Common methods include:
    *   Using `console.log()` within components.
    *   Using browser developer tools (inspecting elements, viewing console errors/logs).
    *   Using the React Developer Tools browser extension (inspecting component hierarchy, props, state, and hooks).
    *   Setting breakpoints in the browser's debugger (Sources tab).

51. **Q: What resources do you use to learn and stay updated with Node.js and React?**
    **A:** (This assesses learning attitude) Examples: Official documentation (Node.js docs, React docs), blogs (React blog, Node.js blog, Smashing Magazine, CSS-Tricks, specific developer blogs), online courses (Udemy, Coursera, Frontend Masters), YouTube channels, Twitter, developer communities (Stack Overflow, Dev.to, Reddit), newsletters.

52. **Q: Describe a small project you built using Node.js or React. What challenges did you face?**
    **A:** (This assesses practical application and problem-solving). The fresher should be able to briefly describe a tutorial project or a simple personal project (e.g., a simple To-Do list API with Node/Express, a basic portfolio website with React) and mention a simple challenge like understanding state management, handling async operations, or setting up routing.

Okay, here are more interview questions suitable for a Node.js and React.js fresher, expanding on the previous list:

**V. JavaScript (Further Fundamentals)**

53. **Q: Explain object destructuring and array destructuring.**
    **A:** Destructuring is a JavaScript syntax expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables.
    *   **Object Destructuring:** `const { name, age } = userObject;` extracts `name` and `age` properties from `userObject` into variables `name` and `age`.
    *   **Array Destructuring:** `const [first, second] = myArray;` extracts the first element into `first` and the second into `second`.

54. **Q: What are the spread (`...`) and rest (`...`) operators? Give examples.**
    **A:** Both use the `...` syntax but in different contexts:
    *   **Spread Operator:** Expands an iterable (like an array or string) or object properties into individual elements/properties. Used for copying arrays/objects, merging them, or passing array elements as individual arguments to functions.
        *   `const arr2 = [...arr1];` (Copy array)
        *   `const obj2 = {...obj1};` (Copy object)
        *   `myFunction(...argsArray);` (Pass array elements as args)
    *   **Rest Operator:** Collects multiple elements or arguments into a single array or object properties into a single object. Used typically in function parameters or destructuring.
        *   `function sum(...numbers) { /* numbers is an array */ }`
        *   `const [first, ...rest] = myArray;` (rest gets remaining elements)
        *   `const { id, ...otherProps } = myObject;` (otherProps gets remaining properties)

55. **Q: What is `Promise.all()` and `Promise.race()`?**
    **A:** These are static methods on the `Promise` object for handling multiple promises:
    *   `Promise.all(iterable)`: Takes an iterable (e.g., an array) of promises. It returns a single promise that fulfills when *all* the promises in the iterable have fulfilled, resolving to an array of their results. If *any* promise rejects, `Promise.all()` immediately rejects with the reason of the first rejected promise.
    *   `Promise.race(iterable)`: Takes an iterable of promises. It returns a single promise that fulfills or rejects as soon as *one* of the promises in the iterable fulfills or rejects, with the value or reason from that first settled promise.

56. **Q: What is the difference between `localStorage` and `sessionStorage`?**
    **A:** Both are web storage APIs allowing browsers to store key/value pairs locally.
    *   `localStorage`: Stores data with no expiration date. Data persists even after the browser window is closed and reopened. Available across all tabs/windows from the same origin.
    *   `sessionStorage`: Stores data for only one session. Data is cleared when the browser tab/window is closed. Each tab/window has its own separate `sessionStorage`.

57. **Q: Explain the `this` keyword in different JavaScript contexts (global, function, method, arrow function, event handler).**
    **A:** The value of `this` depends on how a function is called:
    *   **Global Context (non-strict mode):** `this` refers to the global object (`window` in browsers, `global` in Node.js, although less relevant in modern Node modules). In strict mode, it's `undefined`.
    *   **Regular Function Call (non-strict mode):** `this` refers to the global object (`window`/`global`). In strict mode, it's `undefined`.
    *   **Object Method Call (`obj.myMethod()`):** `this` refers to the object the method was called on (`obj`).
    *   **Constructor Call (`new MyClass()`):** `this` refers to the newly created instance of the class/function.
    *   **Arrow Function:** `this` is lexically bound; it inherits `this` from the surrounding scope where the arrow function was *defined*, not where it's called.
    *   **DOM Event Handler (inline or `addEventListener` with regular function):** `this` usually refers to the DOM element that triggered the event. If using an arrow function as the handler, `this` retains its lexical value.

**VI. Node.js (Deeper Dive)**

58. **Q: What are Streams in Node.js? Why are they useful?**
    **A:** Streams are objects that let you read data from a source or write data to a destination in a continuous fashion, piece by piece (chunks), instead of loading everything into memory at once. They are useful for handling large amounts of data (like large files or network responses) efficiently, improving memory usage and performance. Examples include reading/writing files (`fs.createReadStream`, `fs.createWriteStream`), HTTP requests/responses.

59. **Q: Explain the difference between `module.exports` and `exports`.**
    **A:** In Node's CommonJS module system:
    *   `module.exports`: This is the *actual object* that gets returned when you `require()` a module. By default, it's an empty object (`{}`). You can assign anything to it (an object, a function, a class, a value).
    *   `exports`: This is initially just a *reference* (a shortcut) to the default `module.exports` object. You can add properties to it (`exports.myFunction = ...`), and these will be available on the exported object *as long as you don't reassign `module.exports`*.
    *   **Key Point:** If you assign something completely new to `module.exports` (e.g., `module.exports = myFunction;`), the `exports` variable loses its connection and any properties added directly to `exports` will *not* be exported. It's generally safer and clearer to primarily use `module.exports`.

60. **Q: How can you handle uncaught exceptions in a Node.js application?**
    **A:** While `try...catch` handles synchronous errors and `.catch()`/`try...catch` with `async/await` handles asynchronous errors in promise chains, uncaught exceptions can still crash the application. You can listen for the `uncaughtException` event on the `process` object:
    ```javascript
    process.on('uncaughtException', (err) => {
      console.error('There was an uncaught error!', err);
      // Perform synchronous cleanup (e.g., logging)
      process.exit(1); // It's generally recommended to exit after an uncaught exception
    });
    ```
    It's crucial to understand that after an uncaught exception, the application might be in an inconsistent state, so attempting to resume normal operation is risky. Logging and exiting gracefully is often the best practice. A similar event `unhandledRejection` exists for promises that reject without a `.catch()` handler.

61. **Q: What is an ORM or ODM? Give an example.**
    **A:**
    *   **ORM (Object-Relational Mapper):** A technique/library that converts data between incompatible type systems in object-oriented programming languages (like JavaScript in Node.js) and relational databases (like PostgreSQL, MySQL using SQL). It allows you to interact with your database using object-oriented paradigms instead of writing raw SQL queries. Examples: Sequelize, TypeORM.
    *   **ODM (Object-Document Mapper):** Similar to ORM, but for NoSQL document databases (like MongoDB). It maps document data (e.g., BSON in MongoDB) to objects in your application code. Example: Mongoose.
    *   **Benefit:** They simplify database interactions, provide data validation, abstract away database differences, and can improve developer productivity.

62. **Q: Briefly explain what Cross-Site Scripting (XSS) is in the context of a Node.js backend.**
    **A:** XSS is a security vulnerability where an attacker injects malicious client-side scripts (usually JavaScript) into web pages viewed by other users. While the execution happens in the user's browser, the Node.js backend can be vulnerable if it:
    *   Takes user input and directly embeds it into an HTML response without proper sanitization or encoding.
    *   Stores user input in a database and later renders it unsanitized on a page.
    *   **Prevention (Backend Role):** The backend must treat all user input as untrusted. It should sanitize input and properly encode output that will be rendered as HTML to prevent injected scripts from executing. Using templating engines with automatic escaping or libraries dedicated to sanitization helps.

63. **Q: What is CORS (Cross-Origin Resource Sharing)? Why might you need to configure it in your Node.js/Express API?**
    **A:** CORS is a browser security feature that restricts web pages from making requests to a different domain (origin) than the one that served the web page. If your React frontend (e.g., running on `http://localhost:3000`) needs to fetch data from your Node.js API (e.g., running on `http://localhost:5000`), the browser will block the request by default due to the different origins. You need to configure CORS headers on the *server-side* (your Node.js API) to explicitly tell the browser which origins are allowed to access its resources. Libraries like `cors` for Express simplify this configuration.

64. **Q: Have you used any testing frameworks for Node.js (like Jest, Mocha)? What is the basic purpose of unit testing?**
    **A:** (Mentioning Jest or Mocha is good). Unit testing is a software testing method where individual units or components of the software (e.g., a single function or module) are tested in isolation to verify they work correctly. The purpose is to catch bugs early in development, ensure code quality, facilitate refactoring (tests verify functionality isn't broken), and provide documentation for how units are supposed to behave.

65. **Q: Name a few Express middleware functions (built-in or common third-party).**
    **A:**
    *   `express.json()`: Parses incoming requests with JSON payloads (populates `req.body`).
    *   `express.urlencoded()`: Parses incoming requests with URL-encoded payloads (form submissions).
    *   `express.static()`: Serves static files (like HTML, CSS, JS, images).
    *   `cors()` (from `cors` package): Enables Cross-Origin Resource Sharing.
    *   `morgan()` (from `morgan` package): HTTP request logger.
    *   Middleware for authentication (e.g., using Passport.js).
    *   Custom middleware for validation, error handling, etc.

**VII. React.js (Deeper Dive)**

66. **Q: What is the `useContext` Hook? How does it relate to the Context API?**
    **A:** `useContext` is a React Hook that allows functional components to subscribe to React context without introducing nesting (like traditional Context Consumers did). It accepts a context object (the value returned from `React.createContext`) and returns the current context value for that context. It makes consuming context values simpler and cleaner within functional components compared to the older Consumer component pattern.

67. **Q: When might you use the `useRef` Hook?**
    **A:** `useRef` returns a mutable ref object whose `.current` property is initialized to the passed argument (initialValue). It's useful for:
    *   **Accessing DOM nodes directly:** You can attach a ref to a DOM element in JSX (`<input ref={myInputRef} />`) and then use `myInputRef.current` to access the underlying DOM node (e.g., to focus an input field: `myInputRef.current.focus()`).
    *   **Storing mutable values that don't cause re-renders:** Unlike state, changing the `.current` property of a ref does *not* trigger a component re-render. This is useful for persisting values across renders without affecting the rendering cycle (e.g., storing interval IDs, previous state values).

68. **Q: Explain the concept of "lifting state up" in React.**
    **A:** When multiple components need to share or reflect the same changing data, the common practice is to move the shared state up to their closest common ancestor component. The ancestor then holds the state and passes it down to the relevant children via props. If children need to modify the state, the ancestor also passes down callback functions (via props) that the children can call to update the state in the ancestor. This maintains a single source of truth and unidirectional data flow.

69. **Q: What are different ways to style React components? (Mention at least two).**
    **A:**
    *   **Inline Styles:** Applying styles directly via the `style` prop using a JavaScript object with camelCased CSS properties (`<div style={{ color: 'blue', backgroundColor: 'lightgrey' }}>`). Good for dynamic styles, but can be verbose and lacks features like pseudo-selectors.
    *   **CSS Stylesheets:** Importing regular CSS files (`import './MyComponent.css';`) and using standard CSS classes (`<div className="my-class">`). Simple and familiar, but class names are global by default, potentially leading to conflicts.
    *   **CSS Modules:** Importing CSS files named like `MyComponent.module.css`. Class names defined in these files are locally scoped by default (e.g., `styles.myClass`), preventing naming collisions. `import styles from './MyComponent.module.css'; <div className={styles.myClass}>`
    *   **CSS-in-JS Libraries (e.g., Styled Components, Emotion):** Writing actual CSS code within your JavaScript files using tagged template literals or object styles. Offers component-level scoping, dynamic styling based on props, theming, and eliminates unused styles.

70. **Q: What is the difference between a Controlled and an Uncontrolled Component in React forms?**
    **A:**
    *   **Controlled Component:** (Covered before, good reinforcement) Form input's value is controlled by React state. Data flows from state to input (`value` prop) and back via `onChange` handlers updating the state. The component state is the single source of truth.
    *   **Uncontrolled Component:** Form input's value is handled by the DOM itself (like traditional HTML forms). You typically use a `ref` (`useRef` Hook) to access the input's current value directly from the DOM when needed (e.g., on form submission). Less code for simple cases, but harder to implement instant validation or conditional disabling/formatting of inputs.

71. **Q: What is React Testing Library? What is its philosophy?**
    **A:** React Testing Library (RTL) is a popular library for testing React components. Its core philosophy is to test components in a way that resembles how users interact with them. Instead of testing implementation details (like component state or instance methods), RTL encourages querying the DOM based on accessible attributes (text content, labels, roles) and simulating user events (clicks, typing). The goal is to write tests that are more resilient to refactoring and give more confidence that the component works for the end-user.

72. **Q: Briefly explain what `React.memo()` does.**
    **A:** `React.memo()` is a higher-order component (HOC) used for optimizing functional components. It memoizes the component, meaning React will skip re-rendering the component if its props have not changed. It performs a shallow comparison of the props. It's useful for preventing unnecessary re-renders of components that receive complex props or render frequently. (Similar concept to `PureComponent` for class components).

73. **Q: Have you heard of Redux or Zustand? Why might a project need a state management library?**
    **A:** (Awareness is key). Redux and Zustand are popular external state management libraries for React. While React's built-in `useState` and `useContext` are sufficient for many cases, a dedicated library might be needed in larger applications when:
    *   State needs to be shared across many components that are not closely related in the component tree (avoiding deep prop drilling).
    *   State logic becomes complex and needs to be managed centrally and predictably.
    *   You need advanced features like middleware for logging/async actions, time-travel debugging, or better state persistence.
    *   They enforce a more structured way to handle state updates.

74. **Q: How would you fetch data in a React functional component?**
    **A:** Typically using the `useEffect` Hook combined with the browser's `fetch` API or a library like `axios`.
    ```jsx
    import React, { useState, useEffect } from 'react';

    function MyComponent() {
      const [data, setData] = useState(null);
      const [loading, setLoading] = useState(true);
      const [error, setError] = useState(null);

      useEffect(() => {
        fetch('/api/data') // Or use axios.get('/api/data')
          .then(response => {
            if (!response.ok) {
              throw new Error('Network response was not ok');
            }
            return response.json();
          })
          .then(jsonData => {
            setData(jsonData);
            setLoading(false);
          })
          .catch(error => {
            setError(error);
            setLoading(false);
          });
      }, []); // Empty dependency array means fetch runs once on mount

      if (loading) return <p>Loading...</p>;
      if (error) return <p>Error: {error.message}</p>;
      // Render data...
    }
    ```
    Using `async/await` inside `useEffect` is also common (requires defining an async function inside the effect and calling it).

75. **Q: What is the purpose of the `key` prop when rendering sibling elements without a list (e.g., inside `React.Fragment`)?**
    **A:** While `key` is most known for lists, it can also be crucial when rendering sibling elements conditionally or when their order might change *without* being part of an array `map`. Assigning a stable `key` to such elements helps React differentiate between them and preserve their state or avoid unnecessary re-mounting when the surrounding structure changes. For example, swapping between two components based on a condition might require keys on those components to ensure state isn't accidentally shared or lost. Using `React.Fragment` with a key (`<React.Fragment key={item.id}>...`) is also sometimes necessary when grouping list items without adding an extra DOM node.

**VIII. General / Tooling / Git**

76. **Q: What are some basic Git commands you use frequently?**
    **A:** Common commands:
    *   `git clone <repository_url>`: Copy a remote repository locally.
    *   `git status`: Show the working tree status (changes).
    *   `git add <file>` or `git add .`: Stage changes for commit.
    *   `git commit -m "Your commit message"`: Save staged changes to the local repository history.
    *   `git push`: Upload local commits to the remote repository.
    *   `git pull`: Fetch changes from the remote repository and merge them into the current branch.
    *   `git branch`: List local branches.
    *   `git checkout <branch_name>` or `git switch <branch_name>`: Switch to a different branch.
    *   `git checkout -b <new_branch_name>` or `git switch -c <new_branch_name>`: Create and switch to a new branch.
    *   `git merge <branch_name>`: Merge changes from another branch into the current branch.
    *   `git log`: Show commit history.

77. **Q: What is the difference between HTTP and HTTPS?**
    **A:**
    *   **HTTP (HyperText Transfer Protocol):** The standard protocol for transferring files (like HTML, images) on the web. Data is sent in plain text, making it vulnerable to eavesdropping.
    *   **HTTPS (HyperText Transfer Protocol Secure):** An extension of HTTP that uses encryption (usually TLS/SSL) to secure the communication between the client and server. It ensures confidentiality (data is encrypted), integrity (data cannot be tampered with), and authentication (verifies the server's identity via certificates). Essential for sensitive data like logins and payments.

78. **Q: What does a `404 Not Found` HTTP status code mean? Can you name another common status code?**
    **A:**
    *   `404 Not Found`: The server could not find the requested resource (e.g., the URL path doesn't exist).
    *   **Other common codes:**
        *   `200 OK`: Request succeeded.
        *   `201 Created`: Request succeeded, and a new resource was created (often returned after a POST).
        *   `400 Bad Request`: Server couldn't understand the request due to invalid syntax.
        *   `401 Unauthorized`: Client must authenticate itself to get the requested response (needs login).
        *   `403 Forbidden`: Client does not have access rights to the content (authenticated but not permitted).
        *   `500 Internal Server Error`: A generic error message indicating something went wrong on the server.

79. **Q: What is the purpose of a `.gitignore` file?**
    **A:** The `.gitignore` file tells Git which files or directories it should intentionally ignore and *not* track. This is used to prevent committing files that shouldn't be in version control, such as:
    *   Dependency folders (`node_modules/`)
    *   Build output (`build/`, `dist/`)
    *   Log files (`*.log`)
    *   Operating system files (`.DS_Store`, `Thumbs.db`)
    *   Secret files or environment configuration (`.env` - though `.env.example` might be committed).

80. **Q: Imagine a simple To-Do list application. What components might you create in React? What API endpoints might you need in Node.js?**
    **A:** (Tests basic design thinking)
    *   **React Components:**
        *   `App`: Main application container.
        *   `TodoList`: Displays the list of tasks.
        *   `TodoItem`: Represents a single task item (display text, maybe a delete button, checkbox).
        *   `AddTodoForm`: Input field and button to add new tasks.
    *   **Node.js API Endpoints (RESTful):**
        *   `GET /api/todos`: Fetch all to-do items.
        *   `POST /api/todos`: Create a new to-do item (request body contains task details).
        *   `PUT /api/todos/:id` (or `PATCH`): Update an existing to-do item (e.g., mark as complete).
        *   `DELETE /api/todos/:id`: Delete a specific to-do item.

This extended list provides more depth and breadth for evaluating a fresher candidate's understanding of the Node.js and React ecosystem. Remember to ask follow-up questions based on their answers!
