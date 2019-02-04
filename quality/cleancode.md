# Clean Code by Robert Martin

## Chapter One - Clean Code
### What Is Clean Code?
> Elegant and efficient. Hard for the bugs to hide. Clean code does one thing well. 

> Simple and direct. Reads like well-written prose. Never obscures the designer's intent.

> Provides one way for doing one thing. Can be read and enhanced by a developer other than it's original author.

> Looks like it was written by someone who care. Nothing obvious you can do to make it better.

> Beck's rules of simple design - tests run, no duplication, expresses ideas, minimizes entities.

> Each routine you read turns out to be pretty much what you expected. Makes it look like the language was made for the problem.

### We Are Authors
Authors are responsible for communicating well with their readers. Remember that you are an author, writing for readers who will judge your effort.
You cannot write code if you cannot read the surrounding code.

### The Boy Scout Rule
_Leave the campground cleaner than you found it._

## Chapter Two - Meaningful Names
### Use Intention-Revealing Names
Names should reveal intent. The name of a variable, function or class should answer questions about why it exists, what it deos and how it is used.

### Avoid Disinformation
Avoid words that have an entrenched meaning that differs from our meaning. Don't call a grouping of accounts an `accountsList` unless it is actually a `List`.

### Use Pronounceable Names
If you can't prnounce a variable name, you can't discuss it without sounding like an idiot.

### Use Searchable Names
Single letter names and numeric constants are hard to locate across a body of text. The length of a name should correspond to the size of it's scope. If a variable or constant might be sen or used in multiple places in a body of code, it is imperative to give it a search-friendly name.

### Avoid Mental Mapping
Readers shouldn't have to map your names into names they already know. Use a ubiquitous language that is understood by everyone.

### Class Names
Classes and objects should be noun or noun phrases like `Customer` or `Account` - avoid verbs like `Manager` or `Processor`.

### Method Names
Method names should be verb or verb phrases like `postPayment` or `deletePage`. Accessors, mutators and predicates should be named for their value and prefixed with `get`, `set` and `is`.

### Pick One Word Per Concept
Don't use terms like `fetch`, `get` and `retrieve` as equivalent methods in different classes. This causes confusion over which method name belongs in which class. Pick one word and use it consistently across the codebase.

### Using Solution Domain Names and Problem Domain Names
Considering that people who read your code will be programmers, use specific technical names where possible. If the code has more to do with problem domain concepts use names from the problem domain.

### Add Meaningful Context
Few names are meaningful in and of themselves - most are not. Give your readers context by creating well named classes, functinos or namespaces.

### Don't Add Gratuitous Context
> Shorter names are generally better than longer ones, so long as they are clear. Add no more context to a name than is necessary.

#### Choosing good names requires good descriptive skills and a shared cultural background.

## Chapter Three - Functions
### Size
Functions should be small. Smaller. *Smaller.*

### Blocks and Indenting
Ideally blocks within `if`, `else` and `while` statements should be one line long, and that line shold be a function call. This keeps the enclosing function small and allows you to gave the called function a nice descriptive name. Functions should also not be large enough that they contain nested structures. Indentation in a function should not be greater than one or two.

### Do One Thing
Functions should do one thing, they should do it well and they should do it only.

### One Level of Abstraction Per Function
> In order to make sure out functions are doing one with, we need to make sure that the statements within our function are all the same level of abstraction.

>To say this differently, we want to be able to read the program as though it were a set of TO paragraphs, each of which is describing the current level of abstraction and referencing subsequent TO paragraphs at the next level down.
``` 
To include the setups and teardowns, we include setups, 
then we include the test page content, and then we include the teardowns.

To include the setups, we include the suite setup if this is a suite, 
then we include the regular setup.

To include the suite setup, we search the parent hierarchy for the 
“SuiteSetUp” page and add an include statement with the path of that page.

To search the parent…
```

### Switch Statements
> We can't always avoid switch statements, but we can make sure that each swtich statement is buried in a low-level class and is never repeated using polymorphism. The solution is to bury the switch statement in the basement of an Abstract Factory and never let anyone see it.

 ### Use Descriptive Names
 Don't be afraid to make a name long - a long descriptive name is better than a short enigmatic name. Use a naming convention that allows multiple words to be easily read in the function names, then make use of those multiple words to give the function a name that says what it does.

 ### Function Arguments
 #### Monadic Functions
 Monadic functions take a single argument and are often used to ask a question about that argument (i.e. return a boolean value) or to operate on the argument, transforming it into something else and returning it.

 #### Flag Arguments
 Flag arguments are ugly and a bad practice. Don't pass booleans as an argument.

 #### Dyadic Functions
 Can come at a cost and you should take advantage of any opportunity to convert them to monads.

 #### Triadic Functions
 Harder to understand than dyads.

 #### Argument Objects
 > When groups of variables are passed together, the way x and y are in the example below, they are likely part of a concept that deserves a name of its own.
 ```
 Circle makeCircle(double x, double y, double radius);
 Circle makeCircle(Point center, double radius);
 ```

### Have No Side Effects
Side effects can cause temporal coupling, an implicit relationship between two or more members of a class that requires the client to invoke one member before the other. Breaks the 'do one thing' rule.

#### Output Arguments
Arguments that affect the output of a function.
`public void appendFooter(StringBuffer report)` is better written as `report.appendFooter()`
> In general output arguments should be avoided. If your function must change the state of something, have it change the state of its owning object.

### Command Query Separation
> functions should either do something or answer something, but not both. Either your function should change the state of an object, or it should return some information about that object.

### Prefer Exceptions to Returning Error Codes
Returning error codes from command functions violates command query separation and promotes commands being used as expressions in `if` statements. If you use exceptions instead of returned error codes then processing the error can be separated from the code's happy path.
```
if (deletePage(page) == E_OK) {
     if (registry.deleteReference(page.name) == E_OK) {
       if (configKeys.deleteKey(page.name.makeKey()) == E_OK){
         logger.log("page deleted");
       } else {
         logger.log("configKey not deleted");
       }
     } else {
       logger.log("deleteReference from registry failed");
     }
   } else {
     logger.log("delete failed");
     return E_ERROR;
   }
```

vs

```
try {
     deletePage(page);
     registry.deleteReference(page.name);
     configKeys.deleteKey(page.name.makeKey());
   }
   catch (Exception e) {
     logger.log(e.getMessage());
   }
```

I have a lot of questions about this.