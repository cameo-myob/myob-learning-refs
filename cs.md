# Computer Science Reference

## Abstract Data Types
- A type (or class) for objects whose behavior is defined by a set of values and a set of operations
- Data type is defined by it's behaviour from the point of view of a user of the data
- Mentions what operations can be performed but not how they will be implemented - abstraction
- A theoretical concept in CS

###  Different ADT Perspectives
- Application (user) level - using an ADT to solve a problem
- Logical (abstract) level - an abstract view of data values and operations to manipulate them
- Implementation (concrete) level - a specific representation of ADT to hold data


### ADTs in Java
- List
- Queue
- Stack

### List
#### Linked List
- A collection of separate elements, with each element linked to the one that follows it in the list
- Like a chain of elements

#### Sorted List
- A linear relationship between elements - dictionary, phone book etc.
- Reflects ordering elements from 'smallest' to 'largest'

### Stack
- A list in which elements are accessed in last-in, first-out (LIFO) order only
- Contains elements of the same type arranged in sequential order
- Considered ordered because elements occur in sequence according to how long they've been in the stack
- All operations occur at a single end (top of the stack)
- _Push_ operation adds an element to the top of the stack (transformer)
- _Pop_ operation removes an element from the top of the stack (transformer)

### Queue
- A list in which elements are accessed in first-in, first-out (FIFO) order only
- Operations occur at both ends (insertion at end, deletion at front)
- Supports two basic operations - put and get
- Each put operation will place a new element on the end of the queue
- Each get operation will retrieve the next element from the front of the queue
- Operations are consumptive - once an element has been retrieved, it cannot be retrieved again
- Queues can become full or empty
- Circular queues reuse locations in the underlying array when elements are removed
- Noncircular queue does not reuse locations and eventually becomes exhausted

### Tree
- Non-linear structure
- Each element in tree can have multiple child elements
- Useful for representing hierarchical relationships between elements
- Root does not have parent element

### Graph
- Non-linear structure like trees, but no restrictions between elements
- Elements are called nodes/vertices
- Connections are called edges
- Weighed connections represent some feature of the relationship

### Set
- Stores unique values (no duplicates) without order
- Usually test to see if value belongs in set, rather than retrieving value from set


### Map
- An object that contains key/value pairs
- Cannot contain duplicate keys


---


- Preconditions - Assumptions that much be true on entry into a method for it to work correctly 
- Postconditions - The results expected at the exit of a method, assuming preconditions are true
- Transformers - methods to change the content of an ADT (insert, clear)
- Observers - methods to observe the ADT and return the information (contains, size, isFull, toString)
