
## Ternary Operator
- In the spirit of using short-hand syntax, we can use a ternary operator to simplify an `if...else` statement
- Take a look at the `if...else` statement example:
```javascript
let isNightTime = true;
 
if (isNightTime) {
  console.log('Turn on the lights!');
} else {
  console.log('Turn off the lights!');
}
```
- We can use a ternary operator to perform the same functionality:
```javascript
isNightTime ? console.log('Turn on the lights!') : console.log('Turn off the lights!');
```
- In the example above:
    - The condition, `isNightTime`, is provided before the `?`
    - Two expressions follow the `?` and are separated by a colon `:`
    - If the condition evaluates to `true`, the first expression executes.
    - If the condition evaluates to `false`, the second expression executes.
- Like `if...else` statements, ternary operators can be used for conditions which evaluate to `true` or `false`

## variables
- `var` , `let` , `const`

## Function Declarations
-  In JavaScript, there are __many ways__ to create a function
- One way to create a function is by using a function declaration
- Just like how a variable declaration binds a value to a variable name, a function declaration binds a function to a name, or an identifier
- Take a look at the anatomy of a function declaration below:

![Diagram showing the syntax of a function declaration](https://content.codecademy.com/courses/learn-javascript-functions/Diagram/declaration.svg)
  
- A function declaration consists of:
    - The `function` keyword
    - The name of the function, or its identifier, followed by parentheses
    - A function body, or the block of statements required to perform a specific task, enclosed in the function’s curly brackets, `{ }`
- A function declaration is a function that is bound to an identifier, or name
- In the next exercise we’ll go over how to run the code inside the function body
- We should also be aware of the hoisting feature in JavaScript which allows access to function declarations before they’re defined

- Take a look at example of hoisting:
```javascript
console.log(greetWorld()); // Output: Hello, World!
 
function greetWorld() {
  console.log('Hello, World!');
}
```
- Notice how hoisting allowed `greetWorld()` to be called before the `greetWorld()` function was defined!
- Since hoisting isn’t considered good practice, we simply want you to be aware of this feature

## Helper Functions
- We can also use the return value of a function inside another function
- These functions being called within another function are often referred to as helper functions
- Since each function is carrying out a specific task, it makes our code easier to read and debug if necessary

- If we wanted to define a function that converts the temperature from Celsius to Fahrenheit, we could write two functions like:
```javascript
function multiplyByNineFifths(number) {
  return number * (9/5);
};
 
function getFahrenheit(celsius) {
  return multiplyByNineFifths(celsius) + 32;
};
 
getFahrenheit(15); // Returns 59
```
- In the example above:
    - getFahrenheit() is called and 15 is passed as an argument
    - The code block inside of getFahrenheit() calls multiplyByNineFifths() and passes 15 as an argument
    - multiplyByNineFifths() takes the argument of 15 for the number parameter
    - The code block inside of multiplyByNineFifths() function multiplies 15 by (9/5), which evaluates to 27
    - 27 is returned back to the function call in getFahrenheit()
    - getFahrenheit() continues to execute. It adds 32 to 27, which evaluates to 59
    - Finally, 59 is returned back to the function call getFahrenheit(15)

- We can use functions to section off small bits of logic or tasks, then use them when we need to
- Writing helper functions can help take large and difficult tasks and break them into smaller and more manageable tasks

## Function Expressions
- Another way to define a function is to use a function expression
- To define a function inside an expression, we can use the `function` keyword
- In a function expression, the function name is usually omitted
- A function with no name is called an __anonymous function__
- A function expression is often stored in a variable in order to refer to it

- Consider the following function expression:

![defining a function expression](https://content.codecademy.com/courses/learn-javascript-functions/Diagram/expression.svg)

- To declare a function expression:
    - Declare a variable to make the variable’s name be the name, or identifier, of your function
    - Since the release of ES6, it is common practice to use `const` as the keyword to declare the variable
    - Assign as that variable’s value an anonymous function created by using the `function` keyword followed by a set of parentheses with possible parameters
    - Then a set of curly braces that contain the function body
- To invoke a function expression, write the name of the variable
    - in which the function is stored followed by parentheses enclosing any arguments being passed into the function
```javascript
variableName(argument1, argument2)
```
- Unlike function declarations, function expressions are not hoisted so they cannot be called before they are defined

## Arrow Functions
- ES6 introduced arrow function syntax, a shorter way to write functions by using the special “fat arrow” `() =>` notation

- Arrow functions remove the need to type out the keyword `function` every time you need to create a function
- Instead, you first include the parameters inside the `( )` and then add an arrow `=>` that points to the function body surrounded in `{ }` like this:
```javascript
const rectangleArea = (width, height) => {
  let area = width * height;
  return area;
};
```
- It’s important to be familiar with the multiple ways of writing functions because you will come across each of these when reading other JavaScript code

## Concise Body Arrow Functions
- JavaScript also provides several ways to refactor arrow function syntax
- The most condensed form of the function is known as concise body
- We’ll explore a few of these techniques below:
    1. Functions that take only a single parameter do not need that parameter to be enclosed in parentheses
        - However, if a function takes zero or multiple parameters, parentheses are required
    - ![showcasing how arrow functions parameters differ for different amounts of parameters](https://content.codecademy.com/courses/learn-javascript-functions/Diagram/parameters.svg)

    2. A function body composed of a single-line block does not need curly braces
        - Without the curly braces, whatever that line evaluates will be automatically returned
        - The contents of the block should immediately follow the arrow `=>` and the `return` keyword can be removed
        - This is referred to as implicit return
    - ![comparing single line and multiline arrow functions](https://content.codecademy.com/courses/learn-javascript-functions/Diagram/return.svg)

- So if we have a function:
```javascript
const squareNum = (num) => {
  return num * num;
};
```
- We can refactor the function to:
```javascript
const squareNum = num => num * num;
```
- Notice the following changes:
    - The parentheses around `num` have been removed, since it has a single parameter.
    - The curly braces `{ }` have been removed since the function consists of a single-line block.
    - The `return` keyword has been removed since the function consists of a single-line block.

