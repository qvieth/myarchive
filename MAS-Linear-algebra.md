# MAS Linear algebra
- solve system of equations -> best is matrix
- v, w : vector
- i,j,k : i-hat, j-hat, k-hat : unit vector = basis vector of x,y,z

## Contents

## 1. matrices, elements, and transpose
- A : matrix
    - m rows (like vector)
    - n columns
    - A is "m x n" matrix
    - a_12, a_22, a_{ij} : ... elements
- -> read m first (read like vector first)
- square matrix (rows = columns)
- matrices are = only if they are the same size and a_ij = b_ij
- A^T is the **transpose** matrix of A : rows and cols are swapped
- to optimize the power of computer -> study linear algebra

## 2. n-tuples and matrix arithmetic, part 1
- n-tuple :
- (x,y) : x, y pairs , ordered pairs , 2#s
- a set of n-numbers is called an [n-tuple](n-tuple)
- "[tuple](tuple)" means "ordered list" of numbers

## 3. n-tuples and matrix arithmetic, part 2
- u_1 = (1,0,-3)
- u_2 = (2,0,4)
- u_3 = (4,0,1)
- 3u_1 - 4u_2 + 3u_3 = ?
- -> write u_1 u_2 u_3 **in columns (like vector)**
    - [3,0,-9]-[8,0,16]+[12,0,3] = [7,0,-22]

## 4. matrix multiplication
- AB : A times B : defined only if :
    - the columns of A = rows of B
    - think of matrix vector multiplication -> the same

## 5. the vector dot product
- v = 3i + 1j + 2k
- w = 2i + 2j + 1k

## 6. special matrices
- identity matrix : I_n
- I_2 = [[1,0],[0,1]]
- I_3 = [[1,0,0],[0,1,0],[0,0,1]]

## 7. norm of a vector
- vector norm : magnitude of a vector
- magnitude(length) and direction

## 8. unit vectors in any direction
- the concept of unit vector being a vector has the length of 1
- when we talk about vector
    - we talk about the important unit vector i,j and k
    - vectors that point along the x-axis, y-axis, and z-axis
- unit vectors - i,j,k vectors with length 1

## 9. vector addition and triangle inequalities
- add vectors : graphically


## 10. orthogonal and orthonormal vectors
- looks like these are used in physics
- A.B = ||A||.||B||.\cos \theta
    - ||A|| : magnitude of A
    - orthogonal = perpendicular

- from Khan academy :
- orthonormal = orthogonal + normalized
- `B = {v_1,v_2,...,v_k}`
    - **orthonormal set** B
    - all the vectors in B have length 1
    - all the vectors are orthogonal to each others
        - v_{i} . v_{j} = { 0 for i !=j , 1 for i = j}
    - normal => they all have been "normalized"

## 11. solve systems of equations with row reduction, part 1
- use matrices to solve systems of equations with something that we call row reduction

- **CONCEPTS OF SOLVING SYSTEM OF EQUATIONS**
    - => one of the most important reasons
        - that anybody learns about matrices
    - which means you have 3 equations and 3 unknowns
    - or 6 equations and 6 unknowns
- you learn in basic algebra how to solve those ystems :
    - you might use substitution
    - you might try to graph them and see where they intersect
    - or whatever, which is fine for small systems
    - but for large systems with four or five variables
    - it's very difficult to apply substitution of graphing methods
    - to get to the answer
    - so matrix methods can be applied to any systems of equations
    - any linear system of equations
    - where we have multiple unknowns and multiple equations

## 12. solve systems of equations with row reduction, part 2

## 16. homogeneous systems of equations
## 19. solve systems of equations with inverse matrices
- AX = B
- A^{-1}B = X
