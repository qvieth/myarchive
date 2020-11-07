# binary file
- __binary data__ : sequence of 8-bit bytes
- __binary files__ : are usually thought of as being a sequence of __binary data__
- but __binary files__ can also mean that they __contain images, sounds, compressed versions of other files__, any type of file content whatsoever
- some binary files contain __headers__, __blocks of metadata__ used by a computer program to __interpret the data__ in the file
- the __header__ often contains a __signature or magic number__ which can __identify the format__
- if the file is as __executable__ and run, the operating system will interpret the file as a series of instructions in its machine language 

## send files through internet
to send binary files through certain systems (such as email) that do not allow all data values, they are often translated into a plain text representation (using, for example, __base64__ - __radix-64__).
- base - radix - [positional notation](https://en.wikipedia.org/wiki/positional_notation)
- base16 : hex
- __base64__ : binary-to-text encoding schemes
- each __non-final__ base64 digit represents exactly __6 bits__ of data
- __three__ 8-bit bytes can therefore be represented by __four__ 6-bit base64 digits 
- __MIME__ : Multipurpose Internet Mail Extensions : an Internet standard that extends the format of email messages to support text in character sets other than ASCII, as well as attachments of audio, video, images, and application program
- [base64 vs hex for sending binary content over the internet in xml doc](https://stackoverflow.com/questions/3183841/base64-vs-hex-for-sending-binary-content-over-the-internet-in-xml-doc)

- [Difference between Git and Nexus?](https://stackoverflow.com/questions/13490684/difference-between-git-and-nexus)
- In everyday use, you'd store your :
    - __source code and its history__ in a __git__ repository (for collaboration)
    - __build artifacts__ (the compiled software you want to deliver) in __Nexus__
- developers describe __GitHub__ as "powerful __collaboration__, review, and code management for open source and private development projects"
- while __Sonatype Nexus__ is detailed as "best way to organize, store, and __distribute__ software components". Deliver better, safer software even faster with __software supply chain automation__


- computer security - network security - [vulnebility management](https://en.wikipedia.org/wiki/Vulnerability_management)
- whenever __qualys__ (__vulnebility management__ solution) scan finds out __software vulnerability__, say for example java sdk or any software version that has a potential vulnerability, we search the web to find out the solution and usually install a __later version__ or __patch__ downloading from the web
- the problem is, as we are downloading it from web and there are a number of servers where we patch and as an ultimate outcome different people downloads different version and so forth
- so i want to create a repository for such binaries so that we use the same patch for all servers.
- when i was thinking about the repo, obviously first thought came as github. but then i realized, it is for __code__ version control and __collaboration__, not for the __packaged software__
- the other option i am thinking is __jfrog artifactory__ which stores the __binaries__ and the __package software__ 
- [How do different version control systems handle binary files?](https://stackoverflow.com/questions/6598700/how-do-different-version-control-systems-handle-binary-files/6599303#6599303)

- what is dependency?
- You have two main kind of dependencies:
    - source dependencies (you need to include, within the sources of your project, source from another project),
    - binary dependencies (you need to include a packaged set of files, like the ones found in a shared library).

- continuous integration (CI) pipeline platforms : Travis CI, circleCI, jenkins
- 
- [When to pull from Docker repo and when from Git repo and then build?](https://stackoverflow.com/questions/49071356/when-to-pull-from-docker-repo-and-when-from-git-repo-and-then-build)
