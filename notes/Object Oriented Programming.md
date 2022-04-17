<h1>Object Oriented Programming</h1>
- the four basic principles of OOP
	- Encapsulation: 
		- ensures bundling of data and the methods operating on that data into a single unit. refers to the ability of an object to hide the internal structure of it's properties and methods.
	- Data abstraction: 
		- Means that objects should provide the simplified, abstract version of their implementation
		- interfaces from java
			- provides a structure, it is an abstract class with no body
``` Interface
interface Animal {
  public void animalSound(); // interface method (does not have a body)
  public void sleep(); // interface method (does not have a body)
}

// Pig "implements" the Animal interface
class Pig implements Animal {
  public void animalSound() {
    // The body of animalSound() is provided here
    System.out.println("The pig says: wee wee");
  }
  public void sleep() {
    // The body of sleep() is provided here
    System.out.println("Zzz");
  }
} 
```
- Polymorphism
	- all subclasses inherit methods and attributes
	- Many forms
- Inheritance
	- code reusability
	- subClasses can have other classes inherit traits from the original class
	- 
