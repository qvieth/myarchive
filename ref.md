# ref / reference

<a href="https://en.wikipedia.org/wiki/Reference_(computer_science)">
- ref
</a>

- In computer science, a reference is a value that
- enables a program to **indirectly access** a particular datum
- such as a variable's value or a record
- in the computer's memory or in some other storage device
- The reference is said to refer to the datum
- and accessing the datum is called dereferencing the reference

- A reference is distinct from the datum itself
- Typically, for references to data stored in memory on a given system
- a reference is implemented as the physical address of where the data is stored in memory or in the storage device
- For this reason, a reference is often erroneously confused with a pointer or address
- and is said to "point to" the data
- However, a reference may also be implemented in other ways
- such as the offset (difference) between the datum's address and some fixed "base" address, as an index into an array, or more abstractly as a handle
- More broadly, in networking, references may be network addresses, such as URLs

- The concept of reference must not be confused
- with other values (keys or identifiers) that uniquely identify the data item
- but give access to it only through a non-trivial lookup operation in some table data structure

- References are **widely used** in programming
- especially to efficiently pass large or mutable data as arguments to procedures
- or to share such data among various uses
- In particular a reference may point to a variable
- or record that contains references to other data
- This idea is the basis of indirect addressing and of many linked data structures
- such as linked lists
- References can cause significant complexity in a program
- partially due to the possibility of dangling
- and wild references and partially because the topology of data with references is a directed graph
- whose analysis can be quite complicated

## benefits

...
