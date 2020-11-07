# build automation
- the process of automating the creation of [software build](software build) 
- and the associated processes including: __compiling__ computer source code into binary code, __packaging__ binary code, and __running automated tests__

## overview
- Historically, build automation was accomplished through [makefiles](https://en.wikipedia.org/wiki/Makefile) 
- Today, there are two general categories of tools:
    - Build-automation __utility__ :
         - This includes utilities like Make, Rake, CMake, MSBuild, Ant, Maven or Gradle (Java) etc
         - Their primary purpose is to generate __build artifacts__ through activities like compiling and linking source code.
    - Build-automation __servers__ :
        - These are general __web based tools__ that __execute build-automation utilities__ on a __scheduled or triggered basis__
        - a __continuous integration__ server is a type of __build-automation server__
