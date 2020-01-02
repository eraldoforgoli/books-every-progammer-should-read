# Clean Code

One of the masterpieces of Uncle Bob, highly recommended for craftsman.
I agree with almost everything that Uncle Bob writes in this book.
This book will teach you the art of writing clean code.

# WHAT IS CLEAN CODE ?

- Brajne Stroustrup:
  I like my code to be elegant and efficient. The logic should be straightforward and make it hard for bugs to hide, the dependencies minimal to ease maintenance, error handling complete according to an articulated strategy, and performance close to optimal so as not to tempt people to make the code messy with unprincipled optimizations. Clean code does one thing well.

- Grady Booch, author of Object Oriented Analysis ..
  Clean code is simple and direct. Clean code reads like well-written prose. Clean code never obscurs the designer's intent but rather is full of crisp abstractions and straightforward lines of control.

- Dave Thomas
  Clean code can be read , and enhanced by a developer other than its original author. It has unit and acceptance tests. Is has meaningful names. It provides one way rather than many ways for doing one thing. It has minimal dependencies, which are explicitly defined, and provides a clear and minimal API. Code should be literate since depending on the language, no all necessary information can be expressed clearly in code alone.

- Michael Feathers
  I could list all of the qualities that i notice in clean code, but there is one overarching quality that leads to all of them. Clean code always looks like it was written by someone who cares. There is nothing obvious that you can do to make it better. All of those things were thought by the code's author, and if you try to imagine improvements, you're led back to where you are, sitting in appreciation of the code someone left for you - code left by someone who cares deeply about the craft.

- Ron Jeffries
  In recent years i begin and nearly end, with Beck’s rules of simple code. In priority order, simple code:

  1.  Runs all tests;
  2.  Contains no dublications
  3.  Expresses all the design ideas that are in the system;
  4.  Minimizes the number of entities such as classes, methods, functions and the like.

  Of these, i focus mostly on duplication. When the same thing is done over and over, it’s a sign that there is an idea in our mind that is not well represented in the code. I try to figure it out what it is. Then i try to express that idea more clearly.

  Expressiveness to me includes meaningful names, and i am likely to change the names of things several times before i settle in.
  Expressiveness goes beyond names, however. I also look at whether an object or method is doing more than one thing. If it’s an object, it probably needs to be broken into two or more objects.
  Duplication and expressiveness take me a very long way into what i consider clean code, and improving dirty code with just these two things in mind can make a huge difference.
  After years of doing this work, it seems to me that all programs are made up of very similar elements. Whether we have a database of employee records, or a hash map of keys and values, or an array of items of some kind, we often find ourselves wanting a particular item from that collection. When i find that happening, i will often wrap the particular implementation in more abstract method or class. That gives me a couple of interesting advantages.
  I can implement the functionality now with something simple, say a hash map, I can change the implementation any time i want. I can go forward quickly while preserving my ability to change later.
  Reduced duplication, high expressiveness, and early building of simple abstractions. That’s what makes clean code for me.

- Ward Cunningham
  You know you are working on clean code when each routine you read turns out to be pretty much what you expected. You can tell beautiful code when the code also makes it look like the language was made for the problem.

- The Boy Scout Rule
  It’s not enough to write code well. The code has to be kept clean over time.
  Leave the playground cleaner than you found it.

## **Chapter 2: Meaningful Names**

1. Use Intention-Revealing Names  
   The name of a variable, function or class, should answer all the big questions. It should tell why it exists, what it does and how it is usd. If a name requires comment, then the name does not reveal its intent.

2. Avoid Disinformation  
   We should avoid word whose entrenched meanings vary from our intended meaning.

3. Make Meaningful Distinctions  
   Don’t misspell names just because a name is being already used. Try being more creative.

4. Use Pronounceable Names  
   Don’t make noise by using derived words. If you have a Product class, then you add ProductData, ProductInfo, you just made the names different, without making them mean anything different.

5. Noise words are redundant.  
   The word variable should never appear in a variable name. The word table should never appear in a table name, and so on. Would a name be a floating point number? Or Customer vs CustomerObject ?
   Humans are good at words. If you can’t pronounce it, you can’t discuss it without sounding like an idiot.

6) Searchable Names  
   Single-letter names and numeric constants have a particular problem in that they are not easy to locate across a body of text.
   Single-letter names can only be used as local variables inside short methods (i have my doubts about that too).
   The length of a name should correspond to the size of its scope.

7) Avoid Encodings  
   If a variable or a constant might be seen or used in multiple places in a body of code, it is imperative to give it a search friendly name.

8. Interfaces and Implementations  
   These are sometimes a special case for encodings. For example, when building ABSTRACT FACTORY for the creation of shapes. This factory will be an interface and implemented by a concrete class. You should not name the class indicating that you are handing an interface. So if i must encode the implementation or the interface, i choose the implementation. Calling it ShapeFactoryImp is preferable to encoding the interface.
9. Avoid Mental Mapping  
   Readers shouldn’t have to mentally translate your names into other names they already know.

#### **Class Names**

- Class and objects should have noun or noun phrase names like Customer, WikiPage, Account, and AddressParser. Avoid names like Manager, Processor, Data in the name of a class. Don’t use verbs.

# **Method Names**

- Method names should have verb or verb phase names like postPayment, deletePage. Accessors, mutators and predicates are suggested , i.e getName(), setName(), etc.

### **Don’t be cute**

- If names are too clever, they will be memorable only to people who share the author’s sense of humor, or as long as these people remember the joke. What should HolyHandGranade do? DeleteItems might be a better name.

### **Pick One Word Per Concept**

- Pick one word per concept and stick with it. For instance, is confusing to have fetch, retrieve and get as equivalent method of different classes.
  Likewise, it’s confusing to have a controller and a manager and a driver in the same code base.

### **Don’t Pun**

- Don’t use the same word for two purposes. Using the same term for two different ideas is essentially a pun.

### **Add meaningful Context**

- If you follow the ‘one word per concept’ rule, you could end up with many classes that have for example, the add method. As long as the parameter lists and returns values of the various add method are semantically equivalent, all is well.

### **Use Solution Domain Names**

- Remember that people who will read your code will be programmers. So go ahead and use Computer Science terms, names, math terms, and so on.

### **Don’t Add Gratuitous Context**

- If you app is called Bot, is a bad idea to prefix every class with Bot. Frankly, you are working against your tools.

## **Functions**

### **Small!**

- The first rule of functions if that they should be small. The second rule of functions is that they should be smaller than that.

### **Do One Thing**

- Functions should do one thing. Should do it well. Should do it only.
  What do you mean by ‘do one thing’ ?
  If a function does only these steps that are one level of abstraction below the stated name of the function, then the function is doing one thing.

### **Blocks and Indenting**

- This implies that the blocks within if statements, else statements, while statements and so on, should be one line long. Probably should be a function call. It keeps the function small and adds documentary value.

### **One Level Of Abstraction per Function**

- In order to make sure our functions are doing ‘one thing’, we need to make sure that the statements within our function are all at the same level of abstraction.  
  Mixing levels of abstraction within a function is always confusing.

### **The Step Down Rule**

- We want the code to read like a top-down narrative. We want every function to be followed by those at the next level of abstraction so that we can read the program, descending one level of abstraction at a time as we go down the list of functions.

### **Switch Statements**

It’s hard to make a small switch statement. Even a switch with only two cases is larger than I'd like a single block to be.
Solution: bury the switch statement in the basement of an ABSTRACT FACTORY and never let anyone see it.

- Use Descriptive Names  
   Don’t be afraid to make a long name. A long descriptive name is better than a short enigmatic name, or a long descriptive comment.
  Be consistent in your names.

## **Function Arguments**

- The ideal number of arguments for a function is zero (niladic).
  Next comes one (mondaic), followed closely by two (dyadic).
  Three arguments (triadic) should be avoided where possible.
  More than three (polyadic) requires very special justification - and shouldn’t be used anyway.

- Arguments are hard. They take a lot of conceptual power. Most of the time, the arguments are at a different level of abstraction than the function name and forces you to know a detail. Arguments are even harder from a testing point of view. Imagine the difficulty of writing all the tests cases to ensure that all the various combinations of arguments work properly.

- **Common Monadic Forms**  
   There are two common reasons to pass a single argument into a function:
  You may be asking a question about that argument, as in boolean fileExists(“file”)
  Or you may be operating on that argument, transforming it into something else and returning a value. Use names that make the distinction clear.

- **Flag Arguments **  
  Flag arguments are ugly. Passing a boolean into a function is a truly terrible practice. It immediately complicates the signature of the method, proclaiming that this function does more than one thing.

- **Dyadic Functions**  
  A function with two arguments is harder to understand than a monadic function.
  They aren’t evil, and you will certainly have to write them, but you should be aware that they come at a cost and you should take advantage of what mechanisms may be available to convert them to a monad.

- **Triads**  
  Functions that take three arguments are significantly harder to understand than dyads. I suggest you think before creating a triad.

- **Argument Objects**  
  When a function seems to need more than two or three arguments, it is likely that some of those arguments ought to be wrapped into a class of their own.

- **Verbs and Keywords**  
  Choosing good names for a function can go a long way toward explaining the intent of the function and the intent of the arguments.
  In case of a monad, the function can have a short name, like : writeField(name);
  For example, assertEquals might be better written as assertExpectedEqualsActual(expected, actual).

- **Have No Side Effects**  
  Side effects are lies. Your function promises to do one thing, but it also does other hidden things.

- **Command Query Separation**  
  Functions should either do something or answer something, but not both. Either your function should change the state of an object, or it should return some information about that object. Doing both leads to confusion.

- **Prefer Exception to Returning Error Codes**  
  Returning error codes from command function violates command query separation.

- **Extract Try/Catch Blocks**  
  Try/Catch blocks are ugly in their own right. They confuse the structure of the code and mix error processing with normal processing. So it is better to extract the bodies of the try/catch blocks out into functions of their own.

- **Error Handling Is One Thing**  
  Functions should do one thing. Error handling in one thing. Thus, a function that handles errors should do nothing else. This implies that if the keyword try exists in a function, it shud be the first word of the function and there should be no other blocks.

- **DRY**
  Duplication may be the root of all evil in software. Many principles have been created for the purpose of controlling or eliminating it. Try to reuse as many blocks as possible.

## **SOLID Design Principles**

1. **Single Responsibility Principle**  
   (https://stackify.com/solid-design-principles/)

   - _A class should have one, and only one, reason to change._

   Requirements change over time. Each of them also changes the responsibility of at least one class. The more responsibilities your class has, the more often you need to change it.
   You need to change your class as soon as one of its responsibilities change. This might not seem like a big deal, but it also affects all classes or components that depend on the changed class.

2. **Open/Closed Principle**  
   (https://stackify.com/solid-design-open-closed-principle/)

   - _Software entities (classes, modules, functions, etc) should be open for extension, but closed for modification._

   The general idea of this principle is great. It tells you to write your code so that you will be able to add new functionality without changing the existing code.
   A class is closed, since it may be compiled, stored in a library, baselined, and used by client classes. But it is also open, since any new class may use it as parent, adding new features. When a descendant class is defined, there is no need to change the original or to disturb its clients.
   Use interfaces instead of superclasses to allow different implementations which you can easily substitute without changing the code that uses them. The interfaces are closed for modifications, and you can provide new implementations to extend the functionality of your software.
   The main benefit of this approach is that an interface introduces an additional level of abstraction which enables loose coupling. The implementation of an interface are independent of each other and don’t need to share any code.

3. **Liskov Substitution Principle**  
   (https://stackify.com/solid-design-liskov-substitution-principle/)

- _Let f(x) be a property provable about objects x of type T. Then f(y) should be true for objects y of type S, where S is a subtype of T._

  The principle defines that objects of a superclass shall be replaceable with objects of its subclasses without breaking the application. That requires the objects of your superclass to behave the same way as the objects of your superclass.

4. **Interface Segregation Principle**  
   (https://stackify.com/interface-segregation-principle/)

   - _Clients should not be forced upon interfaces that they do not use._

   Similar to the Single Responsibility Principle, the goal of the Interface Segregation Principle is to reduce the side effects and frequency of required changes by splitting the software into multiple, independent parts.

5. **Dependency Inversion Principle**  
   (https://stackify.com/dependency-inversion-principle/)

   _The general idea of this principle it: High-level modules, which provide complex logic, should be easily reusable and unaffected by changes in low-level modules, which provide utility features. To achieve that, you need to introduce an abstraction that decouples the high level and the low-level from each other._

   1. High-level modules should not depend on low-level modules. Both should depend on abstractions.
   2. Abstractions should not depend on details. Details should depend on abstractions.

Link:
https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship-ebook/dp/B001GSTOAM
