# What is Node?

-   Learn about Node.js, a JavaScript runtime for building server-side or desktop applications

## JavaScript and Node.js

-   Javascript has existed since 1995 and has since taken over as the dominant language for web development
-   For much of its life, JavaScript was used mainly for client-side scripting inside `<script>` tags executing in web browsers
-   This limitation meant that developers were often working in many different languages and frameworks

    -   between the front-end (client-side) and backend (server-side) aspects of a web application

-   Although there were other projects to bring JavaScript to server-side applications, the functionality took off with the launch of Node.js in 2009
-   Node allows developers to write JavaScript code that runs directly in a computer process itself instead of in a browser
-   Node can, therefore, be used to write server-side applications with access to the operating system, file system

    -   and everything else required to build fully-functional applications

-   Node.js is written in C, C++, and JavaScript, and it is built on the **open-source V8 JavaScript engine** which also powers JS in browsers such as Google Chrome
-   As [V8](https://v8.dev/) supports new features in JavaScript, they are incorporated into Node

## Node-Specific Functionality

### Globals

-   Node provides access to several important global objects for use with Node program files
-   When writing a file that will run in a Node environment, these variables will be accessible in the global scope of your file
    -   `module` is an object referring to the functionality that will be exported from a file. In Node, each file is treated as a module.
    -   `require()` is a function used to import modules from other files or Node packages.
    -   `process` is an object referencing to the actual computer [process](<https://en.wikipedia.org/wiki/Process_(computing)>) running a Node program and allows for access to command-line arguments and much more.

### Modules

-   Node has a many built-in modules to aid in interactions with the command line, the computer file system, and the Internet
-   These include
    -   [HTTP](https://nodejs.org/dist/latest/docs/api/http.html) and [HTTPS](https://nodejs.org/dist/latest/docs/api/https.html) for creating web servers
    -   [File System](https://nodejs.org/dist/latest/docs/api/fs.html), [OS](https://nodejs.org/dist/latest/docs/api/os.html), and [Path](https://nodejs.org/dist/latest/docs/api/path.html) for interacting with the file system, operating system, and file/directory paths
-   You can view the full [docs](https://nodejs.org/dist/latest/docs/api/) to see more of Node’s built-in features

## Why Node?

-   Per the [Node.js homepage](https://nodejs.org/en/), Node “uses an event-driven, non-blocking I/O model”
-   In practice, this means that Node is built well to handle **asynchronous** JavaScript code to perform many asynchronous activities

    -   such as reading and writing to the file system, handling connections to database servers, or handling requests as a web server

-   To handle asynchronous code, Node uses a callback-based system
-   Node functions and methods that will implement some asynchronous activity take a callback function
-   This callback will be called whenever the asynchronous operation has resolved
-   By convention, the first argument of this callback is an error placeholder
-   If an error occurred in the asynchronous operation occurred (trying to read a non-existent file, for example)
    -   the error argument will be an Error object, but it will be `null` if no error occurs

```javascript
const fs = require("fs");

fs.readFile("./script.js", function (error, data) {
    // error is null if no error occurred, but an Error object if it did
    if (error) {
        throw error;
    }
    // the file data will be passed into the callback if no error was thrown
    console.log(data);
});
```

-   In this example, we are using Node’s built-in `fs` module to read a script.js file
-   The callback function is called after the file-reading operation is completed
-   If an error occurred, it will be passed in as `error` and thrown
-   If it doesn’t exist, the retrieved data from the file reading operation is logged to the console

## How to use Node

-   install node and use like python

## Node as a REPL

-   Node can also be used in a terminal window as a Read-Evaluate-Print-Loop, or REPL
-   This functionality allows you execute JavaScript commands from the command line

-   With Node installed, you can launch the REPL by running the node command in a terminal and pressing Enter/Return
-   You are now in an interactive JavaScript environment and can run any valid JavaScript code such as 4 + 5
-   After executing a command, Node will always print the result of that evaluation

```
$ node
> 4 + 5
9
> function nodeIsGreat() {
... console.log('Node is great!');
... }
undefined
> nodeIsGreat()
Node is great!
undefined
> .exit
$
```

-   In this example, the user launches node on line one with the `node` terminal command
-   On line 2 the user types `4 + 5` and evaluates with the return key
-   `9` prints to the output terminal

-   On line 4, the user opens a function declaration of `nodeIsGreat`
-   Because this function declaration takes multiple lines

    -   Node REPL will print `...` at the beginning of a line to show that it is still reading the user’s input statement and has not evaluated yet
    -   After the function declaration is closed on line 6, `undefined` prints to the output terminal, as the function declaration itself does not evaluate to any value
    -   When the function is invoked on line 8, `Node is great!` logs to the console, and `undefined` logs after, because `nodeIsGreat()` returns `undefined`

-   To exit the Node REPL, use the `.exit` command at any point and return to the system shell. Pressing `ctrl + c` twice will also exit

## Loading Existing Files

-   Node REPL can also load existing JS files
-   If we had the following code saved into script.js:

```javascript
var a = 'Node REPL is fun!';

We can use .load to load it into the REPL. .load takes a path argument, so to load script.js we would use .load ./script.js.

$ node
> .load ./script.js
var a = 'Node REPL is fun!';

> a
'Node REPL is fun!'
```

-   After the script file is loaded

    -   the variables are accessible in the REPL
    -   so when we evaluate the a variable, it’s value has been set by loading script.js
    -   and ‘Node REPL is fun!’ prints to the console

-   Try it out yourself by running node in a terminal or check out the REPL docs for more functionality
