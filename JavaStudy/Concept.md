Java pass by value  
It is always pass by value in Java

* Primitives, primitive wrapper class, class
* What happed when you pass them to a method
  * Primitives are passed by value  
  * Primitives wrapper class's reference will be passed to a method by value  
  * Class instance reference will be passed to a method by value

* However, I can change the class instance's value by its reference, but not primitive wrapper class'. Because primitive wrapper classes are immutable. 
* An immutable object is an object whose internal state remains constant after it has been entirely created.\
When you try to change the value of a immutable class, a new object will be created