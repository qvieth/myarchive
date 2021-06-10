# data structure - nullpointerexception

-   graphs : 6 different types - look at 3 most popular
    -   directed vs undirected | cyclic vs acyclic | weighting graphs | graph combinations
    -   tree vs graph : trees have a specific starting point
    -   notationally : nodes{1,2,3,4} edges{(1,2),(3,4),(3,1)} | edges - adjacent
    -   undirected graph : direction you traverse isn't important - indicated by lack of arrows
    -   directed graph : has arrows
    -   cyclic graph : one which contains a path from at least one node back to itself
        -   all undirected graphs are cyclical
    -   acyclic graph : one which contains no path from any node which leads back to itself
    -   weighted graphs :
        -   associated a numerical value with each edge(cost)
        -   each weight represents some property of the information you're trying to convey
    -   cyclical undirected - cyclical directed - acyclical directed
    -   **undirected cyclical graphs with weighted edges** can be used through dijkstra's shortest path algorithm
        -   compiles a **list** of the shortest possible paths from that source vertex to all other nodes within the graph
    -   unweighted cyclical graphs are used in the follower system of majority of social media websites
-   heaps
    -   min heap - max heap
    *   heaps are most commonly used in the implementation of Heapsort
        -   [ ] a sorting algorithm which takes in a list of elements, builds them into a min, or max heap, and then removes the root Node continuously to make a sorted list
    *   **priority queues** - an advanced data structure which your computer uses to designate tasks and assign computer power based on how urgent the matter is
        -   think of a line at a hospital || you wouldn't want your computer to update an application before it finishes rendering a video otherwise your progress will be lost
        -   priority queues take care of all the task scheduling done by your computer and the heap data structure used as the backbone for it
-   tries - tree based on alphabet - autosuggestion/spell check - flagging(end of word)
-   trees :
    -   trees store data hierarchically as opposed to linearly
    -   an abstract data structure which contains a series of **linked nodes** connected together to form a hierarchical representation of information
    -   like a **linkedlist** where each has the option of pointing towards **multiple nodes**
    -   node|vertices - edges
    -   height - number of edges on the longest possible path down towards a leaf - property of the tree
    -   depth - number of edges required to get from that node to the root node - property of the node
    -   binary search tree BST - simple variation on the standard tree which has 3 restrictions on it to help organize the data:
        -   a node can have at most 2 children
        -   \forall parent, left child <, right child >
        -   no 2 nodes can contain the same value
    -   BST advantages :
        -   search O(logn)
        -   makes them extremely popular for storing large quantities of data that need to be easily searchable
-   dictionary : key:value | 1 key, 1 value | hashtable - hashfunction | asid 1111
-   each nullpointerexception has a reference part - can be useful

*   linked list : **sequential access** | node = data + pointer(takes computer to the next node in the list)
    -   how to define linked list in a specific language
    -   used in the backing of other data structures, we can use linkedlist to make stacks, queues

-   queue
-   stack : undo/redo | back-paging | recursiong | LIFO ASID nn11
-   random access data structures - independent elements - O(1) accessing - array and arraylist
-   sequential(limited) access data structures - dependent elements - stack, queue and linked lists

*   arraylist - why not always use arraylists - array is quite trash comparing to arraylists
    -   array list size is dynamic

-   array | asid 11nn
    -   parralel arrays - good way to have multiplt bits of information about one entity to be stored in a way that is easily accessible
    -   size cannot be changed
    -   2 ways for creating and filling arrays : populate at the create time, populate later
    -   index : 2d array is mostly the same as with 1d array, just need 1 more indexes
    -   Acessing O(1) | Searching O(n) | Inserting O(n) | Deleting O(n)
    -   searching through array is O(n) because we must use linear search
-   we want a quantifiable way to measure how efficient certain data structures are at different tasks we might as of it
    -   always think of binary search at example for bigO - what is N, steps
    -   searching - modifying - accessing
    -   big O(always talk of worst case)- time complexity equation - O(n!) hasn't been mentioned
    -   by measuring how efficiently a data structure can do these 4 things
        -   we can create a "report card"
    -   the most common functions you might want from a data structure :
        -   ASID : access, search, insert, delete
