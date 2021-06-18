# web

- [app](app)
- [internet](internet)
- [protocol](protocol)
- [server](server)
- [computer science vs web development vs data science](computer science vs web development vs data science)
- [front-end vs back-end](front-end vs back-end)
- [htmlcss](htmlcss)
- [javascript](javascript)
- [origin](origin)
- [web strategy](web-strategy)

## FLEETING NOTES

- [learning web design 5th edition jennier](learning web design 5th edition jennier)
- [modern web architecture explained](https://www.youtube.com/watch?v=YGGBahexXYI) : talks to **3rd party backends** - payment,validation,analytics,maps,...
- [fireship](fireship)
- [websocket with socket.io](https://www.youtube.com/watch?v=1BfCnjr_Vjg) : good video, has a small chat app project
- What types of projects run best on a Backend as a Service? -> do more research about these types of cloud computing
     - Real-time applications (chat, messaging apps)
     - Transportation apps (similar to Uber)
     - Social-network type apps
     - Ecommerce apps
     - Music or Video streaming apps
     - Games
- node.js mvc | django mvt
- https://www.youtube.com/watch?v=9CEW3Tmx2tg : must use websites & tools for web developers
- [ux/ui design principles](https://www.springboard.com/blog/ux-design-principles/)
- https://websitesetup.org/ : how to create website wordpress

     - [back end engineer codecademy](back-end-engineer-codecademy)

- git awesome-react-component -> insight, focus on how to combine already made components/hooks to create websites

* https://blog.risingstack.com/the-history-of-react-js-on-a-timeline/ : react history -> google for similar topics of other technology
* google for ...(react,expressjs) concepts -> make a graph for it
* [react](react) concepts <- googled
     - https://owlypixel.com/learning-react-main-concepts/#components : good cheatsheet
     - https://daveceddia.com/what-react-does/ : what react do and doesn't - react rerender when you trigger it
     - https://daveceddia.com/react-getting-started-tutorial/
     - https://us.hidester.com/proxy.php?u=eJwBVgCp%2F3M6Nzg6Ivh7Uph4wHFImXiNpiysB5KoPVDmaA2LUnc%2B92nOo0P63cJoObjlWeI8SsP9JHBVtnxcExUrHc3%2Fk3U39FXPheWEgNe7i%2FFv6dkhP8zkTSI7CB8rew%3D%3D&b=7
     - https://www.youtube.com/watch?v=O6P86uwfdR0 : usestate() - webdevsimplified
     - https://www.youtube.com/watch?v=hQAHSlTtcmY : react in 30 min - webdevsimplified
     - https://daveceddia.com/react-getting-started-tutorial/ : 38 page react tutorial - this turotial is EXTREMELY GOOD
          - <div key:"value"
              - key:"value" is an object
              - => const hi = ({key}) => return ``<div>`` hi {key} ```</div>``
              - props is object
              - comback

## an overview of how the webs works

### the internet

- giant networks of computer

#### client and server

- usually, the connection on the internet takes place between 2 computers only :

     - one that **has the information** (**server**)
     - one that **wants it** (**client**)

- client is a program that can take up many forms:
     - a web browser
     - email client
     - message app
     - a video streaming service (netflix)
- each of these programs will retrieve information from a **server**,where things are stored (website,mail,message,movie)
- although **client programs** also send information to the server, they usually **don't store** it, while **servers do**
- a **server** can be considered a dedicated computer **always** connected to the internet, whose sole purpose is **deliver** content

#### ip address & domain

- ip address has 4 number `91.198.174.192`
- a **domain** has 3 parts, read from right to left:
     - top-level domain(TLD): .com .org
     - domain name : wikipedia
     - subdomain(optional) : most websites use www as the default subdomain
- think of **domain** as a way to **name** computers connected to the internet
- can't **buy** a domain, actually **rent** it from whoever is managing the **TLD**
- company who manage internet domains are called **domain registrars** :

#### protocols

- the purpose of internet is for computer to talk with each other
- and **like humans talk in different languages**, computer talk using **protocols** : - ftp : file transfer : 1971 - smtp : sending emails : 1971 - imap : receiving emails : 1986 - irc : chat : 1988 - http : browsing html documents : 1989

     > **protocol** is somewhat like human communication: when we speak to each other, the **rules of grammar** > **provide structure** to language and ensures that we can **understand** each other and exchange ideas.

- 2 computer talk together create connection
- that group of interconnected devices grew from one room to many rooms

#### URL

- with domains and protocols, we can build URL : uniform resource locator
- for example, the current page's URL is `http://marksheet.io/internet.html` and can be divided in 3 parts :

     - `http://` is the **protocol**
     - `marksheet.io` is the **domain**
     - `/internet.hml` is the **path**

     - subdomain
     - `?otherpart=-4242` query
     - `#00h42m30s` fragment
     - parameter : found in query string : q=url, ie=utf-8, oe=utf-8, aq=t, rls=org.mozilla:en-GB official, client=firefox-a

### web & website & webpage

- the **web** is part of **internet** _where webpages are shared_
- **webpage** : a document written in HTML
- a **website** is simply a collection of webpages located on a **same domain**

#### html documents

- by default file extensions are hidden
- html is about **meaning**
- there is about 100 semantic HTML elements, but stick to the following list you'll be enough

| structure                                                                     | text                                      | inline                                            |
| ----------------------------------------------------------------------------- | ----------------------------------------- | ------------------------------------------------- |
| header <br> h1 <br> h2 <br> h3 <br> nav <br> footer <br> article <br> section | p <br> ul <br> ol <br> li <br> blockquote | a <br> strong <br> em <br> q <br> abbr <br> small |

#### css

- while html is about meaning, **css** is about **styling**
- syntax :

```css
/* a css rule */
selector{property: value;}
who{what: how;}`
```

- [css preprocessor](https://www.creativebloq.com/web-design/what-is-sass-111517618): scripting language : sass, scss, less

#### packets

- The early creators of the Internet discovered that data and information could be sent more efficiently
- when broken into smaller chunks, sent separately, and reassembled. Those chunks are called packets
- So when you send an email across the Internet, your full email message is broken down into packets, sent to your recipient and reassambled
- the same thing happens when you watch a video on a website like youtube :
     - the videos are segmented into data packets
     - that can be sent from multiple youtube servers around the world and assembled to form the video that you're watching

#### bandwidth

- mb per second

### cloud computing

#### web apps

1. i can access data everywhere
2. i'll always get the lastest version of any app
3. it works on every device with a web browser
4. it's safer

#### html javascript css and more

- today the web goes beyond just text, links and images
- we're able to play online chess or **seamlessly** scroll around a map of our neighborhood, or facebook newsfeed
- without waiting for the **entire page** to reload or every chess move or every map scroll
- the idea of such **dynamic webpage** began with the invention of scripting language Javascript
- but the dynamic web as we know it today truly came to life **when XHR (XMLHttprequest) was introduced into javascript**
- **xhr** enabled **individual parts** of a web page to be altered without needing to reload the entire page
- as a result, web apps are faster and more reponsive
- **AJAX** : the potent combination of Javascript, xhr , css and several web technologies
- ajax is kinda lamp

#### html5

- video
- offline capabilities

#### 3D in the browser

- it was hard to deliver a compelling 3d experience over the internet
- because 3d **requires data** - lots of data - to display textures and shape
- in the past, these large amounts of data demanded more **internet bandwidth** and more **computing power** than most common system could handle
- modern broadband helped solve bandwidth needs
- as a result it's possible to send large amount of data over the internet
- neither broadband or raw computing power would matter without substantial advancements in the web browser's capabilities
- many modern browsers have adopted open **web technologies** like **webgl** and **3d css**
- with these technologies, web developers can create cool 3d effects for their web applications
- on top of that, many modern browsers now take advantage of technique known as **hardware-acceleration**
- this means that the browsers can use the graphic processing unit(GPU) to speed up the computations needed to display both 3d and 2d web content
- so why 3d in the browser a big deal?
- because now it joins html5, javascript and other nifty new technologies in the toolkit that web developers can use to create a powerful new generation of web applications

#### plug-in & extension

#### cookies

- cookies provide functionality that users may want from a websites : a memory of visits, in the past or in progress
- a cookie is a small piece of text sent to your browser by a website you visit
- it contains infomation about your visit that you may want the site to remmeber, like your referred language and other settings
- the browser stores this data and pulls it out the next time you visit the site to make the next trip esier and more personalized
- if you visit a movie website and indicate that you're most interested in comedies
- for instance, the cookies sent by the website can remember this so you may see comedies displayed at the start of your next visit
- cookies can be used in advertising as well, to remmeber your interest and show you related ads
- session-only cookies vs permanent cookies

#### privacy vs security

- think of privacy and security of your home

#### DNS

- think of phonebook but this time it's for IP address

#### evolving a faster web

or speed up image, video, javascript on the web

- images and photos became commonplace on the web when computer scientists found ways to compress them into smaller files that could be send and downloaded more easily
- google is also collaborating with the web community on webm,
- an effort to build out free, open-source video format that adapts to the computing power and bandwidth conditions of the web
- so quality video can be delivered to a computer in a farm house in nebraska or a smartphone in nairobi
- in the meantime, it's true that webpage with photos and video can be slow to load
- that's why a few engineers at google have been experimenting with new ways to compress images even further while keeping the same image quality and resolution
- the early result : they've come up with new image format called webp that cuts down the average image file size by 39%

- the **engines** that **run javascript** code in modern web browser have also been redesigned to process code faster than ever before
- **these** fast javascript engines, such as **google chrome v8**, are now a core part of any modern web browser
- that means the next generation of fabulously useful javascript-based web application won't be hampered by the complexity of more javascript code

- another technique that modern browsers like chrome use to fetch and load web pages much more quickly is called **dns pre-resolution**

#### open source and browsers

- today's internet stands on the **shoulders of giants** :
- the technologists, thinker, developers, and organizations who continue to push the boundaries of innovation and share what they've learned
- **this spirit of sharing is at very heart of open-source software**
- **open source** means that the inner working (source code) of a software are made available to all, and the software is written in an open, collaborative way
