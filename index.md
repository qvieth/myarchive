# My note

```
"Rome wasn't built in a day"
 STRUCTURE : TOP - QUICK NOTE, MIDDLE - IMPORTANT NOTE, BOTTOM - ORGANIZED NOTE
 WP:start
```

## top

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
    -   almost every data structure we've coverd up until this point has been stored "linearly"
    -   trees store data hierarchically as opposed to linearly
    -   an abstract data structure which contains a series of linked nodes connected together to form a hierarchical representation of information
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

*   \*\*linked list : sequential access | node = data + pointer(takes computer to the next node in the list)
    -   how to define linked list in a specific language
    -   used in the backing of other data structures, we can use linkedlist to make stacks, queues

-   queue
-   stack : undo/redo | back-paging | recursiong | LIFO ASID nn11
-   random access data structures - independent elements - O(1) accessing - array and arraylist
-   sequential(limited) access data structures - dependent elements - stack, queue and linked lists

*   \*\*arraylist - why not always use arraylists - array is quite trash comparing to arraylists
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

## middle

1. **USE IT OR LOSE IT** :D -> forget everything after understand it
2. tree | set
3. modeling mathematically
4. Object-oriented studying - modular studying
5. reverse engineering + studying from big ideas down
6. 2 ways to learn everything : bottom-up - top-down (page 13 - mathematics for machine learning)(should combine this)
7. classification tree - how to navigate to the knowledge > knowledge
8. communicating : outcomes{goal{what |though, ideas, concept| you want to transfer to target}}
9. collaboration is about understanding : -> my framework
   X] my communicating framework : get inspired by UML : 1st : goal iamge, 2nd : lack, 3rd : talk without thinking
   X] i'm writing things while talking not for you to see, but for both of us to see, to make me evaluate my own thinking, sometimes i think it is too fast, can't keep track in a short period of times
10.
1. code should be the last thing to be paid attention, focus on the process, ideas
2. level of complexity -> if low, skip, high, pay attention and focus the math concept
3. aware of your own blackbox
4. keyword : FUNDAMENTAL THEOREM OF ... | BIG IDEAS OF ... | ... CHEATSHEET | ... CALCULATOR | ... NOTATION
5. technology - collective learning - technological progress -> [crash course big history](crash-course-big-history)
    - Technology -> progress , engineer -> process
6. there's no one size fit all
7. cookbook
8. start new subject with video, later documents
9. i have not failed, i have only found out 10000 ways that won't work
10. PREPARE - when something would make you panic, think of searching youtube for a way to deal with it e.g. meet girlfriend parents
11. LEARN HOW TO READ THE DOCUMENT - not learn the document - do anything, like watching youtube, reading other things, just to learn to read the document
    - learn from course (like 6hrs)(not small video) - do a research on types of video in relation with grasping rate vs reading docs
    - real projects, long courses video is good for BIG PICTURE grasping
    - always speed up video
    - JS promises
    - callback, arrow functions - middleware function(1,2,next) vs route handler callback
12. search for python equivalent of JS, then try to understand the python
13. async/await is the best way to express asynchronous I/O in combination with using an event loop
14. event loop: when A happens, do B
15. Think of async/await as an **API for asynchronous programming**
16. https://en.wikipedia.org/wiki/Metasyntax
17. CALLBACK FUNCTION AKA HANDLER FUNCTION
18. [I find that learning node.js is difficult for me. Can someone give me an advice?](https://www.quora.com/I-find-that-learning-node-js-is-difficult-for-me-Can-someone-give-me-an-advice)
    ] do similar search
19. LEARN TO ASK QUESTION <- focus on asking question only
20. on my way of self learning, google learning, i realize 1 important things :
    ] it's not about the answer, asking question is everything, asking the right question is the key
21. PROJECT -> BREAKDOWN
22. [Is it possible to append to innerHTML without destroying descendants' event listeners?](https://stackoverflow.com/questions/595808/is-it-possible-to-append-to-innerhtml-without-destroying-descendants-event-list)
23. [programming paradigm](https://en.wikipedia.org/wiki/Programming_paradigm)
24. closure of a function : a variable act like arugment but cannot be passed as parameter
25. programming : types are object, functions are morphisms | a -> b -> b | arrow : f = a -> b, id_b = b -> b | id_b after f
26. [category theory](category-theory) : sets and functions between sets | think of the 2 square image and the arrows
27. composition of functions is associative
28. how to represent lists...
29. what is ordered list?
30. 7 primitive types of data : string, number, array, set, true, false, null
31. GOOGLE HOW TO LEARN ABOUT SOMETHING FIRST RATHER THAN GOOGLE FOR THE THING ITSELF
    - or you can just **WIKI** it
32. https://en.wikipedia.org/wiki/Outline_of_logic
33. https://www.quora.com/What-should-one-do-to-study-mathematical-logic

## bottom

-   [quick thought](quick-thought)
-   [roadmap](roadmap)
-   [MYDOCS](MYDOCS)

-   [Mathematics](Mathematics)
-   [Ideology](Ideology)
-   [Technology](Technology)

-   [Finance & Business](Finance-n-Business)
-   [MYPROJECT](MYPROJECT)

-   [Stephen Wolfram](Stephen-Wolfram)
-   [Elon Musk](Elon-Musk)

-   [Archive](archive)
