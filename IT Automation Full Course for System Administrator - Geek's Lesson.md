[# IT Automation Full Course for System Administrator - Geek's Lesson](https://www.youtube.com/watch?v=ce434nD79nU)
IT Support Professional Certificate

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
### ruby
- puts 'hello world'
- print 'hello world'
- __data types__: string, integer, float, boolean
- __operators__ : arithmetic && comparison && bitwise && assignment && logical && dot && double colon : remainder modulus, greater, smaller, equal ==,not equal !=, and &&, or ||, not !
- __expressions and numbers__
-  __variables__: valid && invalid: name must start with letter or underscore

### system programming
#### flow control with branching
- the ability of a program to alter its execution sequence is called __branching__ or __flow control__
- it's a key component to make your script and automation useful
- you're often use the concept of branching in your everyday life : cold => wear jacket, rain => use umbrella
- in your scripts, you can also instruct computer to make decision based on inputs, so that it's __tailor made__ to you needs
- let's imagine that you would've given a task of writting a program that can decide if a person was old enough to vote
- __if elseif else end__ 
 
#### branching summary
- using branching to determine the flow of your program
- anytime your program needs to make a decision, you can specify its __behavior__ with a __branching statement__

#### object orientation: concepts to code
- think of how to describe an apple to a computer: using just __variables__ and __expressions__
- ruby follow OOP: __model concepts__ using __classes__ and __objects__
- 1:02:33
