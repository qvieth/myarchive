# set theory
- https://en.wikipedia.org/wiki/Set_theory
    - [mathematical object](https://en.wikipedia.org/wiki/Mathematical_object)
    - [cartesian product](https://en.wikipedia.org/wiki/Cartesian_product)
- b : discrete math Susana S
- b : introduction to algorithm cormen

## b.1 sets
- : such that
- |A| : cardinality(size) of A
- a set is a collection of distinguishable objects
    - called members or elements 
- DeMorgan's laws
- cartesian product
    - A x B = {(a,b) : a \in A and b \in B}

## b.2 relations
- **binary relation** : a binary relation R on two sets A and B is a subset of the cartesian product A x B
- if (a,b) \in R, we sometimes write a R b
- when we say that R is a binary relation on set A, we mean that R is a subset of A x A
- for example :
    - the 'less than' relation on the natural numbers is the set {(a,b) : a,b \in N and a < b}
    - an n-ary relation on sets A_1 , A_2,..., A_n is a subset of A_1 x A_2 x ... x A_n
    - a binary relation R \subset A x A is **reflexive** if
        - a R a 
        - for all a \in A 
        - for example, '=' and '\leq' are reflexive relations on N, but '<' is not
    - the relation R is **symmetric** if 
        - a R b implies b R a 
        - for all a,b \in A
        - for example, '=' is symmetric, but '<' and '\leq' are not
    - the relation R is **transitive** if 
        - a R b and b R c imply a R c
        - for all a,b,c \in A
        - for example, the relation '<','\leq' and '=' are transitive, but the relation R = {(a,b) : a,b \in N and a=b-1} is not, since 3 R 4 and 4 R 5 do not imply 3 R 5
    - a relation that is reflexive, symetric and transitive is an **equivalence relation**
        - for example, '=' is an equivalence relation on the natural numbers, but '<' is not
        - if R is an equivalence relation on set A, then for a \in A, the **equivalence class** of a is the set [a] = {b \in A : a R b}
        - that is, the set of all elements equivalence to a
        - for example, if we define R = {(a,b) : a,b \in N and a + b is an even number}
        - then R is an equivalence relation
        - since a + a is even (reflexive)
        - a + b is even implies b + a is even (symetric)
        - and a + b is even b + c is even imply a + c is even (transitive)
        - the equivalence class of 4 is [4] = {0,2,4,6,...}
        - and the equivalence class of 3 is [3] = {1,3,5,7,...}
        - a basic theorem of equivalence classes is the following
            - theorem B.1 (an equivalence relation is the same as a partition)

## b.3 functions


## b.4 graphs


## b.5 trees
