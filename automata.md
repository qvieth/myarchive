# automata

- [cellular automata](cellular-automata)

- A finite-state automaton A **consists of five objects**:

     1. A finite **set** I, called the **input** alphabet, of input symbols
     2. A finite **set** S of **states** the automaton can assume
     3. A designated state s 0 called the **initial state**
     4. A designated set of states called the set of **accepting states**
     5. A next-state **function** N : S X I -> S that associates a “next-state” to each
           - ordered pair consisting of a “current state” and a “current input”

     - https://www.youtube.com/watch?v=SuoDmiJ6zLQ : insight for finite state automata and regular expression
     - definition page 843

     * all regular expression can be represented as **state transition diagram**
     * https://people.cs.clemson.edu/~goddard/texts/theoryOfComputation/5.pdf

     - Each piece of input to a finite-state automaton leads to a change in the state of the automaton
