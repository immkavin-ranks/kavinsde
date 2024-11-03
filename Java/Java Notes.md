Non static members belong to an instance of the class, not the class itself.

Sequential programs: only one instruction is being performed at a time at any given moment.

threading: used in concurrent programs, to improve the performance and efficiency of an application.

use threading when your program has tasks that need to be performed in parallel.

thread synchronization: when multiple threads writing to a resource and manipulating its state.

 A race condition occurs when some inconsistency is caused by two threads trying to access the same shared data at the same time.

Thread methods: start(), sleep(), join(), is Alive()

Interthread communication: wait(), notify(), notifyAll()

principles of OOP: inheritance, polymorphism, abstraction, encapsulation

concurrency: technique of executing relatively independent tasks in parallel to save run time

James gosling - sun microsystems - 1995 - Java 1.0

object oriented - simple - secure - platform independent - architecture neutral - robust - portable - multithreaded - interpreted - high performance - distributed - dynamic

platform independent byte code is interpreted by java virtual machine.

pointers - operator overloading - multiple inheritance - explicit memory allocation

static member can be accessed without creating the object of the class.

Boolean - byte - char - double - float - int - long - short

Non access modifiers: static - final - abstract - synchronized

this - reference to the object of the current class

simulate `finalize()` using `System.gc()` explicitly. 

aggregation - HAS A relationship - A class has another class reference as its data member. `classRef.anotherClassRef.property -> student.address.street` 

