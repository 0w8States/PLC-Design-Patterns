



# State

### Description

The State design pattern is a behavioral pattern in where the object can alter it's behavior when it's internal state is changed.


### Problem

The State design pattern is very similar to what is known as a [Finite-State Machine](https://en.wikipedia.org/wiki/Finite-state_machine).

![FSM](.\Images\FSM.png)

It's a simple concept; at any give moment, the machine has a finite number of states that it can transition into, or be currently in. Within any unique state, the program behaves differently, and the program can be switched from one state to another instantly. One of the key advantages is that depending on the current state, the program may or may not switch to a specific other state. The switching rules are called **transitions**, and are also finite.

Even if you have never heard of a Finite State Machine, you've most likely implemented on in the past when working with PLCs. They are commonly made up of simple IF and CASE statements that transition the machine into specific states and execute some code.

```reStructuredText
CASE eState OF
	Init:
		//Set some values
		eState := E_State.Starting;
	Starting:
		//Start some process
		Motors.Start();
		If Motors.Status = Running THEN
			eState := E_State.Running;
		END_IF
	Running:
		//Status of the process
		nPackageCount := nTotalPackaged.
END_CASE


```


However, there are some weaknesses to a state machine based on conditionals like the one above. The weaknesses only tend to reveal themselves when we start adding more states and state-dependent behaviors. Most methods will contain monstrous conditionals that pick the proper behavior of a method according to the current state. Code like this is very difficult to maintain because any change to the transition logic may require changing state conditionals in every method.

The problem grows into a bigger issue as the project evolves over time, as it's quite difficult to determine all the states and transitions during the design phase. This allows even the smallest state machines and code bases to grow into an unwieldly mess of bloated code in no time.



### Solution

The State design pattern follows the concept of using a class for each possible state, each new state added to the program in the future will have it's own new class. We would extract all the state specific behaviors and implement them in their corresponding classes.

Instead of implementing all the behaviors, the original object (a.k.a *context* object) stores a reference to the state object that represents it's current state. The *context* object then delegates all it's state related work to the referenced state object.

To transition the ***context*** object into another state, we replace the active state object reference with another object that represents the new state. The implementation of this design pattern is only possible if all the state classes use the same interface, as the *context* object will work with these state objects through the interface.

Throughout this series you might see a similar design pattern known as a **Strategy** pattern. One thing to keep in mind is that with the State pattern the states can know of each other, and also initiate transitions to one-another.  Whereas with the Strategy pattern, the states almost never know of each other.



### Structure

![TC Pattern UML](.\Images\ClassDiagram.bmp)

- **FB_Context** stores a reference to one of the FB_States and delegates to it all the specific state work. It does this by accessing the state via the state interface. The context also has a setter for passing it a new state object.

- **ITF_State** interface describes the state specific methods, these methods should make sense for all your FB_State objects because you don't want useless methods laying around. In the examples for this series, I use them as transitional actions.

- **FB_State** provide the own unique implementations for each state specific method. FB_State1 might use doThis() but not the doThat(), so the code would be empty for that method. While FB_State2 might be the other way around. 

  It's very common and powerful to have a backreference to the context inside the state object. By adding a backreference, you can access and required info in the context, and also trigger state changes from within the FB_State; thus making it possible to internally transition from FB_State1 to FB_State2, by using the context backreference located in FB_State1. This is seen inside the Example section below, ATM doesn't do state changes from the MAIN POU, it uses backreferences to transition via it's internal states.



### Example

When using an ATM machine, the buttons and actions of the machine behave differently depending on the  current state of the machine.

- When the machine is off, inserting your credit card or trying to enter a PIN number will do nothing.
- When the machine is on and running, trying to use the machine with a fault occurrence will most likely transition to an Out of Service state from a multitude of other states.
- When the machine is Out of Service, there are only a select few other states that you can select.



![ATM Machine](.\Images\StatePatternDiagram.png)

### Application Use Case

- **Use the State pattern when you have an object that behaves differently** 
  **depending on its current state, the number of states is enormous, and** 
  **the state-specific code changes frequently.**

  The pattern suggests that you extract all state-specific code into a set
  of distinct classes. As a result, you can add new states or change 
  existing ones independently of each other, reducing the maintenance 
  cost.

- **Use the pattern when you have a class polluted with massive conditionals**
  **that alter how the class behaves according to the current values of the**
  **class’s fields.**

  The State pattern lets you extract branches of these conditionals into 
  methods of corresponding state classes. While doing so, you can also 
  clean temporary fields and helper methods involved in state-specific 
  code out of your main class.

- **Use State when you have a lot of duplicate code across similar states and transitions of a condition-based state machine.**

  The State pattern lets you compose hierarchies of state classes and 
  reduce duplication by extracting common code into abstract base classes.