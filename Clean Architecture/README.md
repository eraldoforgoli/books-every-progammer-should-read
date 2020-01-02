## What is an Architecture ?

I would describe an architecture (referring to software) as the organisation of the
code in modules. The architecture defines where the application performs its
functionality, and how do the modules communicate with the external resources
(databases, 3rd party APIs, etc).

Clean Architecture is a set of practices used to create modern software architectures that is simple,
understandable, flexible, testable and maintainable.
Clean architecture is a more modern replacement for the traditional three
layered database-centric architecture that has been used for decades.

## Characteristics of a Clean Architecture

The secret to building a project that is easy to maintain, add features or scale is this:
Separating classes/components into modules that can change independently of other modules.

**Look at the picture above. What does it take to replace the marker pen with a
regular pen? Lets see:**

![common-architectures.jpeg](./assets/common-architectures.jpeg)

You have to untie the strings that ties the marker pen itself, untie the string that goes to the
bottle, untie the other string that goes to the paper clip on top of it, and who the hell knows if i missed something.
Why does the marker pen need the bottle? What about the paper clip?
So, the change that we would make affects at least two more modules, the bottle (don't know what
it contains, let's just call it a bottle) and the compass. It is quite unpleasant.

**Now, take a look at this:**

![clean-architecture.jpg](./assets/clean-architecture.jpeg)  
You want to change the marker pen with a regular pen?
Pull the pen string, tie the string to the pen you want to use. That's it.
This is what Clean Architecture is all about.

#### How would this look in a real application ?

Look at the picture below:

![clean-architecture.jpg](./assets/CleanArchitecture.jpg)

Lets explain each layer.

1. **Entities**  
   Entities encapsulate Enterprise wide business rules. It could be an object with properties, methods or
   data structures (it may vary). It does not matter as long as the entity can be uses across multiple
   modules.
   If you are using a single page application, this layer will contain business application.
   In this layer we usually encapsulate very general business rules, that are unlikely to change over time.
   Don't be afraid to apply OO principles here.
2. **Use Cases**  
   This layer is also known as the application layer, because it contains application specific rules.
   These use cases orchestrate the flow of data from and to the entities.
   As a best practice, you should create models/DTOs in this layer, and not using the entity itself directly,
   as most of the times the information you need to store/retrieve is different than the entity.
   Example: If you save a user to the system, you will likely create a model with what you expect,
   save it, and to retrieve the user, you should create another model, with the fields you need.
   It might look robust at the beginning, but it makes the flow more clear, and tights an operation to
   a model.
   This layer should not affect the entities layer, and vice versa.
3. **Interface Adapters**  
   This layer contains a set of adapters that convert data from a format that is convenient to the
   use cases, to format that is convenient to 3rd party/external services, like: Databases, Web, etc.
   Imagine this as the presenters/vies of the MVC pattern.
   Also in this layer is any other adapter necessary to convert data from some external form, such as an external service,
   to the internal form used by the use cases and entities.
4. **Framework & Drivers**
   This layer contains the frameworks and the drivers that we use, like Databases, API, external
   packages, etc.
   This package contains only details.
   The database is an implementation detail. You might be using MySql, but find out that Postgre
   is more performant, or you are forced to change the provider due to other reasons.
   You might argue that the database is not an implementation detail, well, you are right.
   There are applications where the database should not be seen as an implementation detail,
   because it might play a crucial role in your app.
   Clean Architecture is not meant to be used for every application. You should choose the pattern
   based on the type of application you are trying to build.

## Data flow

Look carefully how the data flows, and what layer knows what.
As you see, the flow is from outside in, not the opposite (it would beat the purpose).
The Controller knows about the use cases, the use cases know about entities.
So, the communication flow is: Controller => Use Case => Entity.

## Screaming Architecture

As you might have guessed, one of the benefits of this architecture is that it screams its intent.
Our architecture is build around use cases of the system. Only by looking at the use cases, you should be
able to understand what is this module trying to solve, and how does it solve it.
This makes it extremely easy for people new to your application, but also for debugging or adding new
features.
You code is organised in such a way, that concerns are split, and it is easier to make isolated changes without
affecting other parts in the application.

## Testability

This architecture is highly testable.
Each module has its own intent, and is independent of the others.
Having such isolation, and using Dependency Inversion principle, we can mock each module pretty easy
and test it.

Links: https://www.amazon.com/Clean-Architecture-Craftsmans-Software-Structure/dp/0134494164
