# eventloop

-   eventloop = callstack -> ES6 job queue -> message queue
    -   https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop
    -   https://nodejs.dev/learn/the-nodejs-event-loop
-   Every time the event loop takes a full trip, we call it a tick
-   Message Queue is also where user initiated events like
    -   click or keyboard events
    -   or fetch responses are queued before your code has the opportunity to react to them
    -   Or also DOM events like onLoad
