# paradigm

-   [anjana vakil - learning functional programming with javascript](https://www.youtube.com/watch?v=e-5obm1G_FY)

# FLEETING NOTES

-   https://www.quora.com/How-many-different-programming-paradigms-are-there-and-what-are-they
-   John Colagioia : Why different paradigms? Because certain problems fit into different paradigms more easily
    -   Simulating physical things is an almost inherently object-oriented process
    -   Applying transformations to separate data sets is almost inherently functional
    -   Joining components is dataflow
-   paradigm : functional programming(everything is function) - procedural programming - oop(everything is object)
    -   pure function(take input, use that compute output)
    -   avoid side effects : return not console.log
    *   we need higher order function in order to avoid some of the tricks that we're used to using from other paradigms
    *   don't iterate(for, while go over lists)
    *   instead in functional style, we might
        -   use higher-order functions like map or reduce or filter
        -   which often take as an input not only the list that you want to do something to in some way
        -   but also a function that then you're going to apply to it
