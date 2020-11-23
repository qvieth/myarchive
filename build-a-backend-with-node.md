# build a back-end with node/express.js

- The goal of this unit is to learn about the popular back-end environment
    - Node.js, and how to create back-end servers and APIs in JavaScript using the popular Express.js framework
- Learning these tools will enable you to create dynamic server applications that can greatly surpass the capabilities of a static web page
- After this unit, you will be able to:
    - Understand Node.js
    - Create a server with Express.js
    - Design/serve RESTful APIs
    - Understand what CORS is
    - Explain routing

## Dynamic site
- [static vs dynamic site](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Client-Server_overview) : look at the static vs dynamic site graph, extremely useful
- Understanding how static sites work is nevertheless useful when learning server-side programming
    - because dynamic sites handle requests for __static files__ (CSS, JavaScript, static images, etc.) in exactly the same way

- A dynamic site is one that can generate and return content __based on__ the `specific request URL` and `data`
    - (rather than always returning the same hard-coded file for a __particular URL__)
- Using the example of a product site, the server would __store__ product "__data__" in a __database__ _rather than individual HTML files_
- When receiving an HTTP GET Request __for a product__, the server determines the product ID, __fetches the data from the database__
    - and then constructs the HTML page for the response by __inserting the data__ into an HTML template
- This has major advantages over a static site:
    - Using a database allows the product information to be stored efficiently in an easily extensible, modifiable, and searchable way
    - Using HTML templates makes it very easy to change the HTML structure
        - because this only needs to be done in one place, in a single template, and not across potentially thousands of static pages

- if you don't write an app which returns dynamically generated html code
    - well then you will at least write some __rest api__ that offers endpoints for your __static app__ to __fetch and store data__


- You also need a way to upload files: from your hard drive to a distant __web server__
    - To do that you should use a __publishing tool__ such as an (S)FTP client, RSync, or __Git/GitHub__
    - https://pages.github.com/

- [the only nodejs introduction youll ever need](https://medium.com/m/global-identity?redirectUrl=https%3A%2F%2Fcodeburst.io%2Fthe-only-nodejs-introduction-youll-ever-need-d969a47ef219)


## what webapps do
- [what can a web framework do for you?](https://developer.mozilla.org/en-US/docs/Learn/Server-side/First_steps/Web_frameworks)
    - Work directly with HTTP requests and responses
        - Get an HttpRequest (request)
        - perform operations using information from the request.
        - Return HttpResponse
    - Route requests to the appropriate handler
    - Make it easy to access data in the request
    - Abstract and simplify database access
    - Rendering data

- In a traditional data-driven website, a web application waits for HTTP requests from the web browser (or other client)
- When a __request__ is received the application works out what action is needed based on the URL pattern
    - and possibly associated information contained in POST data or GET data
    - Depending on what is required it may then __read__ or __write__ information __from a database__ or perform other tasks required to satisfy the request
- The application will then return a __response__ to the web browser
    - often dynamically creating an HTML page for the browser to display by inserting the retrieved data into placeholders in an HTML template
- Express provides methods to specify what function is called for a particular
    - HTTP verb (GET, POST, SET, etc.)
    - and URL pattern ("Route")
    - and methods to specify what template ("view") engine is used
    - where template files are located, and what template to use to render a response
    - You can use Express __middleware__ to __add support for cookies, sessions, and users, getting POST/GET parameters, etc__
    - You can use any __database mechanism__ supported by Node (Express does not define any database-related behaviour)

- The following sections explain some of the common things you'll see when working with Express and Node code
