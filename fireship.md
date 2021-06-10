# fireship

## back end development

-   everythings you need to know about apis - essential skill for both front end and backend developers
    -   oauth 2.0
    -   api keys
    -   how to work with google apis, nodejs
    -   how to schedule your code to run in the background with a service cloud function
    -   stateless : client and server don't need to know anything about each other's internal state
-   there are 2 main types of authentication that you should know about rightnow
    -   api keys
    -   oauth
-   when think about youtube or any api for that matter there are 2 main types of resources :
    -   those are public
    -   those are private
-   for example :
    -   a get request to a public video is something that anybody can do
    -   but if we wanted to modify that video with a `PUT` request
        -   we would need to have the proper authorization to do so like being the videos owner or admin
        -   or as developers we could get the users permission using oauth
    -   just reading public data? -> use api key
        -   the api key is simply a way for youtube to identify who is making the request
        -   quotas : a given api key can only make so many requests per day in the case of youtube they assigned points to every request and then cap your daily usage at 10 thousand points
    -   need private user data? -> use oauth 2.0
    -   access token - refresh token

## learn docker in 7 easy steps

-   https://www.youtube.com/watch?v=gAkwW2tuIqE&list=PL0vfts4VzfNiq0-fXbVVdnngU1Ur2SzyZ&index=5
-   what i will learn :
    -   containerize nodejs app
    -   install & tooling
    -   dockerfile : most important
    -   host machine : hardware + operating system
    -   very important advance concept :
        -   port forwarding
        -   volume
        -   docker compose : how to manage multiple container with docker compose
    -   docker file : blueprint for building iamge
    -   image : template for running container
    -   container : running process
    -   1 image can spawn multiple container -> kubernetes come into play to manage workflow
    -   docker file : write code to build your image and ultimately run your app as a container
    -   iamge -> push to container registry somewhere - docker hub or your favorite cloud provider
    -   but in this lesson only run on local host
    -   if you stop a container, any state or data you creted inside the container will be lost
    -   volumnes : share data across multiple container - to persist files
    -   just a dedicated folder on a host machine
    -   debugging

## firebase

https://www.youtube.com/watch?v=q5J5ho7YUhA&list=PL0vfts4VzfNiq0-fXbVVdnngU1Ur2SzyZ&index=5

-   choosing a right tech stack for your product in a world of unlimit possibility is extremely challenging
-   here's billion dollar todo list app
-   you have a vision for how front end experience will work
-   but behind the front end you have a ton of technical decision to make on the backend :
    -   how authenticate user
    -   which database
    -   how to run trusted code on server
    -   how to handle security
    -   analytics
    -   does it scale when the userbase grow?
-   these decisions are hard to get right
-   think about them take time, money and energy
-   when we better spent focusing on user experiment
-   when it's come to minimize decisions fatique, there's nothing quite like firebase, it's contain everything most app will need
-   to build and run a production app at scale
-   this is what we call BaaS
-   the best code is no code at all
-   when writing code in firebase, you'll find the sdks are extremely well documented and highly optimized to get feature builds quickly
-   what we will learn about firebase :
    1. deploy a full stack web app to the cloud
    2. sign-in with google : google authen the user with google account
    3. firestore
-   googlecloud : serverside infrastructure
-   firebase : client-side sdks that make it easy for your frontend app to connect to backend cloud infrastructure
-   a project connect to multiple app : web app, ios app, android app
