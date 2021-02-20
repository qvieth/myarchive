# Essence of linear algebra
https://www.youtube.com/watch?v=fNk_zzaMoSs&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab
- v,w : vector
- x,y,z : variable vector
- i,j,k : i-hat,j-hat,k-hat : basis vector
- A : matrix
- point - can be think as vector and vice versa

- keep the grid line parallel and evenly space
- v = [x,y,z] = xi + yj + zk
- if the calculation has clear procedural, or proofs, they have computer software for calculating them

## Contents

- [Essence of linear algebra](#Essence of linear algebra)
    - [chapter 1. vectors what even are they?](#Essence of linear algebra#chapter 1. vectors what even are they?)
    - [**chapter 2. linear combinations, span, and basic vectors](#Essence of linear algebra#**chapter 2. linear combinations, span, and basic vectors)
    - [***chapter 3. linear transformations and matrices](#Essence of linear algebra#***chapter 3. linear transformations and matrices)
    - [chapter 4. matrix multiplication as composition](#Essence of linear algebra#chapter 4. matrix multiplication as composition)
    - [chapter 5. three-dimensional linear transformation](#Essence of linear algebra#chapter 5. three-dimensional linear transformation)
    - [chapter 6. the determinant](#Essence of linear algebra#chapter 6. the determinant)
    - [chapter 7. inverse matrices, column space, rank and null space](#Essence of linear algebra#chapter 7. inverse matrices, column space, rank and null space)
    - [chapter 8. nonsquare matrices as transformations between dimensions](#Essence of linear algebra#chapter 8. nonsquare matrices as transformations between dimensions)
    - [chapter 9. dot products and duality](#Essence of linear algebra#chapter 9. dot products and duality)
    - [chapter 9. cross products](#Essence of linear algebra#chapter 9. cross products)
    - [chapter ............](#Essence of linear algebra#chapter ............)
    - [chapter 14. eigenvectors and eigenvalues](#Essence of linear algebra#chapter 14. eigenvectors and eigenvalues)
    - [chapter 15. abstract vector spaces](#Essence of linear algebra#chapter 15. abstract vector spaces)

## chapter 1. vectors what even are they?
- the fundamental, root-of-it-all building block
    - for linear algebra -> **vector**
- linear algebra topics tend to revolve around :
    - vector addition
    - scalar multiplication
- 3 perspective :
    - physics : length + direction
    - cs : list(vector) + length of list(dimensional)
    - math : ignore this for now..
- origin - coordinate - adding vectors

## **chapter 2. linear combinations, span, and basic vectors
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
    - it's called a **linear combination** of those two vectors
    - av + bw 
        - a,b : scalar
        - v,w : vector

- if you let 1 scalar fixed and others range -> the tip of resulting vectors draw a straight line
- if you let both scalars range freely -> the tip of resulting vector react all point in a plane
- however, in the unlucky case where two original vectors happens to line up
    - the tip of the resulting vector is limited to just this single line passing through the origin 
    - another possibilities : both your vectors could be zero, in which case you'd just be stuck at the origin
- remember how i said that linear algebra revolves around vector addition and scalar multiplication

* **the "span" of v and w**
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

## ***chapter 3. linear transformations and matrices
> unfortunately, no one can be told what the matrix is, you have to see it for yourself - morpheus
- important : the idea of linear transformation and its relation to matrices
- linear transformation
    - transformation : fancy word for [function](function)
        - the word 'transformation' suggests that you think using movement
    - **take in a vector as input and split out another vector**
    - linear transformation :
        - origin remain fixed
        - lines remain lines 
        - grid lines remain **parallel** and **evenly spaced**
- it turns out that you only need to record where the two basis vectors, i-hat and j-hat
    - each land and everything else will follow from that
- a linear transformation is completely determined
    - by where it takes the **basis vectors** of the space

- v = -1i + 2j
    - transformed v = -1(transformed i) + 2(transformed j)
    - = -1[1,-2] + 2[3,0]
    - ... video at p5.17

- matrix vector multiplication

## chapter 4. matrix multiplication as composition
- (AB)C = A(BC)
- think composition matrix as composition function f(g(x)) :
    - calculate g(x) first then f(x)

## chapter 5. three-dimensional linear transformation

## chapter 6. the determinant
- the 'determinant' of a transformation

## chapter 7. inverse matrices, column space, rank and null space
- i'm not going to talk about the methods for actually computing these things
- and some would argue that that's pretty important
    - **gaussian elemination and row echolon form**
    - in practice there's computer software for calculating this anyway

- by now you already have a hint for
    - how it's used in **describing the manipulation of space**
    - which is useful for things like computer graphics and robotics
* but on of the main reason that linear algebra is more broadly applicable and required for just about any technical discipline
    * is that it lets us solve certain **systems of equation** 

- when i say 'system of equations'
    - i mean you have a list variables, things you don't know
    - and a list of equations relating them
    - all variables on the left, constant on the right
    - zero coefficient when variable doesn't show up
    - this is linear system of equation

- A^[-1}A
    - the transformation that does nothing is called the 'identity transformation'
- under the light of linear transformation :
    - [inverse matrices](inverse-matrices)
    - [rank](rank) 
    - [column space](column-space)
    - [null space](null-space)

## chapter 8. nonsquare matrices as transformations between dimensions
rewatch

## chapter 9. dot products and duality
- [ ] dot product
    - [ ] between two vectors of the same dimension
- [ ] to think about the dot product between two vector v and w
- [ ] imagine projecting w onto the line that passes through the origin and the tip of v
- [ ] duality
rewatch

### chapter 8 and 9 seem important : has some relevance to linear regression
- the dual of linear transformation from space to one dimension
- dot product between 2 vector is like linear tranformation of 1 vector with other as matrix

## chapter 10. cross products
- v X w =  area of the parallelogram
- cross product of two 3d vectors
- use determinant
- there's a reason for that notational trick
- to understand the idea, use the duality
- right hand rules
rewatch

## chapter 11. cross product in the light of linear transformation
- as a quick reminder, the idea of duality is
- anytime you have a linear transformation from some space to the number line
- it's associated with a unique vector in that space
- in the sense that performing the linear transformation
- is the same as taking a dot product with that vector
- numerically, this is because one of those transformations
- is described by a matrix with just one row
- where each column tells you the number that each basis vector lands on
- 2:41 -> IMPORTANT -> insight for remmeber duality and dot product

## chapter 12. crammer's rule, explained geometrically
- cross product, dot product -> let the computer handle it
- and while it's true that number-crunching is something we typically leave to the computers
- digging into some of these computational methods
- is a good litmus test for whether or not you
- actually understand what's going on
- since this is really where the rubber meets the road
- here i want to describe the geometry behind a certain method
- for computing solutions to these systems
- known as Cramer's rule
- prerequisites :
    - determinant
    - dot products, duality
    - inverse matrices, rank, null space
- i should say up front that **Crammer's rule**
    - is not the best way for computing solutions
    - to linear systems of equations
    - **gaussian elimination**, for example, will always be faster
    - so why learn it?
- THINK OF THIS AS A SORT OF CULTURAL EXCURSION
- it's a helpful exercise in deepening your knowledge of the theory of these systems
- wrapping your mind around this concept will help consolidate ideas from linear algebra
    - like the determinant and linear systems, by seeing how they relate to each other 
    - also, from artistic standpoint, the ultimate result is just really pretty to think about
    - much more so that gaussian elimination

## chapter 13. change of basis
- think of coordinates as scalars
- anyway to translate between vectors and sets of numbers
- is called a coordinate system
- and the two special vectors, i-hat, j-hat are called the [basis vector](basis-vector) of our standard coordinates system
- different basis vectors - like different languages
- how to translate a matrix

## chapter 14. eigenvectors and eigenvalues
- https://www.youtube.com/watch?v=PFDu9oVAE-g&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab&index=14
- one of those topics that a lot of students find particularly unintuitive
- vector that remains fixed in place after transformation
- Av = \lambda v
    - Av : matrix vector multiplication
    - eigenvetors - v
    - eigenvalues - lambda
    - det(A - \lamda I) = 0
- diagonal matrix
- rewatch
- many insight
- 

## chapter 15. abstract vector spaces
- linear transformations = linear operators
- formal definition of linearity :
    - additivity : L(v+w) = Lv + Lw
    - scaling : 
- derivative is linear
- LET'S DESCRIBE THE DERIVATIVE WITH MATRIX
- axioms for adding and scaling vector
- rules your result in terms of these axioms
- vector spaces?
    - **set** of objects called vectors
- abstractness is the price of generality
