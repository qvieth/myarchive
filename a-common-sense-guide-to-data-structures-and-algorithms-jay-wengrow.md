# a common sense guide to data structures and algorithms - jay wengrow

## chapter 1 : why data structures matter
- the first metric : does the code actually work?
- there are numerous measures of code quality :
    - code maintainability
    - code efficiency
- CRUD
- measuring speed :
    * if you take away just 1 thing from this book, let it be this :
        - when we measure how 'fast' an operation takes
            - we do not refer to how fast the operations takes in term of pure time
            - but instead of how many steps it takes
    - **Measuring the speed** of an operation is also known as measuring its **time complexity**
    - speed - time complexity - efficiency -  performance -  runtime

- reading

## chapter 2 : why algorithms matter
- Code Implementation of ....algorithm
- With an array containing 100 values, here are the maximum number of steps each type of search would take:
    • Linear search: 100 steps
    • Binary search: 7 steps
- This pattern is unusually efficient: each time we double the data, the binary search algorithm adds just one more step
- graph time complexity function :
    - x : number of elements
    - y : number of steps
- binary search vs linear search
- insertion requires a search before the actual insertion
- insertion within an ordered array still remains slower than within a regular array, as the regular array’s insertion doesn’t require a search at all
- there isn't a single data structure or algorithm that is perfect for every situation
- In situations where you don’t anticipate the need to search the data much, only adding data, standard arrays may be a better choice because their insertion is faster

## chapter 3 : Big O Notation
- To help ease communication regarding time complexity
    - computer scientists have borrowed a concept from the world of mathematics
    - to describe a concise and consistent language around the efficiency of data structures and algorithms
- Big O: How Many Steps Relative to N Elements?
- graph time complexity function :
    - x : number of elements
    - y : number of steps
    - O(n) : given n elements, takes n steps
- Big O is originally a concept from mathematics, and therefore, it’s often described in mathematical terms

## chapter 4 : speeding up your code with big O
- 
