# Method Dispatch
Is the algorithm used to decide which method should be called in response to a message. The goal is to inform the CPU where it can find the executable code. It will be used for Object Oriented systems that needs a memory reference to classes that inherit implementations from other classes. The **METHOD DISPATCH** will be used for nested subclasses (when the parent class inherit other class)
## Compiled programming languages have three primary methods of dispatch.
* **STATIC DISPATCH(or direct dispatch)**: fastest style of method dispatch. While building(building time) the compiler already knows what to call and when. Can NOT be used with subclasses. 
* **TABLE DISPATCH(or dynamic dispatch)**: Every class has a table with pointers and functions. Every subclass has its copy of the table with a different function pointer for the methods that the class overriden. When sublaclasses add new methods, those methods are appended to the end of this array. The table is consulted at runtime to determine the method to run. Is the functiolality that consults the class table to knows when to have a copy or a new pointer when we use subclasses.
* **MESSAGE DISPATCH**: When you have a class which is a subclass of some class, whitch a subclass of some other class, the app will decide at **RUNTIME** what method of which parent it should use. Pure Swift classes don´t normally use message dispatch, it is a **OBJECTIVE-C** concept. We need to use *DYNAMIC* to enforce the message dispatch on the property or method. Extension methods always use static dispatch (they can´t be overriden). Adding dynamic to their declaration allows us overriding.


## Increasing performance by reducing Dynamic Dispatch (Table Dispatch).
* Use **FINAL** when you know that a declaration does not need to be overriden: The final keyword is a restriction on a class, method or property that indicates that the declaration can not be overriden. This allows the compiler to safely forget the dynamic dispatch.
* Apply the **PRIVATE** keyword: restricts the visibility of the declaration to the current file. This allows the compiler to find all potentially overriding declarations.
* Use **MODULE OPTIMIZATION**: all declarations with internal access (default) will be compiled as a single module instead of separated modules for each class. This allows a compiler to use final type on all methods with no overrides.
