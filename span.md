# span
- i-hat and j-hat : [basis vectors](basis-vectors) of the xy coordinate system
- by framing our coordinate system in terms of these two special basis vectors
- it raise the question :
- what if we chose different basis vector? : v and w 
    - => gotten a new coordinate
```
* anytime we describe vectors numerically
    - it depends on an implicit choice
    - of what basis vectors we're using
```
* so anytime that you're scaling two vectors and adding them :
    - it's called a [linear combination](linear-combination) of those two vectors
    - av + bw 
        - a,b : scalar
        - v,w : vector

- if you let 1 scalar fixed and others range -> the tip of resulting vectors draw a straight line
- if you let both scalars range freely -> the tip of resulting vector react all point in a plane
- however, in the unlucky case where two original vectors happens to line up
    - the tip of the resulting vector is limited to just this single line passing through the origin 
    - another possibilities : both your vectors could be zero, in which case you'd just be stuck at the origin
- remember how i said that linear algebra revolves around vector addition and scalar multiplication

* the "[span](span)" of v and w
    - is the set of all their **linear combinations**
    * is basically a way of asking :
        - what are **all the possible vectors you can reach**
        - using only these two fundamental operations

- this is a good time to talk about how people commonly think about vectors as points
    - it gets really crowded to think about a whole collection of vectors sitting on a line
    - so when dealing with collections of vectors like this
    - it's common to represent each one with just a point in space (its tail still at origin)
    - that way, if you want to think about every possible vector whose tip sits on a certain line, just think about the line itself
- when 2 vectors line up, their span is just a line

* [linearly dependent](linearly-dependent) :
    - can remove 1 vector without reducing the span
    - another way of phrasing :
        * one of the vectors can be expressed as
        * a linear combination of the others
        - since it's already **in the span of the others**
            - **u = av + bw**

* [linear independent](linear-independent)
    - w != av
```
* EXTREMELY IMPORTANT :
* Technical definition of basis
    * the basis of a vector space is
    * a set of linear independent vectors
    * that span the full space
* another important note | 9:51
    * vector v w u are independent if the only solution to
    * av + bw +cu = 0 is a=b=c=0
* for teaching purpose, it is more intuitive to think about how anyone of them is outside the span of the other two
```


