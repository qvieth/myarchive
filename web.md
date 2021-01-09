# web

## Contents

- [web](#web)
- [an overview of how the webs works](#an overview of how the webs works)
    - [the internet](#an overview of how the webs works#the internet)
        - [client and server](#an overview of how the webs works#the internet#client and server)
        - [ip address & domain](#an overview of how the webs works#the internet#ip address & domain)
        - [protocols](#an overview of how the webs works#the internet#protocols)
        - [URL](#an overview of how the webs works#the internet#URL)
    - [web & website & webpage](#an overview of how the webs works#web & website & webpage)
        - [html documents](#an overview of how the webs works#web & website & webpage#html documents)
        - [css](#an overview of how the webs works#web & website & webpage#css)
        - [packets](#an overview of how the webs works#web & website & webpage#packets)
        - [bandwidth](#an overview of how the webs works#web & website & webpage#bandwidth)
    - [cloud computing](#an overview of how the webs works#cloud computing)
        - [web apps](#an overview of how the webs works#cloud computing#web apps)
        - [html javascript css and more](#an overview of how the webs works#cloud computing#html javascript css and more)
        - [html5](#an overview of how the webs works#cloud computing#html5)
        - [3D in the browser](#an overview of how the webs works#cloud computing#3D in the browser)
        - [plug-in & extension](#an overview of how the webs works#cloud computing#plug-in & extension)
        - [cookies](#an overview of how the webs works#cloud computing#cookies)
        - [privacy vs security](#an overview of how the webs works#cloud computing#privacy vs security)
        - [DNS](#an overview of how the webs works#cloud computing#DNS)
        - [evolving a faster web](#an overview of how the webs works#cloud computing#evolving a faster web)
        - [open source and browsers](#an overview of how the webs works#cloud computing#open source and browsers)

# an overview of how the webs works
## the internet
- giant networks of computer

### client and server
- usually, the connection on the internet takes place between 2 computers only :
    - one that __has the information__ (__server__)
    - one that __wants it__ (__client__)

- client is a program that can take up many forms:
    - a web browser
    - email client
    - message app
    - a video streaming service (netflix)
- each of these programs will retrieve information from a __server__,where things are stored (website,mail,message,movie)
- although __client programs__ also send information to the server, they usually __don't store__ it, while __servers do__
- a __server__ can be considered a dedicated computer __always__ connected to the internet, whose sole purpose is __deliver__ content

### ip address & domain
- ip address has 4 number `91.198.174.192`
- a __domain__ has 3 parts, read from right to left:
    - top-level domain(TLD): .com .org
    - domain name : wikipedia
    - subdomain(optional) : most websites use www as the default subdomain
- think of __domain__ as a way to __name__ computers connected to the internet
- can't __buy__ a domain, actually __rent__ it from whoever is managing the __TLD__
- company who manage internet domains are called __domain registrars__ :

### protocols
- the purpose of internet is for computer to talk with each other
- and __like humans talk in different languages__, computer talk using __protocols__ :
    - ftp : file transfer : 1971
    - smtp : sending emails : 1971
    - imap : receiving emails : 1986
    - irc : chat : 1988
    - http : browsing html documents : 1989
> __protocol__ is somewhat like human communication: when we speak to each other, the __rules of grammar__
__provide structure__ to language and ensures that we can __understand__ each other and exchange ideas.

- 2 computer talk together create connection
- that group of interconnected devices grew from one room to many rooms

### URL
- with domains and protocols, we can build URL : uniform resource locator
- for example, the current page's URL is `http://marksheet.io/internet.html` and can be divided in 3 parts :
    - `http://` is the __protocol__
    - `marksheet.io` is the __domain__
    - `/internet.hml` is the __path__


    - subdomain
    - `?otherpart=-4242` query
    - `#00h42m30s` fragment
    - parameter : found in query string : q=url, ie=utf-8, oe=utf-8, aq=t, rls=org.mozilla:en-GB official, client=firefox-a

## web & website & webpage
- the __web__ is part of __internet__ _where webpages are shared_
- __webpage__ : a document written in HTML
- a __website__ is simply a collection of webpages located on a __same domain__

### html documents
- by default file extensions are hidden
- html is about __meaning__
- there is about 100 semantic HTML elements, but stick to the following list you'll be enough

| structure                                                                     | text                                      | inline                                            |
|-------------------------------------------------------------------------------|-------------------------------------------|---------------------------------------------------|
| header <br> h1 <br> h2 <br> h3 <br> nav <br> footer <br> article <br> section | p <br> ul <br> ol <br> li <br> blockquote | a <br> strong <br> em <br> q <br> abbr <br> small |

### css
- while html is about meaning, __css__ is about __styling__
- syntax : 
```css
/* a css rule */
selector{property: value;}
who{what: how;}`
```
- [css preprocessor](https://www.creativebloq.com/web-design/what-is-sass-111517618): scripting language : sass, scss, less

### packets
- The early creators of the Internet discovered that data and information could be sent more efficiently
- when broken into smaller chunks, sent separately, and reassembled. Those chunks are called packets
- So when you send an email across the Internet, your full email message is broken down into packets, sent to your recipient and reassambled
- the same thing happens when you watch a video on a website like youtube :
    - the videos are segmented into data packets
    - that can be sent from multiple youtube servers around the world and assembled to form the video that you're watching

### bandwidth
- mb per second

## cloud computing
### web apps
1. i can access data everywhere
2. i'll always get the lastest version of any app
3. it works on every device with a web browser
4. it's safer

### html javascript css and more
- today the web goes beyond just text, links and images
- we're able to play online chess or __seamlessly__ scroll around a map of our neighborhood, or facebook newsfeed
- without waiting for the __entire page__ to reload or every chess move or every map scroll
- the idea of such __dynamic webpage__ began with the invention of scripting language Javascript
- but the dynamic web as we know it today truly came to life __when XHR (XMLHttprequest) was introduced into javascript__
- __xhr__ enabled __individual parts__ of a web page to be altered without needing to reload the entire page
- as a result, web apps are faster and more reponsive
- __AJAX__ : the potent combination of Javascript, xhr , css and several web technologies
- ajax is kinda lamp

### html5
- video
- offline capabilities

### 3D in the browser
- it was hard to deliver a compelling 3d experience over the internet
- because 3d __requires data__ - lots of data - to display textures and shape
- in the past, these large amounts of data demanded more __internet bandwidth__ and more __computing power__ than most common system could handle
- modern broadband helped solve bandwidth needs
- as a result it's possible to send large amount of data over the internet
- neither broadband or raw computing power would matter without substantial advancements in the web browser's capabilities
- many modern browsers have adopted open __web technologies__ like __webgl__ and __3d css__
- with these technologies, web developers can create cool 3d effects for their web applications
- on top of that, many modern browsers now take advantage of technique known as __hardware-acceleration__
- this means that the browsers can use the graphic processing unit(GPU) to speed up the computations needed to display both 3d and 2d web content
- so why 3d in the browser a big deal?
- because now it joins html5, javascript and other nifty new technologies in the toolkit that web developers can use to create a powerful new generation of web applications

### plug-in & extension
### cookies
- cookies provide functionality that users may want from a websites : a memory of visits, in the past or in progress
- a cookie is a small piece of text sent to your browser by a website you visit
- it contains infomation about your visit that you may want the site to remmeber, like your referred language and other settings
- the browser stores this data and pulls it out the next time you visit the site to make the next trip esier and more personalized
- if you visit a movie website and indicate that you're most interested in comedies
- for instance, the cookies sent by the website can remember this so you may see comedies displayed at the start of your next visit
- cookies can be used in advertising as well, to remmeber your interest and show you related ads
- session-only cookies vs permanent cookies

### privacy vs security
- think of privacy and security of your home

### DNS
- think of phonebook but this time it's for IP address

### evolving a faster web
or speed up image, video, javascript on the web
- images and photos became commonplace on the web when computer scientists found ways to compress them into smaller files that could be send and downloaded more easily
- google is also collaborating with the web community on webm, 
- an effort to build out free, open-source video format that adapts to the computing power and bandwidth conditions of the web
- so quality video can be delivered to a computer in a farm house in nebraska or a smartphone in nairobi
- in the meantime, it's true that webpage with photos and video can be slow to load
- that's why a few engineers at google have been experimenting with new ways to compress images even further while keeping the same image quality and resolution
- the early result : they've come up with new image format called webp that cuts down the average image file size by 39%
 

- the __engines__ that __run javascript__ code in modern web browser have also been redesigned to process code faster than ever before
- __these__ fast javascript engines, such as __google chrome v8__, are now a core part of any modern web browser
- that means the next generation of fabulously useful javascript-based web application won't be hampered by the complexity of more javascript code


- another technique that modern browsers like chrome use to fetch and load web pages much more quickly is called __dns pre-resolution__

### open source and browsers
- today's internet stands on the __shoulders of giants__ :
- the technologists, thinker, developers, and organizations who continue to push the boundaries of innovation and share what they've learned
- __this spirit of sharing is at very heart of open-source software__
- __open source__ means that the inner working (source code) of a software are made available to all, and the software is written in an open, collaborative way
