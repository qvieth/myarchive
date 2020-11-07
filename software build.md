# software build
- build is the process of converting __source code__ files into standalone software __artifact(s)__ that can be run on a computer, or the result of doing so  
- build is the process of creating the application program for a __software release__ :
    1. Fetching the code from the __source control repository__
    2. __Compile__ the code and __check__ the dependencies/modules
    3. Run the __automated unit test__
    4. Link the __libraries, code, files__, etc accordingly.
    5. Once successfully passed, Build the __artifacts__ and store them.
    6. Archive the build __logs__
    7. Send the notification emails.
## Functions
- Building software is an end-to-end process that involves many distinct functions
- Some of these functions are described below.

### Version control
- The version control function carries out activities such as __workspace creation__ and __updating, baselining__ and __reporting__
- It creates an environment for the build process to run in and captures metadata about the inputs and outputs of the build process to ensure repeatability and reliability
- Tools such as Git, AccuRev or StarTeam help with these tasks by offering tools to tag specific points in history as being important, and more

### Code quality
- Also known as static program analysis/static code analysis this function is responsible for checking developers have adhered to the seven axes of code quality: comments, unit tests, duplication, complexity, coding rules, potential bugs and architecture & design
- Ensuring a project has high-quality code results in fewer bugs and influences nonfunctional requirements such as maintainability, extensibility and readability, which have a direct impact on the ROI for a business

### Compilation
- This is only a small feature of managing the __build process__
- The __compilation__ function turns source files into directly executable or intermediate objects
- Not every project will require this function
- While for simple programs the process consists of a single file being compiled, for complex software the source code may consist of many files and may be combined in different ways to produce many different versions

### Build tools
- The process of building a computer program is usually managed by a __build tool__, a program that coordinates and controls other programs
- Examples of such a program are __make__, Gradle, Meister by OpenMake Software, Ant, Maven, Rake, SCons and Phing
- The build utility typically needs to compile the __various__ files, in the correct order
- If the source code in a particular file has not changed then it may not need to be recompiled (may not rather than need not because it may itself depend on other files that have changed)
- Sophisticated build utilities and linkers attempt to refrain from recompiling code that does not need it, to shorten the time required to complete the build
- A more complex process may involve other programs producing code or data as part of the build process 
