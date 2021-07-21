# C

- [Cpp](Cpp)
- build your own x

> you don't understand a thing unless you program it

- good source from snap token
     - https://viewsourcecode.org/snaptoken/ -> kilo text editor in C
     - https://viewsourcecode.org/snaptoken/similarTutorials.html -> similar tutorials
- [how can i learn dsa in c](https://www.quora.com/How-can-I-learn-Data-Structure-and-Algorithm-in-C-language)
     - I would start with writing the basics from scratch in C:
          - Data Structures
          - vector
          - linked list
          - binary search tree
          - hash table
          - adjacency matrix
          - adjacency list
     - Algorithms
          - ...
- [Caleb Curry](Caleb-Curry)
- https://www.youtube.com/watch?v=YrVT09OS7VM&list=PL_c9BZzLwBRJVJsIfe97ey45V4LP_HXiG&index=18
- Data Structures and Algorithms in C
     - So there are 2 things, I want to learn Data Structures and Algorithms
     - and want to implement them in C language
     - So I should know the C language well, specially what requires for implementation
     - I would suggest you to have good understanding of pointers and pointer to structure
     - tell me how did you
     - Now come to Data Structures and Algorithms, we have to understand variety of Data Structures and Algorithms
     -    - Algorithm Analysis, Linked List, Stack & Queue, Tree, Graph, Sorting, Searching and Hashing
     - They are not related to any language. So understand the concepts well and then implement it in C language
- ===BIG IDEA=== :
- blackbox-containerized knowledge <- BID IDEA think about RISC chips when learning hardware Caleb Curry
     - = scope the knowledge
     - combine with the model :
- Caleb Curry - computer science : 4 layer :

```
    | user         |
    | applications |
    | OS           |
    | hardware     |
```

- between each of these layers is interface(how each layer communicate to each other)
- ===END OF BIG IDEA===
- static : can't be changed
- dynamic : can be changed

- [Caleb Curry - C programming tutorials](https://www.youtube.com/playlist?list=PL_c9BZzLwBRKKqOc9TJz1pP0ASrxLMtp2)
- function : group instruction into one
- anonymous => statement vs expression => memory vs calculation => learn C to grasp these concepts
- function -> call -> main ()
- end of function have return => many function can call our function
- expression : anything that can be evaluated (to 1 value)

```c
int x;
x = 10;
int y = x/5;
```

- **declaration** : int x
- **initialization** : x = 10
- expression : x/2
- statement : y = x/2
- sequence of characters
- data types :
     - **primitive** - smallest data type - indivisible - atomic - building blocks
     - **complex** - struct
     - float becomes double when format to %f
- **scientific notation** : 24000 -> 2.4 \* 10^4
     - in C : `2.4e4`
- **conversion character** :
     - `%f` - decimal notation
     - `%e` - scientific notation
     - `%g` - computer decides : < -4 | > 5
     - `%lf`
- &dogs : **address of** dogs - address operator
- **char** - character -> 'single quotes'
- **character set** : allowed characters : in C -> ASCII
- when a programming language use ASCII character set
     - it will interpret group of eight bits
- human brains like to categorize and groups things
- operator ->

     - classification by number of operands :
          - unary (1 operand)
          - binary (2 operand)
          - ternary (3 operand)
     - classification by functions(what they do) :
          - arithmetic
          - logical
          - assignment
          - relational
     - `printf(),` `scanf()` are examples of I/O function
     - truncated vs rounded : 5,6 -> 5 (truncated) -> 6 (rounded)
     - a character array put \0 ( null character or terminating character or null terminator) becomes a string
     - **control flow** statements aka **branching** : `if`, `for`, `while`
     - code block -> scoping -> curly braces in if statement

- the logic is more complicated than i thought, should relearn logic math

```
if A :
  if B :
    A and B true
  else :
    A true B false
else :
  A false B false
  ====
if A or B :
  A or B true
else :
  A and B false
  ====
if A and B :
  A and B true
else :
  A or B false
```

- **short circuit evaluation**: when executing long expression, save computing time -> know whether true or false early
- [multiple-if vs else-if : tutorial 58](https://www.youtube.com/watch?v=ksfOGOqgj4c&list=PL_c9BZzLwBRKKqOc9TJz1pP0ASrxLMtp2&index=59)
     - the board drawing in the video :
          - if true -> go into the code block
          - so many if same level can be all executed
          - unlike if else only 1 can be executed
- if can be used without brackets(scoped by semi-colon;), -> bad practice, only use when statement fit on 1 line
- **switch statement** switch(variable){case variable-value:\n //code break;default}->break is important, switch may run through all cases if there's no break
- input stream or buffer temporarily data ready to store in variable
     - `scanf()` input function -> there are other (better) input functions, check them out
     - `printf()` output function
     - string = array of char => `char a[];`
     - null character at the end of string, reserve 1 space
     - function -> DRY don't repeat yourself
     - lesson 88 : function design

```
return_type function_var_name(parameter)
{
  //function code
  return statement
}
```

- parameter(in function definition) != argument(value)
- int \* int always = int => this concept is known as closure
- refactoring code -> write some test then refactoring
- how to have good code :
     - write some shit code first then think about refactoring later
- indirection operator : `*` -> with declaration this become pointer :
     - ex :
          - `int *P;` -> pointer
          - `*P` -> indirection operator -> reference the value where the pointer point to

* 3 things you need to know :
     1. pointer declaration : `int *P;`
     2. assign value : `p = &x;`
     3. reference the value : `*P` <- indirection operator (aka dereferencing, dereference a pointer)

- pointer = object that stores a memory address -> what variable name really is
- dereference : obtain from (a pointer) the address of a data item held in another location.
- `scanf()` require argument is address, because it will change the actually value of the variable
- think of `scanf()` like this :
     - if you pass the value : the value is copied and inside `scanf()` they do whatever but never change the value outside of that function
     - if you pass the address : the dereferencing pointer is changed means they affect outside of the function
