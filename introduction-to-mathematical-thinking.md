# introduction to mathematical thinking
- https://www.coursera.org/learn/mathematical-thinking
```lecture3
* think of implies as :
    - superset => subset
```
- university math :
    - understanding not doing
    - not about right or wrong, but about how to think about the problems
    - why you get right or wrong is important
    - please read the document called BACKGROUND READING

## 1. introductory material
- read the BACKGROUND READING
- what kinds of patterns are studied in topology?
    - -> closeness
- in the nineteenth century, the primary focus in math became
    - -> concepts and relationship
- according to keith devlin, the most valuable mathematical ability in today's advanced nations is
    - -> adapt old methods or develop new ones
- the secret of this entire course is reflection, not completion
- which of the following was a major change in the nature of mathematics in the 19th century?
    - -> the main focus mathematics shifted from developing and using procedures to analyzing properties and relationships
    - mathematics became more abstract
* the main thing to realize is that a lot of what we do probably won't seem like doing math, since the focus is on how to think mathematically, not how to apply standard techniques to solve problems
* modern pure mathematics is primarily concerned with **precise statements** about mathematical objects
    * **MATHEMATICAL OBJECTS ARE THINGS LIKE INTEGERS, REAL NUMBERS, SETS, FUNCTIONS, ETC.**
* which one of these are some mathematical statements :
    * [X] there are infinitely many prime numbers
    * [ ] for every real number a, the equation x^2 + a = 0 has a real root
    * [X] \sqrt{2} is irrational
    * [X] if p(n) denotes the number of primes less than or equal to the natural number n, then as n becomes very large, p(n) approaches n/log_{e}{n}
- not only are mathematicians interested in statements like these, they are above all, interested in knowing which statements are true, and which are false
- the truth or falsity in each case is demonstrated not by observation or measurements or experiment, as in the natural sciences, but **by a proof**
- in this course, we look at some different ways of proving statemen
- SLEEP -> comback 12:50

## 2. logical combinators
- exclusive or
    - a > 0 or the equation x^2 + a = 0 has a real root 
- inclusive or 
    - ab = 0 if a = 0 or b = 0 
- in mathematics, 'or' means inclusive or
- A : and - conjunction
- v : or - disjunction - the constituents are called disjuncts
- advanced mathematics is very abstract, and the language is the only means we have to access it and decide what is true and what is false
- negate the subject of the sentence - false - true

## week 2
### lecture 3 - implification (conditional)
- $\phi$ implies $\psi$
- => : aka conditional
    - \phi : antecedent
    - \psi : consequent
- the truth of $\psi$ **follows** from the truth of $\psi$
- implication involves causality
- implication has a **truth part** and a **causation part**
- implication = conditional(truth part) + causation
    - conditional : define entirely in terms of truth values 
    - causation : leave to philosopher
* think of implies as :
    - **superset => subset**
- example for 'phi implies psi'
    - if phi then psi 
    - phi is sufficient for psi
    - phi only if psi
    * psi if phi
    * ...
### lecture 4 - equivalence (biconditional)
- implies each other
- \phi <=> \psi : phi biconditional psi
    - it's an abbreviation of (\phi => \psi) and (\psi => \phi)
- phi <=> psi if they are both true or both false
- central notion in mathematics
- one way to show two statement phi and psi are equivalent
    - is to show they have the same truth tables
- "phi is equivalent to psi" is itself equivalent to
    - phi is necessary and sufficient for psi
    - phi if and only if psi

### lecture 5 - quantifiers
- quantifiers
    - there exists ...
    - for all ...
#### existential quantifier
    - $\exists$
    - there is an object x having property P
    - \exists x[x^2+2x+1=0]
#### universal quantifier
    - $\forall$
- ...
- university level : less material, less doing, focus on more depth, more thinking, slower progress
- this is a proof of indirect proof

* IMPORTANT example : 'one american dies of melanoma almost every hour'
    * \exists A \forall H [A dies in hour H]
        * exist american such that for every hour [A dies in hour H]
* what the writer meant was :
    * \forall H \exists A [A dies in hour H]

### SUPLEMENT : how to read mathematical formulas
- convention :
    1. quantifiers bind whatever comes next
    2. so does negation

## lecture 9 : number theory
- 9B : **DIVISIBILITY**
- think of divisibity of animation that the numbers are broken down into many same sum
- if division of a by b produce a remainder r = 0
    - we say a is **divisible** by b
    - notation : b|a : a is divisible by b
    - b|a : relationship between a and b : TRUE OR FALSE
- a **prime number** is an integer p>1 that is divisible only by 1 and p
- the following are TRUE :
    - 9|0
    - 1|1
    - 7|(-42)
    - (-7)|49
- BASIC PROPERTIES OF DIVISIBILITY
- FUNDAMENTAL THEOREM OF ARITHMETIC
- DIFFERENT KINDS OF PROOFS

## lecture 10A : real analysis 1
- completeness property
