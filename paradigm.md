# paradigm

- [imperative](imperative)
     - [object](object)
- [declarative](declarative)
     - [function](function)
- ooo

- [wiki : programming paradigm](https://en.wikipedia.org/wiki/Programming_paradigm)
- imperative in which the programmer instructs the machine how to change its state
     - procedural which groups instructions intro procedures
     - object-oriented which groups instructions with the part of the state they operate on
- declarative in which the programmer merely declares properties of the desired result, but not how to compute it
     - functional in which the desired result is declared as the value of a series of function applications,
     - logic in which the desired result is declared as the answer to a question about a system of facts and rules,
     - mathematical in which the desired result is declared as the solution of an optimization problem
     - reactive in which the desired result is declared with data streams and the propagation of change
- For example,
- languages that fall into the [imperative](imperative) paradigm have two main features:
     - they **state the order in which operations occur**
          - with constructs that explicitly control that order
     - and they **allow side effects**
          - in which state can be modified at one point in time within one unit of code
          - and then later read at a different point in time inside a different unit of code
          - the communication between the units of code is not explicit
     - Meanwhile, in [object oriented](object-oriented) programming
          - code is organized into objects that contain a [state](state)
          - that is only modified by the code that is part of the object
          - **Most object-oriented languages are also imperative languages**
- In contrast, languages that fit the [declarative](declarative) paradigm
     - do not state the order in which to execute operations
     - Instead, they supply a number of available operations in the system
          - along with the conditions under which each is allowed to execute
     - The implementation of the language's [execution model](execution-model) tracks
          - which operations are free to execute and chooses the order independently
     - [wiki : comparison of multi paradigm programming languages](https://en.wikipedia.org/wiki/Comparison_of_multi-paradigm_programming_languages)

# FLEETING NOTES

- [anjana vakil - learning functional programming with javascript](https://www.youtube.com/watch?v=e-5obm1G_FY)
- https://www.quora.com/How-many-different-programming-paradigms-are-there-and-what-are-they
- John Colagioia : Why different paradigms? Because certain problems fit into different paradigms more easily
     - Simulating physical things is an almost inherently object-oriented process
     - Applying transformations to separate data sets is almost inherently functional
     - Joining components is dataflow
- paradigm : functional programming(everything is function) - procedural programming - oop(everything is object)
     - pure function(take input, use that compute output)
     - avoid side effects : return not console.log
     * we need higher order function in order to avoid some of the tricks that we're used to using from other paradigms
     * don't iterate(for, while go over lists)
     * instead in functional style, we might
          - use higher-order functions like map or reduce or filter
          - which often take as an input not only the list that you want to do something to in some way
          - but also a function that then you're going to apply to it
