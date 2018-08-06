# Beginner Java Reference

- Many modern languages are designed to compile into CPU specific executable code
- A Java compiler outputs _bytecode_, which is then executed by the _Java Virtual Machine (JVM)_
- Java is an Object-Oriented Programming language
- Uses camelCase for methods and variables, TitleCase for class names
- Variable names can start with a letter, a digit, a dollar sign or an underscore
- Java only passes arguments by value, not by reference

## A Basic Java Program
```java
class Example {
    public static void main(String args[]){
        System.out.println("Java drives the Web.");
    }
}
```
- `class Example` declares that a new class is being defined, `Example` is the name of the class.
- `public` is an _access modifier_, which determines how other parts of the program can access members of the class - `main()` will always be public
- `static` means `main()` can be called without creating an instance of the class
- `void` tells the compiler that `main()` does not return a value
- `String args[]` are passed as a parameter to `main()` - it is an array of strings
- `System.out.println()` accesses System class to print output to the console

## Primitive Data Types
- Boolean
- Byte (8 bit int)
- Char
- Double (double precision floating point, 64 bit)
- Float (single precision floating point, 32 bit)
- Int (32 bit)
- Long (long int, 64 bit)
- Short (short int, 16 bit)

## Type Conversion
- Automatic (widening) type conversion
> Byte -> Short -> Int -> Long -> Float -> Double
- Explicit (narrowing) type conversion
> Double -> Float -> Long -> Int -> Short -> Byte
- Explicit conversion has the form (target-type) expression i.e. _(int) x / y_


## Operator Precedence
Highest | - | - | - | - | - | -
--- | --- | --- | --- | --- | --- | ---
++ (postfix) | -- (postfix) | - | - | - | - | -
+ (prefix) | -- (prefix) | ~ | ! | + (unary) | - (unary) | (typecast)
* | / | % 
+ | - 
>> | >>> | << 
> | >= | < | <= | instanceof
== | != 
- Index operator ([]) has highest precedence of all Java operators


## Access Modifiers
- Private can only be accessed inside the class it is declared
- Protected can be accessed from within the same package (only relevant in terms of inheritance)
- Public can be accessed globally
- Private methods denoted by `-` on UML design
- Public methods denoted by `+` on UML design
- Protected methods denoted by `#` on UML design
- Protected variables and methods can be accessed by children
- Private members cannot be accessed directly by children classes, though they can be referenced indirectly when calling super methods

 --- | Public | Private
 --- | --- | ---
 **Variables** | Violate encapsulation | Enforce encapsulation
 **Methods** | Provides services to clients | Supports other methods in the class

## Static VS Non-Static Methods
A method with Static is a class method and can be run without creating an instance of the class. A method without Static is an instance method and can only be run on an instance of a class.

## Void Methods
Void methods such as `public void methodname` do not return a value.


## Data Types as Objects
- Primitive data type like int, double, float etc. 
- Data type classes like Integer, Double, String
- Compiler can automatically convert primitives to their object wrapper class (boxing), and back to primitive (unboxing)

## Data Structures
### Arrays
- The only primitive data structure
- Fixed length which is determined at creation
- Holds values of a single type
- More common to use lists
- `int[] height = new int[11]`
- Or initialize with values `int[] scores = { 87, 89, 87, 60, 91, 83 }`
#### Bounds Checking
- Use `length - 1` to find array bounds

### List
- An ordered collection of elements
- Can contain duplicates
- Useful for positional access and insertion, search, iteration and range viewing
- Most common is the ArrayList, but LinkedList is useful if workload is write heavy not read heavy
- Often better to use List than Array
- Is dynamic, not fixed length like Array
- Lists cannot contain primitives such as bytes

### ArrayList vs LinkedList
- ArrayList is like a dynamic array - can change size as needed
- LinkedList is implemented like a double linked list (??????)
- LinkedList is faster for add/remove operations, but slower for gets and sets
- LinkedList also implements Queue interface, so adds methods like offer, peek and poll
- ArrayList a better choice for most cases - LinkedList is only marginally faster for writes but is almost 6 times slower for reads

### Sets
- A collection of unique elements (no duplicates)
- Only gives methods for adding and checking if an element exists - can't directly retrieve elements
- No guarantee around order
- HashSet, TreeSet and LinkedHashSet common
- Used to maintain a collection of elements in order to determine the uniqueness of something new
- HashSet has a consistent time complexity regardless of size

### Maps
- Map has `key: value` pairs
- Must have unique keys
- HashMap has consistent time complexity regardless of size

## Accessors and Mutators
 - Getter methods are called Accessors - they access the data
 - Accessor method names are generally `getX`
 - Setter methods are called Mutators - they mutate the data
 - Mutator method names are generally `setX`
 
## Class Relationships
- Most common relationships are dependency, aggregation and inheritance
- Dependency 'uses', aggregation 'has-a', inheritance 'is-a'
- The less dependencies between classes the better (low coupling)
- Aggregation is when an object is made of other objects - a car as an object has an engine and a chassis which are both objects too
- The more complex an object, the more likely it is to be an aggregate object
- In `UML`, aggregate objects are represented with a diamond near the class that is the aggregate

## `this`
- Allows an object to refer to itself
- Often used to distinguish parameters of a constructor from the corresponding instance variables
```java
public Account (String name, long acctNumber, double balance)
{
    this.name = name;
    this.acctNumber = acctNumber;
    this.balance = balance;
}
```

## `final`
- Non-access modifier applicable to only a `variable`, `method`, or `class`
- Used with variable to create constant variables
- Used with methods to prevent method overriding
- Used with classes to prevent inheritance
- Final variables must be initialised with a value
- Naming convention is all uppercase with underscores separating words i.e. `final int MAX_WIDTH = 4`

## `super`
- Used to refer to a parent class
- Commonly used to invoke a parent's constructor
- Can also be used to invoke a superclass method

## Abstract Classes
- Represents a generic concept
- Cannot be instantiated
- Usually contains one or more abstract methods (method signatures with no body)
- Can contain data declarations/variables
- In `UML`, abstract classes and methods are shown in italics
- Can use abstract classes as reference objects
- A child of an abstract class must implement all of the abstract methods provided, or else be defined abstract too
- A class that has abstract methods must also be abstract, but an abstract class can have non-abstract methods
- A subclass may be abstract even if its superclass is concrete
- Abstract methods have only method signature, no method body

## Interfaces
- A classlike construct that contains only constants and abstract methods
- `className implements interfaceName`
- Relationship is known as interface inheritance
- Check if object implements interface with for loop and `if(object[i] instanceof interfaceName)`

### Interfaces vs Abstract Classes
--- | Variables | Constructors | Methods
--- | --- | --- | ---
Abstract Class | No restrictions. | Constructors are invoked by subclasses through constructor chaining. An abstract class cannot be instantiated using the `new` operator. | No restrictions.
Interface | All variables must be `public static final` | No constructors. An interface cannot be instantiated using the `new` operator. | All methods must be `public abstract` instance methods.

## Constructors
- Must have the same name as the class itself
- Do not have a return type - not even `void`
- Invoked using the `new` operator when an object is created
- Can be overloaded (can have multiple constructors with varying parameters)
- Provide at least a constructor without arguments, referred to as a `no-arg` or `no-agrument` constructor (e.g. `Circle()`), to make the class easy to extend
- A class can be defined without constructors - a no-arg constructor with an empty body will be implicitly defined in the class
- The above is called a `default constructor` and is provided automatically only if no constructors are explicitly defined in the class