# [IT Automation](https://www.youtube.com/watch?v=ce434nD79nU)

<!-- vim-markdown-toc GFM -->

* [Introduction to Automation](#introduction-to-automation)
* [what is automation](#what-is-automation)
        * [what's difference between a script and a program?](#whats-difference-between-a-script-and-a-program)
        * [benefits of automation](#benefits-of-automation)
        * [pitfalls of automation](#pitfalls-of-automation)
* [ruby (file.rb)](#ruby-filerb)
        * [flow control with branching](#flow-control-with-branching)
        * [branching summary](#branching-summary)
        * [array data type](#array-data-type)
        * [loops](#loops)
        * [hashes](#hashes)
* [OOP](#oop)
        * [class](#class)
        * [methods](#methods)
        * [styles](#styles)
* [system programming](#system-programming)
        * [reusing code](#reusing-code)
        * [modules](#modules)
        * [library](#library)
        * [packages](#packages)
        * [finding packages](#finding-packages)
        * [programming with files (manipulate files and directories)](#programming-with-files-manipulate-files-and-directories)
        * [scripting pipelines](#scripting-pipelines)
                * [intro to I/O streams](#intro-to-io-streams)
                * [Standard Streams](#standard-streams)
        * [subprocess](#subprocess)
                * [running System Commands in Ruby](#running-system-commands-in-ruby)
                * [scripting subprocess](#scripting-subprocess)
                * [backticks "`"](#backticks-)
                * [open3](#open3)
                * [when to use subprocesses](#when-to-use-subprocesses)
                * [subprocess summary](#subprocess-summary)
        * [writing script from the ground up](#writing-script-from-the-ground-up)
                * [introduction](#introduction)
                * [problem statement](#problem-statement)
                * [research](#research)
                * [planning](#planning)

<!-- vim-markdown-toc -->

## Introduction to Automation
automation, centralize monitoring, configuration management at scale

## what is automation
- autimation is process of replace manual step with the one which automatically.
- benefit of automation : consistency
- automation isn't the solution to all situation
> some task just aren't suited to automation, because they might require a degree of __creativity__ or __flexibility__ that automatic systems can't provide
- for more __complexity__ and less __frequency__, automation is more costly
- in this course we talk about different ways you can leverage you automation for your role in Informaiton technology
> in information technology, the automation of these tasks is commonly accomplished by encoding the logic to perform the task into a __program__ or __script__
- automation in technology industry is usually done through the implementatiof __programs__ and __scripts__
- some tools like __chef__ or __puppet__ provide out of the box solution to automate repetitive tasks, without required much programming knowledge
- in the situation you need to perform a task these tools __don't support__, you can __create your own custom automation__ by using programming language to manipulate the underlying system

### what's difference between a script and a program?
- Scripts: Programs with a __short development cycle__ that can be created and deployed __quickly__, usually be written in __interpreted language__
- whether you use the interpreted or compiled language, the ability to program is one of the most powerful tools in the IT support specialist toolbox

### benefits of automation
- increase the effectiveness of IT team without increasing team member
- automation allows IT infrastructure to '__scale__', and keep pace with growth and demand
- IT : setting an account for new worker
- instead of having the IT support specialists interact independently with each of the system that create a new user account, mailbox, shared folder and permissions, there could be a better way : the IT suport specialist create a list of the steps and action that needed to be taken, and then has the computer computer perform them each team a new employee was hired by company
- we can refer this list of step as a __script__ as we mentioned
- think of this script as the series of instruction written in code by computer
- when we given initial information like

### pitfalls of automation
- Pareto priciple can help you to decide which task to automate: 20% of the system admin tasks you perform are responsible for 80% of your work
- if you can identify and automate those 20% of task, you can save yourself a lot of time
- it can be really difficult where to automate
- an automation that is implemented can be fragile: if underlying system changed and the automation is updated accordingly
- __bit rot__ : the actual bits in the script don't decay, but its assumptions about the implicit signals it relies on do
- __SRE__: site reliability engineer : unique role that requires either a background as software developer with addional operations experience, or a sysadmin or in an IT operations role that also has software development skill, SRE teams use software as a tool to manage systems, solve problems, and automate operations tasks [(read more)](https://www.redhat.com/en/topics/devops/what-is-sre#:~:text=Site%20reliability%20engineering%20SRE%20is,problems%2C%20and%20automate%20operations%20tasks.)

## ruby (file.rb)
- puts 'hello world'
- print 'hello world'
- __data types__: string, integer, float, boolean
- __operators__ : arithmetic && comparison && bitwise && assignment && logical && dot && double colon : remainder modulus, greater, smaller, equal ==,not equal !=, and &&, or ||, not !
- __expressions and numbers__
-  __variables__: valid && invalid: name must start with letter or underscore

### flow control with branching
- the ability of a program to alter its execution sequence is called __branching__ or __flow control__
- it's a key component to make your script and automation useful
- you're often use the concept of branching in your everyday life : cold => wear jacket, rain => use umbrella
- in your scripts, you can also instruct computer to make decision based on inputs, so that it's __tailor made__ to you needs
- let's imagine that you would've given a task of writting a program that can decide if a person was old enough to vote
- __if elseif else end__ 

### branching summary
- using branching to determine the flow of your program
- anytime your program needs to make a decision, you can specify its __behavior__ with a __branching statement__

### array data type
- []
- __indexing__ [0,1,2]
- .each : iterator
- do...end block
- |iterator| {#{variables} seach for these}

### loops
- while loop

### hashes
- aka __associative array__
- key : value
- a={'cat'=>'animal'}
- iterate with hases

## OOP
- think of how to describe an apple to a computer: using just __variables__ and __expressions__
- ruby follow [OOP](OOP): __model concepts__ using __classes__ and __objects__
### class
- class name must start with __uppercase__ letter
- .class .instance_of?(Integer)
- __inheritance__:
- object = class.new

### methods
- __argument, parameter__
- __return__ value

### styles
principles when writing script : 
- self documenting
- choose conventional name for variables
- comments and consistency

## system programming
### reusing code
- organize and reusing code __across__ different files
- code from different files : load, require, include 
- __requires__ : 
```
re "./super_useful_methods"
```
- $LOAD_PATH variable
- require_relative
- load vs require method : load reprocess each time it is called, while require keep track of what called, used only one 
- just stick with __require__

### modules
now that we know how to import and use code written in other files, let's check out what kind of mechanism ruby offer for organizing that code
- we've already learn that use can use __method__ to group together logical blocks of code
- these __method__ can be defining classes and use on __instantiated objects__
- but what if you have a bunch of __loosely related method__ that didn't really fit well into a class, or set of classes that you need to group together them self
- to do this, we use __module__
- __modules__ are not __classes__ : this means we can't create __instances__ of module
- modules provide organizational structure to the code, but the real power comes from : __namespaces__ and __mixins__
```ruby
module MartialArts
        def kung_fu
                return "Now I know kung-fu"
        end
end

class Person
        include MartialArts
end

class Panda
        include MartialArts
end

p = Panda.new
n = Person.new

puts p.kung_fu
puts n.kung_fu
```
- module method decoration

### library
A collection of code, likely organized into __multiple modules__, that can be reused by any program that imports it
- most programming languages come with __standard library__ which provide code to accomplish many common and even some uncommmon tasks
- ruby __standard library__ : collection of __multiple libraries__, come __built-in__ along with the __installation__ of the language, provide to program with code to do variety tasks
- libraries exist to do anything from reading, working with __csv files__ to sending emails to manipulate system logs directly 
- libraries code must be well tested, exercised and generally written in high standard of code quality : so using libraries is using the best of the best
- :: - identify accessing to class in module
> using libraries can really helpful, even without knowledge of low level details, you're able to create a simple scripts to send request to web server in couple of lines, easy peasy

### packages
- ruby gem package management system
- ruby gems : instead of distributing platform-dependent software, it distribute ruby program in library
- ruby gems use the standard format for distributing packages called __gem__
- these gems are hosted in gem __repository__ and can be installed for use by your scripts through the __gem command line tools__
- programmer usually use gems available on the public repository
- you can browse these at ruby gem site and install them using gem tool from you terminal
- to use package management system you first need to have ruby gem installed on your computer

### finding packages
many way to search for packages: 
- on the site
- gem query --remote --name-matches net-ping

### programming with files (manipulate files and directories)
read files :
- so far we've learn how we can get data into and out of your script
- gets : take user input
- puts , print : print to the screen
- but the terminal in screen is not the only way to work with data in a program
- your scripts can also use __files__ to read a large chunk of data
- or __write a result__ to a location on disk
- __working with file__ is such a common and __useful task__ in programming
- the most languages build the ability into the core set of features 
- provide funtionality in form of __file class__
- you can use the __instance of file class__ to __do all sort of things with files__
- reading, writing, moving, delete
```ruby
file = File.new("birthday_song.txt")
puts file.gets
file.close
```
- in this example, a new __file object__ aka __File handle__ is created and assigned to varible called _file_
- remember to __close__ file

writing files :
- write, append

directories:
- create, delete and browse
- Dir class : __entries__ method : return an arry, each element of which will be a file or subdirectory within the current directory
```ruby
contents = Dir.glob("**/*.txt")
contents.each do |entry|
        puts entry
end
```
> ** recursive , * wildcard

working with files :
- __change permissions__, __delete__, __rename__
- another ability file class provide : work with relative and absolute path

### scripting pipelines

#### intro to I/O streams
- we've seen bunch of ways to get information into and out of scripts
- we know that we can read and write files and accept input from the keyboard and print it to the screen
- but what's exactly going on behind the scene when we do this, how do ruby program connect to both the screen and keyboard?
- __I/O streams__ : the basic mechanism for performing input and output operations in Ruby scripts
- you can think of these streams as __pathway__ between your __program__ and sources of __input__ like keyboard and __output__ like screen
- I/O streams __aren't__ just for ruby program either
- when you run a system command on your terminal, __I/O streams__ are also been ultilized __connect__ that command to the terminal __input__, __output__
- this way you can __see the result__ of the command or even __pass the data__ interatively, if it support that functionality
- in this lesson we dig a little deeper into the concept of __I/O streams__
- especially __zoning in__ the standard or default stream that are found in most OS
- we'll see how to manipulate and redirect those streams, and how to use them writting scripts

#### Standard Streams
- most OS supply 3 different kinds of IO streams by default, each with __different purpose__

1. standard in
stdin : channel between __program__ and __source of input__, use in the form of text data from the keyboard
2. standard out
stdout : pathway between program in target output like display
3. standard error

### subprocess
#### running System Commands in Ruby
- net-ping
- sometimes its better to use terminal command in ruby script

#### scripting subprocess
- parent process : running script
- child process : when parent process run a external command
- parent process are __blocked__ when child process executing
- method : system
```
success = system("chmod", "777", "somefile.txt")
```
- the _system_ method will return __TRUE__ when the command that it's running returns a 0 exit status
- __False__ if the exit status is __non-0__
- remember in Unix-like OS, 0 exit status of child process usually indicate _success_, while a non-0 status generally indicate _failure_
- the __system__ method if we just want to run a command and determine whether or not it were successful 
- this can come in handy for system command without much useful output like _chmod_
- but if we want to capture the output of some external command, we need different strategy

#### backticks "`"
- another way a terminal command can be executed through a subprocess is by wrapping that command in backticks
- when external commands are executed through backticks, their output is __returned__ through the standard out stream instead of their __exit status__
```
[qvieth@localhost myconf]$ irb
irb(main):001:0> output = `ls`
=> "gnomesetting\ninit.vim\nkeymap.json\nREADME.md\nvimium.css\n"
irb(main):002:0> puts output
gnomesetting
init.vim
keymap.json
README.md
vimium.css
=> nil
irb(main):003:0>
```
- %x, $?
- silent failure

#### open3
- as we learned, silent failure can be dangerous for automation
- don't worry, ruby always find a way
- in this case, ruby find a solution to get both standerr, standout and return code from a finished subprocess without having to resolve to redirection
- introduce open3 module from the standard library
- multiple assignment : cool ruby feature let you assign value to multiple variables at once
``` ruby
require "open3"

stdout, stderr, status = Open3.capture3("ls","-z")
puts stdout
puts stderr
puts status.success?
```

#### when to use subprocesses
- if you're automating a 1 off, well-defined tasks where the speed of developing the solution is the biggest requirement, then using system command in subprocesses can help out of time
- if you're doing something more complex or long run : it's better to use __libraries , modules, gems__ provided by ruby before diciding to use subprocesses
- check this standard library and gem repository to see if the task you want to accomplish can be done with native ruby

#### subprocess summary
- we've explored some of the ways that you can use external terminal command to interface with underlying system in your script
- we focused on 3 method for acomplishing this : each with positive and negative :
    - if you want to run a system command and only need to know whether or not it succeeded, use __system__ method
    - if you want to quickly run a command and capture its standard output, use __backticks__, as long as you're ok with the script failing if the command doesn't succeed
    - if you need to capture both standout, standerr, and the __return status__, import the __open3__ module and use the __capture3__ method
- it's worth noting that's there other ways to run subprocesses in ruby what we haven't covered : fork,... look for more in processes ruby documentation

### writing script from the ground up
#### introduction
- by now you've seen how to extend the usefulness of your script by importing external code and using libraries, performed I/O operations with files and manipulated directories, run external commands using subprocesses and constructed I/O pipelines to process data ,combing with the coding technique introduced earlier, you've learned a lot about the tools you can use to create automation through scripting
- in this lesson, we'll pull together what we've learned so far to write the script from the group up
- we start with the task that we want to accomplish, do a little research on the subject and plan out what we want our code to look like
- then we dive in coding it up
- at the end of the lesson, we'll have the working script and hopefully demonstrate lots of the technique we've learned

#### problem statement
- imagine you're IT support specialist at a medium size company, your manager wants to do a security audit of the computers on the internal network
- and need to list all active IP adresses connected to it
- she give you a task of scanning the network and compiling this list of active adresses
- to determine if computer is connected to a network you can run a __ping__ command to send a package of data to a IP address using __ICMP__(internet control message protocol)
- ping all the computer on networks would be a painful task
- so we need to write a script to automatically ping each IP address on the network
- we should also generalize the script to be use on __any__ network. why?
- because if the infrastructure chaged later : like by adding another network or changing the setup of current one, our script could adapt and still be useful
- this example of using ping to scan local network is just illustrated
- other options might include viewing the active DHCP leases on the network (like by looking at the __/var/lib/dhcp/dhcp.leases__ file in a Unix-like system)
- this scan itself can be perform with specialized tool like __nmap__
- some machines in the network might also filter out __ICMP packages__, which mean the ping wouldn't able to discover 

#### research
- before write with ruby ask : how big is the network
- to-range

#### planning
2:48:00
need more knowledge in IT, net, IP commands
comeback later
