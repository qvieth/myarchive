# Essence of linear algebra
https://www.youtube.com/watch?v=fNk_zzaMoSs&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab

## chapter 1. vectors what even are they?
- the fundamental, root-of-it-all building block
    - for linear algebra is the vector
- linear algebra topics tend to revolve around :
    - vector addition
    - scalar multiplication
- 3 perspective :
    - cs : list(vector) + length of list(dimensional)
    - physics : length + direction
    - math : ignore this for now..

## **chapter 2. linear combinations, span, and basic vectors
- i-hat and j-hat : **basis vectors** of the xy coordinate system
- what if we chose different basis vector? : v and w 
    - => gotten a new coordinate
- anytime we describe vectors numerically
    - it depends on an implicit choice
    - of what basis vectors we're using
- the '**span**' of v and w is the set of all their **linear combinations**
* linearly dependent :
    - can remove 1 vector without reducing the span
    - another way of phrasing :
        - one of the vectors can be expressed as
        - a linear combination of the others
        - since it's already in the span of the others
            - u = av + bw
* linear independent
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
- linear transformation :
    - transformation : fancy word for [function](function)
        - the word 'transformation' suggests that you think using movement
    - linear transformation : origin remain fixed, lines remain lines : can think as keep grid lines remain **parallel** and **evenly spaced**
        - think of grid return parallel and evenly spaced
- it turns out that you only need to record where the two basis vectors, i-hat and j-hat
    - each land and everything else will follow from that
- a linear transformation is completely determined
    - by where it takes the **basis vectors** of the space

## chapter 4. matrix multiplication as composition
- (AB)C = A(BC)

## chapter 5. three-dimensional linear transformation

## chapter 6. the determinant
- the 'determinant' of a transformation

## chapter 7. inverse matrices, column space and null space
- the transformation that does nothing is called the 'identity transformation'
- under the light of linear transformation :
    - inverse matrices
    - column space
    - rank : number of dimensions in the output of a transformation
    - null space

## chapter 8. nonsquare matrices as transformations between dimensions
rewatch
## chapter 9. dot products and duality
- [ ] dot product
- [ ] duality
rewatch
## chapter 9. cross products
rewatch

## chapter ............

## chapter 14. eigenvectors and eigenvalues
- eigenvetors - rotation
- eigenvalues - lambda

## chapter 15. abstract vector spaces
