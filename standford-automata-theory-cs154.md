# standford automata theory cs154
## 1.1.1 course outline and motivation
- some of the ideas we are going to learn :
    - regular expressions are used in many systems
    - finite automata model protocols, electronic circuits
    - context-free grammars are used to describe the syntax of
        - essentially every programming language
        - not forget their important role in describing natural languages
    - and DTD's taken as a whole, are really CFG's
    - when decide solutions to real problems, we often confront the
        - limitations of what software can do
        - **undecidable** things - no program whatever can do it
        - **intractable** things - there are programs but no fast programs
    - we will learn how to deal formally with discrete systems
        - proofs: you never really prove a program correct, but you need to think why a tricky technique really works
    - we'll gain experience with abstract models and constructions
        - models layered software architectures

## 1.2.2 informal introduction to finite automata
- TENNIS AUTOMATON
- what is a finite automation :
    - a formal system
    - remember only a finite amount of information
    - information represented by its state
    - state changes in response to inputs
- why study finite automata :
    - used for both design and verification of circuits and communication protocols 
    - used for many text-processing applications
    - an important component of compilers
    - describes simple patterns of events, etc..
- transition diagram for finite automaton
- the jobs of an automaton is to process strings of input symbols or input strings
- acceptance of inputs
    - given a sequence of inputs(input strings), start in the start state and follow the transition from each symbol in turn 
    - input is accepted if you wind up a final(accepting) state after all inputs have been read
- the job of a finite automaton is to process strings of inputs and accept or reject them
- language of an automaton
    - the set of strings accepted by an automaton A is the **language** of A
    - denoted L(A)
    - different sets of final states -> different languages

## 1.3.3 deterministic finite automata
- RECONIZING STRINGS END IN 'ING' AUTOMATON
* PROTOCOL FOR SENDING DATA AUTOMATON
- deterministic : means that there's unique transition for every state and input symbol
- alphabets, strings, and languages transistion graphs and tables - some proof techniques
- DFA :
    - a formalism for defining languages, consist of :
        1. a finite set of **states** (Q, typically)
        2. an **input alphabet** ($\sigma$, typically)
        3. a **transition function** ($\delta$, typically)
        4. **start state** (q0, in Q, typically)
        5. a set of **final(accepting) states**(F ..don't know what is this symbol.. Q, typically)
- graph representation of DFA's
    - node = states
    - arc represent transition function
        - arc from state p to state q labeled by all those input symbols that have transitions from p to q
