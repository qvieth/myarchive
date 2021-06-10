# nodejs

-   [handler](handler)
-   [eventloop](eventloop)
-   [callback](callback)
-   [promise](promise)
-   [middleware](middleware)
-   [fastify](fastify)
-   [async](async)

-   node is ideal for data, I/O intensive and realtime apps include lot of disk or network access, we can serve more clients without the need to throw more in hardware - that's why node apps are highly scalable
    -   do not use node for CPU-intensive apps like video encoding or image manipulation service
    -   node s
-   backend -> main purpose : any application or sets of applications connected to the internet who's main purpose is to serve client's requests
    -   the 2 most common **back-end processes** are web servers and databases
        -   web server : anything that responses to http request with some data
        -   database : can be used independently from web servers - dbs can use a lot of resources - connect with each other sockets - support many connection
    -   old backend model : reder html on back end and send to client
    -   new model : backend return only data
    -   front end : code **running** on browser of mobile
    -   background process and caching
-   rest handling resources and request easier
    -   restful URL
    -   rest is just a fancy way of saying that a server responds to CRUD request in a standard way
-   In the prior chapter we learned how to build mock HTTP services
    -   In this chapter(chapter 2) we'll build on those services to include real-time functionality with mock data
    -   Deploying production-worthy real-time APIs is an **architectural and operational challenge** in itself
    -   -> need **infrastructurally and architecturally** focused teams and roles
