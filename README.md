# Method Dispatch
Is the algorithm used to decide which method should be called in response to a message. The goal is to inform the CPU where it can find the executable code.
## Compiled programming languages have three primary methods of dispatch.
* **STATIC DISPATCH(or direct dispatch)**: fastest style of method dispatch. While building(building time) the compiler already knows what to call and when. Can NOT be used with subclasses. 
* **TABLE DISPATCH(or dynamic dispatch)**: Every class has a table with pointers and functions. Every subclass has its copy of the table with a different function pointer for the methods that the class overriden. When sublaclasses add new methods, those methods are appended to the end of this array. The table is consulted at runtime to determine the method to run. Is the functiolality that consults the class table to knows when to have a copy or a new pointer when we use subclasses.
