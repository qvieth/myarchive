# promises

-   [You don't need promises in Python: just use async/await!](https://quentin.pradet.me/blog/you-dont-need-promises-in-python-just-use-asyncawait.html)

-   [better error handling with async/await](https://dev.to/sobiodarlington/better-error-handling-with-async-await-2e5m)
    -   from callback hell to promises
    -   The example below use promises to solve callback hell
        -   by using multiple chained `.then` calls
        -   instead of nesting callbacks
-   [promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)
-   avoid callback hell => `new Promise(resolve, reject) => {}`
    -   [webdevsimplified - js promises](https://www.youtube.com/watch?v=DHvZLI7Db8E)
        -   `.then` or `.catch`
        -   setTimeout is not the only form of asynchronous code in JS that's built in -> promises
        -   the concept of promises which is something that you see whenever you see .then or .catch coming after a function
        -   especially when you're doing a fetching for example is another great example of asynchronous code that you don't actually know how long it's going to take since you don't specify the timeout
        -   **WE SETTIMEOUT BECAUSE WE HYPOTHETICALLY WORKING WITH SERVER**
