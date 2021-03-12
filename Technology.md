# Technology
* [science](science) of craft - 'know how' knowledge of how to make things that would otherwise not exist
# end goal
* organize this mess of idea | Sat Jan  9 12:56:37 PM +07 2021
* [fundamentals](fundamentals)
# note
- callback : you can do it rightnow, but you would do it later
    - think of call to dentist just to tell them call me back later for appointment
``` MIDDLEWARE
A function that is invoked by the Express routing layer before the final request handler, and thus sits in the middle between a raw request and the final intended route. A few fine points of terminology around middleware:
    var foo = require('middleware') is called requiring or using a Node.js module. Then the statement var mw = foo() typically returns the middleware.
    app.use(mw) is called adding the middleware to the global processing stack.
    app.get('/foo', mw, function (req, res) { ... }) is called adding the middleware to the “GET /foo” processing stack.
```
``` * A special mention for lodash/underscore and functional programming in general
First, don't use any for or while loops in your node program. It does not work with concurrent processes.
Example: For each file in Files, open it, then do X. Yeah good luck.
The correct way to do this is to _.map(Files, ... ) into either a) functions with a callback or b) promises and then use async.parallel/Promise.all respectively. Technically you could create a new array, for loop into it and then async.parallel/Promise.all on that, but if you do that a few times your code will look like !$%^$!.
The key idea here is to be able to treat "code i am going to run" as objects. _.map captures that semantics very well.
```
- [o] [Better error handling with async/await ](https://dev.to/sobiodarlington/better-error-handling-with-async-await-2e5m)
    - [ ] from callback hell to promises
    - [X] The example below use promises to solve callback hell
        * [X] by using multiple chained `.then` calls
        - [X] instead of nesting callbacks
- [ ] [You don't need promises in Python: just use async/await!](https://quentin.pradet.me/blog/you-dont-need-promises-in-python-just-use-asyncawait.html)
- [ ] destructuring - powerful for data manipulation
- [ ] [webdevsimplified - js array](https://www.youtube.com/watch?v=R8rmfD9Y5-c&list=PLZlA0Gpn_vH-0FlQnruw2rd1HuiYJHHkm)
    - `.filter` `.map`
    - high order function and array
- [ ] error handling
    - [ ] async - more elegant way to handle promises
    - [ ] [webdevsimplified - js promises](https://www.youtube.com/watch?v=DHvZLI7Db8E)
        - [ ] `.then` or `.catch`
        - [ ] setTimeout is not the only form of asynchronous code in JS that's built in -> promises
        - [ ] the concept of promises which is something that you see whenever you see .then or .catch coming after a function
        - [ ] especially when you're doing a fetching for example is another great example of asynchronous code that you don't actually know how long it's going to take since you don't specify the timeout
        - [ ] **WE SETTIMEOUT BECAUSE WE HYPOTHETICALLY WORKING WITH SERVER**
- [ ] avoid callback hell => `new Promise(resolve, reject) => {}`
- [ ] `getElementById()`
- [ ] `querySelector()`
- [ ] `addEventListener()` 
- [ ] traversy DOM 4 part - event object part 3 - last project
- https://www.youtube.com/watch?v=PoRJizFvM7s
    - callbacks-promise-async await: dom was already painted, resolve, output, promise.all, .then()
    - sync call back, async call back
- [JS arrow function](https://www.youtube.com/watch?v=h33Srr5J9nY) : great tutorial for named function, anon function vs arrow function, their this scope
- responsive website :
    - https://www.youtube.com/watch?v=M3qBpPw77qo
    - https://www.youtube.com/watch?v=p0bGHP-PXD4
- https://rapidapi.com/blog/types-of-apis/
- management information systems
    - system development or system analysis
    - Basic analytical and problem solving skills for design, creation and testing of programs
    - gathering requirements from a technical perspective and developing documentation of system specifications
    - designing and implementing new methods, procedures, and systems (both automated and manual) to improve the processing and flow of information within the company.
    - Gathers information from users for analysis of technical problem areas and prepares elementary feasibility studies
- 
-   Emmet is Vim for web developing. XD
    P.S.: Since you are gonna do webdev
        try vim-surround
        vim-commentary
        and vim-easymotion for flash like workflow
        And also learn SASS(Tabbed version) from the get go
        instead of writing traditional CSS and thank me later. XD

- css - reset - normalizer
-   2 project
    -   1 data science : back to datacamp finish the career track and get the project from it
    -   1 django - https://www.youtube.com/watch?v=6DI_7Zja8Zc&list=PL-osiE80TeTtoQCKZ03TU5fNfx2UY6U4p&index=17
    -   look for job description on itviec, glints
-   comeback to datacamp, continue the reverse engineering
- Nho lz Tai giang lai Mdn docs css
- hoi ve cach dxc.technology hoat dong(cach business kiem tien, khach hang,...) cong nghe, viec lam
- in-box knowledge and out-box knowledge : read in-box to relax, when feel focus learn out-box

- middleware is just a function take in req, res, next and call next whenever it wants to move to the next form of the [middleware](middleware)
- web security - sanitize data
- They provide tools and libraries that simplify common web development tasks including :
    - routing URLs to appropriate handlers
    - interacting with databases
    - supporting sessions and user authorization
    - formatting output (e.g. HTML, JSON, XML)
    - and improving security against web attacks
- [serverside diagram](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Introduction)
- [management information system](https://en.wikipedia.org/wiki/Management_information_system)

* https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Thinking_before_coding : important, many insights
    * When starting with a web project, many people focus on the technical side
        - Of course you must be familiar with the technique of your craft, but what really matters is what you want to accomplish
        - Yes, it seems obvious, but too many projects fail not from a lack of technical know-how, but from **lack of goals and vision**
        - **A project should never starts with the technical side**
- look back to look forward
- optimize : time to learn something = time to do something
- express :
    - middleware functions are functions that have acces to the request and response object
    - express has built in middleware but middleware also comes from 3rd party packages as well as custom middleware
    - excute any code
    - make changes to the request/response objects
    - end response cycle
    - call next middleware in the stack
- javascript
    - named function
    - async = non-blocking i/o call
    - high order array methods
    - anonymous function
    - arrow function
    - ?
    - destructuring assignment to assign variables from arrays
    - rest operator
- array index
- realtime chat with user & room
    - socketio
    - use the javascript to insert into the DOM
    - right now we just have a bunch of static stuff here, hard coded with html
    - so the next thing i want to do is set up our server to handle SOCKET.IO
    - so this is working really good
    - of course you could add on to this
    - intergreate mongoDB or somekind of SQL database or whatever
    - and store the users and basically have them log in to join the chat
- https://www.youtube.com/watch?v=GZvSYJDk-us
    - apis : interface : abstract way to use something
    - web apis
    - that all browser must implement
    - leverage apis to focus on the business problem at hand

- [CCS](https://www.youtube.com/watch?v=1Rs2ND1ryYc)
    - which properties you use to describe this :
[developer platform](developer-platform)
[.NET](.NET)

- theory of computation


# data scientist career
* data science is OSEMN 
* [google merge sort and copy paste it](https://www.youtube.com/watch?v=X34ZmkeZDos) : **insight
* [introduction to algorithms by cormen](introduction-to-algorithms-by-cormen)
* [standford automata theory cs154](standford-automata-theory-cs154)
* [Top 6 Python Libraries for Visualization Which one to Use?](Top-6-Python-Libraries-for-Visualization-Which-one-to-Use)
* [crash course chemistry](crash-course-chemistry)
* [crash course physics](crash-course-physics)
* [crash course game](crash-course-game)
* [crash coure engineering](crash-cour-engineering)
* [crash course AI](crash-course-AI)
* **[data science datacamp](data-science-datacamp)
* data science = computer science + data mining
* data mining = mining data to find insight(not finding data)
* [jupyternotebook and ipython](jupyternotebook and ipython)
* **[data science codecademy](data-science-codecademy)
* [back end engineer codecademy](back-end-engineer-codecademy)
* [python-cheatsheet](https://www.codecademy.com/learn/paths/data-science/tracks/dscp-python-fundamentals/modules/dscp-python-lists/cheatsheet)

# IT
* [os](os)
* [IT Automation](IT Automation) - cron - cron jobs - crontab - for system admin
* [Configuration management](cm)
* https://unix.stackexchange.com/questions/325938/unauthorized-installations-in-dnf-after-entering-a-command-thats-not-found/ : sudo vs policykit, sudoers file, wheel group

# unclassified
* [The 1 coding project idea guaranteed to get you a Software Development job](https://www.youtube.com/watch?v=oC483DTjRXU)
* [bigO complexity charts](https://www.bigocheatsheet.com/)
* https://www.quora.com/Is-reinforcement-learning-considered-a-branch-of-semi-supervised-learning : great insight - noether's theorem
* [ux/ui design principles](https://www.springboard.com/blog/ux-design-principles/)
