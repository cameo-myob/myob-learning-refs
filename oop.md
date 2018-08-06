# Object Oriented Programming

Object Oriented Software is divided into objects which data and functions are built around.

### Designing a Class
- A clear concept
- A well designed interface of things you can do with it
- Abstract away some of the complexities

## Core Principles
- Encapsulation: hiding internal complexities
- Inheritance: inherit common functionality between different and related objects
- Polymorphism: something (usually function) has one name but many implementations

### Encapsulation
- Data and methods that change that data are enclosed in single unit
- Also refers to hiding internal details/complexities, which allows us to hide details of an object from other objects (abstraction)
- Uses getters and setters to access private information
- Make as much information private as possible and use getters/setters to access
- `right click > 'Source' > 'Generate Getters and Setters'`

### Inheritance
- When a class includes a property of another class
- Increases object reusability 
- Child object includes the properties of its parent, these can be overwritten
- Abstract classes can't be instantiated themselves but can pass on properties to its children
- Declared by `abstract` - `public abstract class Vehicle`
- Class inheriting `extends` parent class - `public class Car extends Vehicle`
- Use `super` to call functions from parent class
- Original class that is used to derive a new one is the `parent class`, `superclass` or `base class`
- Keyword `extends` denotes a class inheriting from another class
- A class can only `extend` one class, can `implement` many interfaces

#### Notes on Inheritance
- Every derivation should be an 'is-a' relationship, a more specific version of the parent
- Design class hierarchy or capitalise on reuse and potential reuse in the future
- As classes and objects are identified in the problem domain, find their commonality and push those features as high in the class hierarchy as appropriate
- Override methods as appropriate to tailor or change functionality of the child
- Add new variables to the child class as needed, but don't shadow any inherited variables
- Allow each class to manage it's own data. Use the `super` reference  to invoke a parent's constructor and to call overridden versions of methods if needed
- Design a class hierarchy to fit the needs of the application, with attention to how it may be useful in the future
- Override general methods such as `toString` and `equals` appropriately in child classes to that the inherited versions don't cause problems later
- Use abstract classes to specify a common class interface for the concrete classes lower in the hierarchy
- Use visibility modifiers carefully to provide needed access in derived classes without violating encapsulation

### Polymorphism
- Child classes inherit both the state (data) and the methods of the parent
- Multiple versions of the same method
- Overriding and overloading

#### Overriding
- Methods are passed from parent to child and can be overwritten
- Inheritance tree prioritizes the most local or specific implementation of method
- If child doesn't have local version of method, program will look to parents for method
- `@Override` above method - annotations
- Running a method will call the most local version, calling `super` before the method will look to the parent
- Defining a method with the `final` modifier means the method cannot be overridden by children
- Not recommended to declare variable in child with same name as one that is inherited from the parent, called `shadow variable`


#### Overloading
- Using the same method name but different paramaters (either number or type) to run different method bodies
- Allows you to offer more than one constructor for a class

### Class Abstraction 
- The separation of class implementation from the use of a class


## Class Design Guidelines
### Cohesion
- A class should describe a single entity and all operations should logically fit together to support a coherent purpose
- A single entity with too many responsibilities should be broken into several classes to separate responsibilities

### Consistency
- Follow standard Java programming style and naming conventions
- Provide a public no-arg constructor for constructing a default instance

### Encapsulation
- A class should use the `private` modifier to hide its data from direct access by clients
- Provide a `get` method only if you want the field to be readable, and a `set` method only if you want it to be updatable

### Clarity
- A class should have a clear contract that is easy to explain and easy to understand
- Design a class that imposes no restrictions on what or when the user can do with it
- Design methods that function independently of their order of occurrence

### Completeness
- A class should provide a variety of ways for customisation through properties and methods

### Instance vs Static
- A variable or method that is dependent on a specific instance of the class should be an instance variable
- A variable or method that is not dependent on a specific instance of the class should be declared static




