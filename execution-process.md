# execution process

- Prior to execution, a program must first be written
     - This is generally done in [source code](source-code)
- which is then compiled at [compile time](compile-time)
     - (and statically linked at [link time](link-time)) to an executable
- This executable is then **invoked**, most often by an operating system
     - which loads the program into memory ([load time](load-time))
     - possibly performs [dynamic linking](dynamic-linking)
     - and then begins execution by moving control to the [entry point](entry-point) of the program
     - all these steps depend on the [Application Binary Interface](Application-Binary-Interface) of the operating system
- At this point execution begins and the program enters [run time](run-time)
     - The program then runs until it ends, either normal termination or a crash
