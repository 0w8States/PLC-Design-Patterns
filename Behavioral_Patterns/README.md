# Behavioral Design Patterns

Behavioral patterns are concerned with algorithms and the assignment of responsibilities between objects.

*Patterns marked with **Creational Pattern** should be used sparingly and with caution. They require dynamic memory allocation on runtime, and are typically not ideal for PLC environments.*



1. [**Chain of Responsibility**](Chain_of_Responsibility/) - Lets you pass requests along a chain of handler object. Each handler can then decide to process the request, or pass it to the next in the chain.

2. [**Command**](Command/) - Turns a request into a stand-alone object that contains all information about the request.

3. [**Iterator**](Iterator/) - Used to get a way to access the elements of a collection object in sequential manner without any need to know its underlying representation. **Creational Pattern**

4. [**Mediator**](Mediator/) - Used to reduce communication complexity between multiple objects or classes.

5. [**Memento**](Momento/) - Used to restore state of an object to a previous state. **Creational Pattern**

6. [**Observer**](Observer/) - Lets you define a subscription mechanism to notify multiple objects about any events that happen to the object they’re observing.

7. [**State Pattern**](State/) - Similar to a Finite-State machine. Lets and object alter its behavior when its internal state changes.

8. [**Strategy**](Strategy/)- Lets you define a family of algorithms, put each of them into a separate class, and make their objects interchangeable.

9. [**Template Method**](Template_Method/) - Defines the skeleton of an algorithm in the superclass but lets subclasses override specific steps of the algorithm without changing its structure.

10. [**Visitor**](Visitor/) - Lets you separate algorithms from the objects on which they operate.
