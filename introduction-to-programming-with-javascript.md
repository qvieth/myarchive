# JavaScript: All the Cool Kids Are Doing It
- https://developer.mozilla.org/en-US/docs/Web/JavaScript
- Why is JavaScript so popular? What can you do with it?
- When the Internet boomed in the 1990s, technology companies battled to build the most powerful and efficient web browser on the market
- This sparked the first “browser war,” between Microsoft (Internet Explorer) and NetScape (NetScape Navigator) to gain dominance in the usage share of web browsers

- Netscape needed a lightweight scripting language for easier programming which ultimately made web development more accessible
    - unlike other languages that required deeper training
- In 1995, a NetScape employee, Brendan Eich, was given ten days to help build the company a lightweight scripting language
- As a result, Eich built Mocha, which was later renamed JavaScript
- The moral of the story – JavaScript was never intended to become the standard language for the web!
    - However, as NetScape won the browser war, the popularity of JavaScript grew
- More and more sites began using JavaScript, and those that didn’t eventually had to as most developers used JavaScript to make websites

- JavaScript is now an essential web technology that’s supported by major web browsers
    - The language is crucial for anyone who wants to become a web developer
    - Many experts agree that JavaScript will continue to grow as an indispensable language for web development

## JavaScript on the Web
- JavaScript, also called JS, is a flexible and powerful language that is implemented consistently by various web browsers, making it the language for web development
- JavaScript, HTML, and CSS are the core components of web technology
- While HTML is responsible for structure and CSS is responsible for style, JavaScript provides interactivity to web pages in the browser

## Popularity of JavaScript
- At this point, you may be wondering:
    - how is it that a language written in 10 days by one guy became mass-adopted by the world wide web?
- In short, JavaScript became a hit because it turned web browsers into application platforms. Here’s how:
    - JavaScript can be used in both the front-end and back-end of web development
    - JavaScript is standardized so it’s frequently updated with new versions
    - JavaScript integrates easily with HTML and CSS
    - JavaScript allows websites to have interactivity like scroll transitions and object movement
        - Modern browsers still compete to process JavaScript the fastest for the best user experiences
        - Chrome, the most used Internet browser in 2017, has been so successful because of its ability to process JavaScript quickly
    - JavaScript offers a wide range of frameworks and libraries that help developers create complex applications with low overhead
        - Programmers can import libraries and frameworks in their code to augment their application’s functionality

## JavaScript for Servers
- In the early 2000s, big platforms like Facebook and Google began using JavaScript in their back-end server logic to process and respond to front-end requests
- JavaScript helped businesses scale since engineers who knew JavaScript could apply those skills in a back-end context

- JavaScript used for servers, also known as server-side JavaScript, gained popularity because it allowed for scalability
- In the server, JavaScript can be integrated with other languages to communicate with databases

- Node.JS, or Node, is one of the most popular versions of server-side JavaScript
- Node has been used to write large platforms for NASA, eBay and many others
- Since Javascript can execute programs out of sequential order, Node can be used to create scalable web applications, messaging platforms, and multiplayer games
- This is why Google Cloud and Amazon Web Service depend on Node for some of their services

## What Else Can JavaScript Do?
- Beyond the web, JavaScript has a large presence amongst cross-platform applications
- We use some popular standalone desktop apps like Slack, GitHub, Skype, and Tidal
- These applications are developed with the JavaScript framework called Electron.js
- Electron is excellent for making desktop applications that need to work across different devices regardless of operating system

- In addition, JavaScript has the potential of expanding into other innovative technologies such as virtual reality and gaming
- JavaScript can be used for animating, rendering and scaling
- JavaScript even has contributed to the internet of things, the technology that makes simple objects, like your fridge, smarter
- Everyday devices can become interactive and collect data using JavaScript libraries

## Conclusion
- When diving into either programming or web development, JavaScript is an excellent language to learn
- The capabilities of JavaScript allow you to use it in many different fields
- Mastering what is known as “vanilla” or plain JavaScript will help you to tackle more complicated frameworks and libraries to make you a competitive developer
- Take some of our Codecademy JavaScript courses to become the JavaScript rockstar companies are looking for!

# JavaScript Versions: ES6 and Before
- You might have seen the term “ES6” or “Javascript ES6” and wondered what it actually means

- First, let’s bring in some history
    - JavaScript was introduced in 1995 by the company Netscape Communications as a scripting language for web designers and programmers to interact with web pages
    - The next year, Netscape submitted JavaScript to a standards developing organization
    - called Ecma International to create standards for a scripting language (a type of programming language)
    - In 1997, Ecma International released __ECMA-262__ which sets __standards__ for the first version of a scripting language called ECMAScript, shortened to ES

- These new ECMAScript standards provided rules for the architecture of JavaScript features
- As new programming paradigms emerged and developers sought new features
- newer versions of ECMAScript provided a basis for a consistency between new and old JavaScript versions

- To fully distinguish the difference between JavaScript and ECMAScript:
    - if you want to create an app or program you can use JavaScript 
    - if you want to create a new scripting language you can follow the guidelines in ECMAScript
    - So, when you see ES6 or JavaScript ES6
        - it means that that version of JavaScript is following the specifications in the sixth edition of ECMAScript!
        - You might also see ES2015 instead of ES6, but both terminologies are referring to the same 6th edition of ECMAScript that was released in 2015
    - Take a look at the timeline below to see how JavaScript has evolved over the years:
    - ![js timeline](https://content.codecademy.com/courses/javascript-article-assets/javascript_timeline.svg)

- Now, you may be asking, what makes an update in 2015 still relevant today when there are more recent updates like ES7 and ES8?
- Well, despite the release of newer versions, ES6 is actually the biggest update made to ECMAScript since the first edition released in 1997!
- Some developers even refer to ES6 as “Modern JavaScript” because of all the major additions
- There were so many great features added to help JavaScript developers that include:
    - new keywords like let and const to declare variables,
    - new function syntax using Arrow functions,
    - creation of Classes,
    - parameters with default values,
    - promises for asynchronous actions,
    - and many more!

- Up-to-date browsers now support most of the ES6 features which allow developers to take advantage of these new additions
- ES6 ultimately allows programmers to save time and write more concise code
- Take for example pre-ES6 syntax for function expressions:
```
var greeting = function() {
  console.log('Hello World!');  
};
```
- With ES6 arrow functions, we can transform the expression above into:
```
const greeting = () => console.log('Hello World'); 
```
- However, arrow functions are not just simply syntactical re-writes
- As with other ES6 features, there are other underlying benefits and tradeoffs to consider
- Nonetheless, there has been a strong adoption of ES6 in the development community
- Benefits such as new ES6 syntax, makes it easier to utilize a popular programming paradigm, Object Oriented Programming (OOP)
- This change allowed for developers of other languages who are used to OOP can now transition into learning and using JavaScript
- Another reason for the popularity of ES6 is correlated with the usage of ES6 in popular frameworks like React
- So, if you want to learn the newest tools and frameworks, you will have to pick up ES6 along the way

- This being said, we shouldn’t disregard legacy code, i.e. older versions of JavaScript
- In fact, there are still many projects that are built and maintained with legacy code!
- If you want the ability and freedom to work on any sort of JavaScript project
    - you should familiarize yourself with pre-ES6 and ES6 JavaScript syntax
- But don’t worry, we cover both pre-ES6 and ES6 in our JavaScript course
- Check it out to become a rockstar at JavaScript basics and learn fundamental programming skills!
