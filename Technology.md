# Technology

-   [science](science) of craft - 'know how' knowledge of how to make things that would otherwise not exist

## top

-   [ ] [programming paradigm](https://en.wikipedia.org/wiki/Programming_paradigm)
-   [ ] programming : types are object, functions are morphisms | a -> b -> b | arrow : f = a -> b, id_b = b -> b | id_b after f
-   [ ] composition of functions is associative
-   Think of async/await as an **API for asynchronous programming**
-   [Is it possible to append to innerHTML without destroying descendants' event listeners?](https://stackoverflow.com/questions/595808/is-it-possible-to-append-to-innerhtml-without-destroying-descendants-event-list)
-   event loop: when A happens, do B
-   async/await is the best way to express asynchronous I/O in combination with using an event loop
-   7 primitive types of data : string, number, array, set, true, false, null
-   loop : thik of mathematical induction(sequences) with pre and post conditions
    -   a_n = frac{-1^n}{n+1} for every interger n \geq 0
    -   -> BIG IDEA : THINK OF THE FORMULA FIRST, NOT THE FOR FIRST
-   a third way to define a sequence is to use recursion, as was done in example 5.3.3, 5.4.2, 5.4.3
-   Defining sequences recursively is similar to proving theorems by mathematical induction - discrete math book page 325
-   Recursive Thinking : The process of solving large problems by breaking them down into smaller, simpler problems that have identical forms.
-   https://www.youtube.com/watch?v=g-PaL3GKL6U : good video - think about what not how, post condition not recursive part

-   CALLBACK FUNCTION AKA HANDLER FUNCTION

-   JS promises
-   callback, arrow functions - middleware function(1,2,next) vs route handler callback

-   For sequential circuits one cannot predict the output corresponding to a particular input, unless one knows the state the circuit was in

-   closure of a function : a variable act like arugment but cannot be passed as parameter
-   A finite-state automaton A **consists of five objects**:

    1. A finite **set** I, called the **input** alphabet, of input symbols
    2. A finite **set** S of **states** the automaton can assume
    3. A designated state s 0 called the **initial state**
    4. A designated set of states called the set of **accepting states**
    5. A next-state **function** N : S X I -> S that associates a “next-state” to each
        - ordered pair consisting of a “current state” and a “current input”

    -   https://www.youtube.com/watch?v=SuoDmiJ6zLQ : insight for finite state automata and regular expression
    -   definition page 843

    *   all regular expression can be represented as **state transition diagram**
    *   https://people.cs.clemson.edu/~goddard/texts/theoryOfComputation/5.pdf

    -   Each piece of input to a finite-state automaton leads to a change in the state of the automaton

-   [10 tips tricks python - corey schafer](https://www.youtube.com/watch?v=C-gEQdGVXbk)
-   [corey schafer pandas](corey-schafer-pandas)
-   https://www.youtube.com/watch?v=Xcet6msf3eE : 10:23
-   build a better spotify with react - wds : https://www.youtube.com/watch?v=Xcet6msf3eE
-   https://www.youtube.com/watch?v=9CEW3Tmx2tg : must use websites & tools for web developers
-   https://www.youtube.com/watch?v=xxpc-HPKN28 statistics freecodecamp
-   node.js mvc | django mvt
-   https://www.youtube.com/watch?v=8kDs8QkFI2Y : watch this
-   https://www.youtube.com/watch?v=2bW3HuaAUcY : mysql in 10 minutes
    -   **RELATIONAL ALGEBRA** ALLOW US TO RETRIEVE DATA EFFICIENTLY
-   https://www.youtube.com/watch?v=cWMCHbxMiMI : mysql syntax in 20 minutes -> good video
    -   procedural : how
    -   object oriented programming : python
    -   declarative : SQL : concentrate on what result you want to obtain, not how your data can be obtain
    -   functional : JS
    *   sql command types :
        -   DD - DM - DC - TC
        -   data definition - data manipulation - data control(grant,revoke) - transaction control(commit,rollback)
-   https://www.youtube.com/watch?v=JT80XhYJdBw : python django 2 project in 8 hours

-   https://en.wikibooks.org/wiki/Discrete_Mathematics/Recursion
    -   recursion : algebra -> sequence | discrete math -> induction and recursion

*   i should make a cheat sheet for programming by all languages
    -   expression vs statement : https://en.wikipedia.org/wiki/Expression_(computer_science)
        -   Expressions PRODUCE AT LEAST ONE VALUE
        -   expressions \subset statements
        -   statement - single statement - compound statement
        -   Classes allow programmers to implement abstract data types

-   https://www.youtube.com/watch?v=nykOeWgQcHM&list=PLUl4u3cNGP63WbdFxL8giv4yhgdMGaZNA : introduction to computer science and programming in python

    -   chapter 1 : what is computation
        -   fixed program computer - stored program computer
        -   computer architecture : cpu - memory - i/o
        -   turing showed that you can compute anything using 6 primitives : move left, move right, read, write, scan and do nothing
        -   modern programming langueges have more convinient set of primitives
        -   can abstract methods to create primitives
        -   python rules:
            1. everything is an object
            2. every object has an type
            3. object can be converted from one type to another
            4. expressions : combination of objects and operators - has a value - which has a type
                - syntax for expression : <object> <operator> <object>
    -   chapter 2 : branching and interation
        -   control flow - branching - <condition> has a True of False value
            -   if <condition>:
                -   <expression>
                -   ...
            -   else :
                -   <expression>
                -   ...
    -   chapter 3 : string mainpulation, guess and check , approximations, bisection
    -   chapter 4 : decomposition, abstraction and functions
        -   decomposition idea : different devices work together to achieve an end goal
        -   reuseable pieces/chunks of code, called functions
        -   functions are not run in a program until they are called or invoked
        -   functions' characteristics : name(parameter) - scope - docstring + body - return something - function definition and function call
    -   chapter 6 : \*\*recursion and dictionaries
    -   chapter 7 : testing, debuggin, exceptions and assertions
        -   test case - input - output specification
        -   3 kinds :
            -   unit testing
            -   regression testing
            -   inegration testing
            -   black box testing
            -   glass box testing

-   https://www.youtube.com/watch?v=eWTuFoBYiwg : The difference between an expression and a statement in JavaScript
    -   interpolation
-   Handler, an asynchronous callback (computer programming) subroutine in computing

*   how to import in python
*   comeback - book : a common sense guide to data structures and algorithms -> node-based data structures
*   book : a common sense guide to data structures and algorithms
    -   big o has to be the same category : O(N^2) and O(N) is different category - O(N) and O(100N) is same category
    -   while Big O is perfect for contrasting algorithms that fall under different classifications of Big O
    -   when two algorithms fall under the same classification, further analysis is required to determine which algorithm is faster
    *   [ ] NODE-BASED DATA STRUCTURES - LINKED LIST - THE FOUNDATION
*   isn't that measuring time complexity is :
    -   based on RSID operations of array - the foundation block which other data structure based on
*   isn't that measuring time complexity is :
    -   based on RSID operations of array - the foundation block which other data structure based on
    -   index take 1 step
    -   search N step
    -   insert N + 1 step (move entire array to the right then insert the first)
    -   delete N step (delte the first value then move the entire array to the left)
    -   SETS: HOW A SINGLE RULE CAN AFFECT EFFICIENCY
    -   An algorithm is simply a SET of instructions
    -   where we had two different approaches for printing out even numbers
        -   one algorithm had twice as many steps as the other
    -   But here’s the trade-off: by using an ordered array, you have somewhat slower insertion, but much faster search
    -   think of BIG O of how the CHANGE is as data increase
*   https://www.youtube.com/watch?v=bFvjE4ZRtSE : webdevsimplified html elements series
    -   head
        -   title
    -   body
        -   header
            -   h1 || nav
        -   section
            -   h2
        -   footer
            -   h3
    -   button, anchor, hr, br, div, span, &entities(name,#;)
    -   anchor>img (img is child of anchor(target="\_blank") - open in new tab)

-   https://www.youtube.com/watch?v=l1mER1bV0N0 : css selector
    -   class selector(50%)
    -   pseudo selector(20%)
        -   pseudo classes :hover :focus :last-of-type() :not()
        -   pseudo element ::before ::after -> require content property
    -   attribute selectors (5%): data
-   git awesome-react-component -> insight, focus on how to combine already made components/hooks to create websites

*   https://blog.risingstack.com/the-history-of-react-js-on-a-timeline/ : react history -> google for similar topics of other technology
*   google for ...(react,expressjs) concepts -> make a graph for it
*   [react](react) concepts <- googled
    -   https://owlypixel.com/learning-react-main-concepts/#components : good cheatsheet
    -   https://daveceddia.com/what-react-does/ : what react do and doesn't - react rerender when you trigger it
    -   https://daveceddia.com/react-getting-started-tutorial/
    -   https://us.hidester.com/proxy.php?u=eJwBVgCp%2F3M6Nzg6Ivh7Uph4wHFImXiNpiysB5KoPVDmaA2LUnc%2B92nOo0P63cJoObjlWeI8SsP9JHBVtnxcExUrHc3%2Fk3U39FXPheWEgNe7i%2FFv6dkhP8zkTSI7CB8rew%3D%3D&b=7
    -   https://www.youtube.com/watch?v=O6P86uwfdR0 : usestate() - webdevsimplified
    -   https://www.youtube.com/watch?v=hQAHSlTtcmY : react in 30 min - webdevsimplified
    -   https://daveceddia.com/react-getting-started-tutorial/ : 38 page react tutorial - this turotial is EXTREMELY GOOD
        -   <div key:"value"
              - key:"value" is an object
              - => const hi = ({key}) => return ``<div>`` hi {key} ```</div>``
              - props is object
              - comback

-   create binary search tree by making a root and insert key into it
-   page 698 - matrix multiplication - comeback
-   treatise : try pronouce it
-   a + (a+d) + (a+2d)... + (a+(n-1)d) + (a + nd) : arithmetic sequence
-   time and space complexity
    -   time complexity : how many steps
    -   space complexity : how many **extra memory**
        -   some algorithm require the computer to allocate extra memory in the computer
        -   selection sort is in-place algorithm : no auxilary memory
        -   worst case scenario will prevent system crash
        -   have to balance space and time/ make sacrifice which one to choose
-   sort : selection | insertion | odd-even | bubble | cocktail-shaker | quicksort | bitonic | heap | cycle
    -   merge sort : recurive sorting
    -   bucket sort : counting sort
    -   comb sort : exchange sort
    -   sorting algorithm
        -   -> speed
        -   -> memory required
-   graphs : 6 different types - look at 3 most popular
    -   directed vs undirected | cyclic vs acyclic | weighting graphs | graph combinations
    -   tree vs graph : trees have a specific starting point
    -   notationally : nodes{1,2,3,4} edges{(1,2),(3,4),(3,1)} | edges - adjacent
    -   undirected graph : direction you traverse isn't important - indicated by lack of arrows
    -   directed graph : has arrows
    -   cyclic graph : one which contains a path from at least one node back to itself
        -   all undirected graphs are cyclical
    -   acyclic graph : one which contains no path from any node which leads back to itself
    -   weighted graphs :
        -   associated a numerical value with each edge(cost)
        -   each weight represents some property of the information you're trying to convey
    -   cyclical undirected - cyclical directed - acyclical directed
    -   **undirected cyclical graphs with weighted edges** can be used through dijkstra's shortest path algorithm
        -   compiles a **list** of the shortest possible paths from that source vertex to all other nodes within the graph
    -   unweighted cyclical graphs are used in the follower system of majority of social media websites
-   heaps : https://www.youtube.com/watch?v=PEhPs4ZVvaw
    -   min heap - max heap
    *   heaps are most commonly used in the implementation of Heapsort
        -   [ ] a sorting algorithm which takes in a list of elements, builds them into a min, or max heap, and then removes the root Node continuously to make a sorted list
    *   **priority queues** - an advanced data structure which your computer uses to designate tasks and assign computer power based on how urgent the matter is
        -   think of a line at a hospital || you wouldn't want your computer to update an application before it finishes rendering a video otherwise your progress will be lost
        -   priority queues take care of all the task scheduling done by your computer and the heap data structure used as the backbone for it
-   tries - tree based on alphabet - autosuggestion/spell check - flagging(end of word)
-   trees :
    -   trees store data hierarchically as opposed to linearly
    -   an abstract data structure which contains a series of **linked nodes** connected together to form a hierarchical representation of information
    -   like a **linkedlist** where each has the option of pointing towards **multiple nodes**
    -   node|vertices - edges
    -   height - number of edges on the longest possible path down towards a leaf - property of the tree
    -   depth - number of edges required to get from that node to the root node - property of the node
    -   binary search tree BST - simple variation on the standard tree which has 3 restrictions on it to help organize the data:
        -   a node can have at most 2 children
        -   \forall parent, left child <, right child >
        -   no 2 nodes can contain the same value
    -   BST advantages :
        -   search O(logn)
        -   makes them extremely popular for storing large quantities of data that need to be easily searchable
-   dictionary : key:value | 1 key, 1 value | hashtable - hashfunction | asid 1111
-   each nullpointerexception has a reference part - can be useful

*   linked list : **sequential access** | node = data + pointer(takes computer to the next node in the list)
    -   how to define linked list in a specific language
    -   used in the backing of other data structures, we can use linkedlist to make stacks, queues

-   queue
-   stack : undo/redo | back-paging | recursiong | LIFO ASID nn11
-   random access data structures - independent elements - O(1) accessing - array and arraylist
-   sequential(limited) access data structures - dependent elements - stack, queue and linked lists

*   arraylist - why not always use arraylists - array is quite trash comparing to arraylists
    -   array list size is dynamic

-   array | asid 11nn
    -   parralel arrays - good way to have multiplt bits of information about one entity to be stored in a way that is easily accessible
    -   size cannot be changed
    -   2 ways for creating and filling arrays : populate at the create time, populate later
    -   index : 2d array is mostly the same as with 1d array, just need 1 more indexes
    -   Acessing O(1) | Searching O(n) | Inserting O(n) | Deleting O(n)
    -   searching through array is O(n) because we must use linear search
-   data structure :
    -   3 attributes : name - type - size
-   we want a quantifiable way to measure how efficient certain data structures are at different tasks we might as of it
    -   always think of binary search at example for bigO - what is N, steps
    -   searching - modifying - accessing
    -   big O(always talk of worst case)- time complexity equation - O(n!) hasn't been mentioned
    -   by measuring how efficiently a data structure can do these 4 things
        -   we can create a "report card"
    -   the most common functions you might want from a data structure :
        -   ASID : access, search, insert, delete
-   https://www.youtube.com/watch?v=3b7NiTO8U4g : data structure-nullpointerexception
    -   reference list at the end of video
    -   efficiency - 10 most used data structures
    -   array and array lists : the basics
    -   stacks and queues : backbone for recursive processses
    -   linkedlists and dictionaries : specialized data structures
    -   trees and tries : used for **word processing**
    -   heaps and graphs
-   string math
-   how to debug -> git, read line error, stack overflow, commenting
-   coding bat - coderbyte - hackerrank - ap computer science principle
-   https://www.youtube.com/channel/UCmWDlvMYYEbW42B8JyxFBcA : null pointer channel
-   https://www.freecodecamp.org/news/i-dont-understand-graph-theory-1c96572a1401/ :
    -   Use arrays if you need fast element access, use lists if you need fast element insertion/deletion,
    -   how to represent lists...
-   [proof](https://en.wikipedia.org/wiki/Mathematical_proof) direct proof(deduction), proof by induction vs proof by contradiction, proof by contrapositive,...
-   deep understanding : detailed explanations vs succinct definitions
-   A graph is a set of vertices V and a set of edges E
    -   comprising an **ordered pair** G=(V, E)
    -   ex :G = V{0,1,2,3} \cap E{01,02,03,12,13,23}
-   time complexity, storage methods
-   measureing efficiency of ASID with bigO - time complexity **equations**
    -   accessing - searching - iserting - deleting
    -   6 most common time complexity equations
        -   O(1)
        -   O(logn)
        -   O(n)
        -   O(nlogn)
        -   O(n^2)
        -   O(2^n)
        -   the more you use the more inefficient it becomes
-   we always use the worst case scenario when judgin these data structure
-   prolem -> contentualize -> contextualize -> reformulate problem -> find relevant categorical requirements -> solve problem
-   [OOJS - inheritance - admin - user](https://www.youtube.com/watch?v=_cgBvtYT3fQ)
    -   chapter 9-10-11 : prototype property
    -   filter - array
    -   inheritence - extends - new class inherit from old class - superset subset
    -   methods chain - `return this`
-   In our experience, thinking about how the UI should look at any given moment, rather than how to change it over time, eliminates a whole class of bugs
-   `<div id="root"></div>` : we call this root DOM node because everything inside it will be managed by React DOM
-   study main concepts before doing actual project
-   before study react :
    -   array methods like forEach() & map()
    -   fetch api & making http requests
    -   when using react, think of your UI as bunch of separate components
    *   component created by functions or classes -> return JSX
        -   component can also take in "props" in components = attributes
    -   components can have 'state' - **object** that determines how a component **renders and behaves**
    -   "app" or "global" state refers to state that is available to the entire UI, not just a single component
    -   when you have tons of state
        -   context apis
        -   3rd party state management : redux
    -   prior to react 16.8, we had to use class based components to use state
        -   now we can use functional components with hooks
        -   react hooks are functions that let us **hook** into
            -   the React state and lifecycle features
            -   from function components
-   EDX - Node
-   [graph search in 100s](https://www.youtube.com/watch?v=cWNEl4HE2OE)
-   [fireship](fireship)
-   build a chatbot app using nodejs, dialogflow and cloud functions
-   What types of projects run best on a Backend as a Service? -> do more research about these types of cloud computing
    -   Real-time applications (chat, messaging apps)
    -   Transportation apps (similar to Uber)
    -   Social-network type apps
    -   Ecommerce apps
    -   Music or Video streaming apps
    -   Games
-   [nodejs fireship](https://www.youtube.com/watch?v=ENrzD9HAZK4)
-   [firebase](https://www.youtube.com/watch?v=q5J5ho7YUhA)
    -   the first we want to do here is grabing html elements we want to interact with which we can do by calling `document.getElementById()`
    -   this code is obviously pretty ugly, it's the main reason why people choose a framework like React or Vue
    -   even if you use a framework, it's important to understand how these low level API works
    -   awesome tool for quickly development
-   API clients (aka REST Clients)
-   blockchain : protocol
-   [websocket with socket.io](https://www.youtube.com/watch?v=1BfCnjr_Vjg) : good video, has a small chat app project
-   https://github.com/getify/You-Dont-Know-JS

-   [ibm four architecture choices for app development in the digital age](https://www.ibm.com/cloud/blog/four-architecture-choices-for-application-development)

```framework
1. learn just enough
2. do a project/experiment
3. iterate
4. accountability - tell people what you will do and try to keep promise
```

-   ARCHITECTURE
-   [ ] [modern web architecture explained](https://www.youtube.com/watch?v=YGGBahexXYI) : talks to **3rd party backends** - payment,validation,analytics,maps,...
-   [ ] node is ideal for data, I/O intensive and realtime apps include lot of disk or network access, we can serve more clients without the need to throw more in hardware- that's why node apps are highly scalable
    -   [ ] do not use node for CPU-intensive apps like video encoding or image manipulation service
    -   [ ] node s
-   [ ] backend -> main purpose : any application or sets of applications connected to the internet who's main purpose is to serve client's requests
    -   [ ] the 2 most common **back-end processes** are web servers and databases
        -   [ ] web server : anything that responses to http request with some data
        -   [ ] database : can be used independently from web servers - dbs can use a lot of resources - connect with each other sockets - support many connection
    -   [ ] old backend model : reder html on back end and send to client
    -   [ ] new model : backend return only data
    -   [ ] front end : code **running** on browser of mobile
    -   [ ] background process and caching
-   [ ] rest handling resources and request easier
    -   [ ] restful URL
    -   [ ] rest is just a fancy way of saying that a server responds to CRUD request in a standard way
-   [ ] In the prior chapter we learned how to build mock HTTP services
    -   [ ] In this chapter(chapter 2) we'll build on those services to include real-time functionality with mock data
    -   [ ] Deploying production-worthy real-time APIs is an **architectural and operational challenge** in itself
    -   [ ] -> need **infrastructurally and architecturally** focused teams and roles
-   [ ]
-   [ ] handler : an async function (like event listener) -> that's why we have to close it in python(we don't want eventlistener to runforever)
-   [ ] Fastify works by dividing the service up into plugins
    -   [ ] A plugin is a module that exports a function
    -   [ ] The exported function is passed a fastify instance and options
    -   [ ] What we've created here is a route plugin (as opposed to a library plugin, which would go into the plugins folder)
-   [ ] origin : protocol + domain + port - CORS : cross-origin resource sharing: by default doesnot allow cross-domain requests
-   [ ] https://learning.edx.org/course/course-v1:LinuxFoundationX+LFW111x+1T2021/home
    -   [ ] how not to install node
-   [ ] eventloop = callstack -> ES6 job queue -> message queue
-   [ ] https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop
-   [ ] https://nodejs.dev/learn/the-nodejs-event-loop
-   [ ] Every time the event loop takes a full trip, we call it a tick
-   [ ] Message Queue is also where user-initiated events like - [ ] click or keyboard events - [ ] or fetch responses are queued before your code has the opportunity to react to them - [ ] Or also DOM events like onLoad
-   [ ] learn stream programming
-   [ ] https://nodejs.dev/learn/understanding-javascript-promises
    -   [ ] read Promise API
    -   [ ] pending state - (resolved state - rejected state) none of these 2 called in the execution path, promise remain in pending state
    -   [ ] promise - oop - initialize new
-   [ ] LEARN THE BEHAVIOR FIRST, SKIP HOW DOES IT WORK
-   [ ] read the stack trace/ understand call stack
-   [ ] JS common error
-   [ ] [code 4 du an html/css/js trong 2 tieng](https://www.youtube.com/watch?v=YtYcYRsODmI)
-   [ ] [vn - event looop trong javscript la gi](https://www.youtube.com/watch?v=64ASqMjj9_o)
-   [ ] wake up and keep learning express - read their documentation + mdn
-   [ ] [promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)
-   [ ] [anjana vakil - learning functional programming with javascript](https://www.youtube.com/watch?v=e-5obm1G_FY)
-   mori, immunable.js
-   logic = if else condition...
-   https://www.quora.com/How-many-different-programming-paradigms-are-there-and-what-are-they
-   John Colagioia : Why different paradigms? Because certain problems fit into different paradigms more easily
    -   Simulating physical things is an almost inherently object-oriented process
    -   Applying transformations to separate data sets is almost inherently functional
    -   Joining components is dataflow
-   paradigm : functional programming(everything is function) - procedural programming - oop(everything is object)
    -   pure function(take input, use that compute output)
    -   avoid side effects : return not console.log
    *   we need higher order function in order to avoid some of the tricks that we're used to using from other paradigms
    *   don't iterate(for, while go over lists)
    *   instead in functional style, we might
        -   use higher-order functions like map or reduce or filter
        -   which often take as an input not only the list that you want to do something to in some way
        -   but also a function that then you're going to apply to it
-   types of javascript error and their fix <- google this
-   [what the heck is the event loop anyway?](https://www.youtube.com/watch?v=8aGhZQkoFbQ)
    -   call stack = thread
-   [ ] https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop : comeback tomorrow
    -   [ ] The documentation is misleading since they console.log a message but it likely isn&#39;t a message in the queue. It&#39;s likely just a normal message like this comment is a message to you. They overloaded the term. In the section under &quot;adding messages&quot; they use this language: In web browsers, messages are added anytime an event occurs and there is an event listener attached to it. So, yes, the queue is only for event listeners and asynchronous code (i.e. setTimeout)
    -   Function calls form a stack of frames.
        -   When calling `bar`
            -   a first **frame** is created
                -   containing `bar`'s arguments and local variables
        -   When `bar` calls `foo`
            -   a second **frame** is created and pushed on top of the first one
                -   containing `foo`'s arguments and local variables
        -   When `foo` returns
            -   the top **frame** element is popped out of the stack (leaving only `bar`'s call frame)
        -   When `bar` returns, the stack is empty
-   callback : you can do it rightnow, but you would do it later
    -   think of call to dentist just to tell them call me back later for appointment

```MIDDLEWARE
A function that is invoked by the Express routing layer before the final request handler, and thus sits in the middle between a raw request and the final intended route. A few fine points of terminology around middleware:
    var foo = require('middleware') is called requiring or using a Node.js module. Then the statement var mw = foo() typically returns the middleware.
    app.use(mw) is called adding the middleware to the global processing stack.
    app.get('/foo', mw, function (req, res) { ... }) is called adding the middleware to the “GET /foo” processing stack.
```

```* A special mention for lodash/underscore and functional programming in general
First, don't use any for or while loops in your node program. It does not work with concurrent processes.
Example: For each file in Files, open it, then do X. Yeah good luck.
The correct way to do this is to _.map(Files, ... ) into either a) functions with a callback or b) promises and then use async.parallel/Promise.all respectively. Technically you could create a new array, for loop into it and then async.parallel/Promise.all on that, but if you do that a few times your code will look like !$%^$!.
The key idea here is to be able to treat "code i am going to run" as objects. _.map captures that semantics very well.
```

-   [o][better error handling with async/await ](https://dev.to/sobiodarlington/better-error-handling-with-async-await-2e5m)
    -   [ ] from callback hell to promises
    -   [x] The example below use promises to solve callback hell
        -   [x] by using multiple chained `.then` calls
        *   [x] instead of nesting callbacks
-   [ ] [You don't need promises in Python: just use async/await!](https://quentin.pradet.me/blog/you-dont-need-promises-in-python-just-use-asyncawait.html)
-   [ ] destructuring - powerful for data manipulation
-   [ ] [webdevsimplified - js array](https://www.youtube.com/watch?v=R8rmfD9Y5-c&list=PLZlA0Gpn_vH-0FlQnruw2rd1HuiYJHHkm)
    -   `.filter` `.map`
    -   high order function and array
-   [ ] error handling
    -   [ ] async - more elegant way to handle promises
    -   [ ] [webdevsimplified - js promises](https://www.youtube.com/watch?v=DHvZLI7Db8E)
        -   [ ] `.then` or `.catch`
        -   [ ] setTimeout is not the only form of asynchronous code in JS that's built in -> promises
        -   [ ] the concept of promises which is something that you see whenever you see .then or .catch coming after a function
        -   [ ] especially when you're doing a fetching for example is another great example of asynchronous code that you don't actually know how long it's going to take since you don't specify the timeout
        -   [ ] **WE SETTIMEOUT BECAUSE WE HYPOTHETICALLY WORKING WITH SERVER**
-   [ ] avoid callback hell => `new Promise(resolve, reject) => {}`
-   [ ] `getElementById()`
-   [ ] `querySelector()`
-   [ ] `addEventListener()`
-   [ ] traversy DOM 4 part - event object part 3 - last project
-   https://www.youtube.com/watch?v=PoRJizFvM7s
    -   callbacks-promise-async await: dom was already painted, resolve, output, promise.all, .then()
    -   sync call back, async call back
-   [JS arrow function](https://www.youtube.com/watch?v=h33Srr5J9nY) : great tutorial for named function, anon function vs arrow function, their this scope
-   responsive website :
    -   https://www.youtube.com/watch?v=M3qBpPw77qo
    -   https://www.youtube.com/watch?v=p0bGHP-PXD4
-   https://rapidapi.com/blog/types-of-apis/
-   management information systems
    -   system development or system analysis
    -   Basic analytical and problem solving skills for design, creation and testing of programs
    -   gathering requirements from a technical perspective and developing documentation of system specifications
    -   designing and implementing new methods, procedures, and systems (both automated and manual) to improve the processing and flow of information within the company.
    -   Gathers information from users for analysis of technical problem areas and prepares elementary feasibility studies
-
-   Emmet is Vim for web developing. XD
    P.S.: Since you are gonna do webdev
    try vim-surround
    vim-commentary
    and vim-easymotion for flash like workflow
    And also learn SASS(Tabbed version) from the get go
    instead of writing traditional CSS and thank me later. XD

-   css - reset - normalizer
-   2 project
    -   1 data science : back to datacamp finish the career track and get the project from it
    -   1 django - https://www.youtube.com/watch?v=6DI_7Zja8Zc&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=17
    -   look for job description on itviec, glints
-   comeback to datacamp, continue the reverse engineering
-   Nho lz Tai giang lai Mdn docs css
-   hoi ve cach dxc.technology hoat dong(cach business kiem tien, khach hang,...) cong nghe, viec lam
-   in-box knowledge and out-box knowledge : read in-box to relax, when feel focus learn out-box

-   middleware is just a function take in req, res, next and call next whenever it wants to move to the next form of the [middleware](middleware)
-   web security - sanitize data
-   They provide tools and libraries that simplify common web development tasks including :
    -   routing URLs to appropriate handlers
    -   interacting with databases
    -   supporting sessions and user authorization
    -   formatting output (e.g. HTML, JSON, XML)
    -   and improving security against web attacks
-   [serverside diagram](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Introduction)
-   [management information system](https://en.wikipedia.org/wiki/Management_information_system)

*   https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Thinking_before_coding : important, many insights
    -   When starting with a web project, many people focus on the technical side
        -   Of course you must be familiar with the technique of your craft, but what really matters is what you want to accomplish
        -   Yes, it seems obvious, but too many projects fail not from a lack of technical know-how, but from **lack of goals and vision**
        -   **A project should never starts with the technical side**

-   look back to look forward
-   optimize : time to learn something = time to do something
-   express :
    -   middleware functions are functions that have acces to the request and response object
    -   express has built in middleware but middleware also comes from 3rd party packages as well as custom middleware
    -   excute any code
    -   make changes to the request/response objects
    -   end response cycle
    -   call next middleware in the stack
-   javascript
    -   named function
    -   async = non-blocking i/o call
    -   high order array methods
    -   anonymous function
    -   arrow function
    -   ?
    -   destructuring assignment to assign variables from arrays
    -   rest operator
-   array index
-   realtime chat with user & room
    -   socketio
    -   use the javascript to insert into the DOM
    -   right now we just have a bunch of static stuff here, hard coded with html
    -   so the next thing i want to do is set up our server to handle SOCKET.IO
    -   so this is working really good
    -   of course you could add on to this
    -   intergreate mongoDB or somekind of SQL database or whatever
    -   and store the users and basically have them log in to join the chat
-   https://www.youtube.com/watch?v=GZvSYJDk-us

    -   apis : interface : abstract way to use something
    -   web apis
    -   that all browser must implement
    -   leverage apis to focus on the business problem at hand

-   [CCS](https://www.youtube.com/watch?v=1Rs2ND1ryYc) - which properties you use to describe this :
    [developer platform](developer-platform)
    [.NET](.NET)

-   theory of computation

## middle

1. [fundamentals](fundamentals)

## bottom

-   data scientist career

    -   data science is OSEMN
    -   [google merge sort and copy paste it](https://www.youtube.com/watch?v=X34ZmkeZDos) : \*\*insight
    -   [introduction to algorithms by cormen](introduction-to-algorithms-by-cormen)
    -   [standford automata theory cs154](standford-automata-theory-cs154)
    -   [Top 6 Python Libraries for Visualization Which one to Use?](Top-6-Python-Libraries-for-Visualization-Which-one-to-Use)
    -   [crash course chemistry](crash-course-chemistry)
    -   [crash course physics](crash-course-physics)
    -   [crash course game](crash-course-game)
    -   [crash coure engineering](crash-cour-engineering)
    -   [crash course AI](crash-course-AI)
    -   \*\*[data science datacamp](data-science-datacamp)
    -   data science = computer science + data mining
    -   data mining = mining data to find insight(not finding data)
    -   [jupyternotebook and ipython](jupyternotebook and ipython)
    -   \*\*[data science codecademy](data-science-codecademy)
    -   [back end engineer codecademy](back-end-engineer-codecademy)
    -   [python-cheatsheet](https://www.codecademy.com/learn/paths/data-science/tracks/dscp-python-fundamentals/modules/dscp-python-lists/cheatsheet)

-   IT

    -   [os](os)
    -   [IT Automation](IT Automation) - cron - cron jobs - crontab - for system admin
    -   [Configuration management](cm)
    -   https://unix.stackexchange.com/questions/325938/unauthorized-installations-in-dnf-after-entering-a-command-thats-not-found/ : sudo vs policykit, sudoers file, wheel group

-   unclassified
    -   [The 1 coding project idea guaranteed to get you a Software Development job](https://www.youtube.com/watch?v=oC483DTjRXU)
    -   [bigO complexity charts](https://www.bigocheatsheet.com/)
    -   https://www.quora.com/Is-reinforcement-learning-considered-a-branch-of-semi-supervised-learning : great insight - noether's theorem
    -   [ux/ui design principles](https://www.springboard.com/blog/ux-design-principles/)
