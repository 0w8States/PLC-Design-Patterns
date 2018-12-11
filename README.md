# Software Design Patterns for TwinCAT PLC



Welcome to my series on software design patterns for PLC programming. This series will focus on the primary design patterns that are used throughout the software industry but will show where they fit and how they might be implemented in PLC type systems.



To start off the series, I will be going through the design patterns noted by the notorious **GoF** (Gang of Four) authors. In 1994, the book **Design Patterns: Elements of Reusable Object-Oriented Software** was published and set up most of the industry standards for OOP design theory and practice. The book's authors are [Erich Gamma](https://en.wikipedia.org/wiki/Erich_Gamma), Richard Helm, [Ralph Johnson](https://en.wikipedia.org/wiki/Ralph_Johnson_(computer_scientist)) and [John Vlissides](https://en.wikipedia.org/wiki/John_Vlissides) with a foreword by [Grady Booch](https://en.wikipedia.org/wiki/Grady_Booch). While the book shows examples in more mainstream languages, they can be adapted to almost any OOP based architecture, thus the can also be implemented in IEC 61131-3 3rd edition PLC environment.



Starting off the series, I'd like to cover the question of **What?** and **Why?**



### **What is a design pattern?**

A design pattern is a solution to commonly occurring problems in software design. The can be considered as a blueprint that you can tweak to fit a reoccurring problem in your code.

Patterns are often confused with algorithms, mostly because both of them describe a solution to known problems. Algorithms can be followed many times without tweaking, as it's a clear set of actions to achieve some goal. A pattern, on the other hand, is much more of a high-level description of a system; the same set of code for pattern implementation in a problem today might be different for a problem tomorrow. 

An analogy to an algorithm is a recipe; you have clear steps the achieve a goal. While a pattern is more like a blueprint; you can see the results and it features, but the implementation is up to you.



A pattern consists of the following:

- **Intent** - briefly describes both the problem and solution
- **Motivation** - further explains the problem and solution that the pattern makes possible
- **Structure** - usually a UML diagram or some type of description that shows each part of the pattern, and how they relate to one another.
- **Example** - a code example to show how the pattern is implemented in various languages, for this series it will be IEC61131-3 Structured Text.



### **Why should I use or learn patterns?**

With the introduction of OOP in the IEC61131-3 3rd edition standard, this opened the doors to many of the features the software engineering industry already uses. Truth be told, both PLC and non-PLC programmers might go for many years without studying a single pattern. Some might even implement a pattern without even knowing. So why would you spend time studying patterns?

Consider design patterns a toolkit, a tested and proved solution for many of the problems that arise in software design. If you ever encounter a problem, it's very advantageous to know that there is a solution already available and is easily solvable with object-oriented design principals. Design patterns also provide a common blueprint or language and allow teammates to communicate more efficiently. 





## **Design Pattern Types**

Follow the link to your desired design pattern type, inside there will be examples of the various design patterns.



- **Creational Design Patterns** *(COMING SOON....)*

  These patterns provide various object creation mechanisms, which increase flexibility and reuse of existing code.

- **Structural Design Patterns** *(COMING SOON....)*
  These patterns explain how to assemble objects and classes into larger structures while keeping this structures flexible and efficient.

- **[Behavioral Design Patterns](Behavioral Patterns/)** These patterns are concerned with algorithms and the assignment of responsibilities between objects.