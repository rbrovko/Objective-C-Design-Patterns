#### Design patterns will be based off of my own knowledge, ___Cocoa Design Patterns___ by Eric Buck, and ___PRO Objective-C Design Patterns___

------

#### Index:
- [Object Creation](###Object-Creation)
- [Interface Adaptation](#Interface-Adaptation)
- [Decoupling of Objects][]
- [Abstract Collection][]
- [Behavioral Extension][]
- [Algorithm Encapsulation][]
- [Performance and Object Access][]
- [State of the Object][]

------

###Object-Creation 
------

1. **Prototype**: The Protoype design pattern is one of the easiest design patterns to implement. A client knows an abstract Prototype Class. At runtime any object that is a subclass of the abstract prototype can be cloned at the client's will. So the client can make multiple instances of the same type without creating them manually. It's handy in the following use cases:
	* We need to create objects that should be independent of what they are and how they are created
	* Classes to be instantiated are determined at runtime
	* We don't want to have a hierarchy of factories for a corresponding hierarchy of problems
    * The differences between instances of different classes are just a few combinations of state. Then it's more conveinent to clone a corresponding number of prototypes rather than instatiating them manually
    * Classes are not easy to create, such as compositie objects in which each component can have other components as children. I'd be easier to clone _existing_ compositie objects and modify the copies
    * **bottom line** is to make a _true copy_ of an object so that we can use it as a basis (prototype) for something else related in the same context
    
    ##### Using the Prototype Pattern
    To use the Prototype pattern, try implementing the `<NSCopying>` protocol, which requires using the `- (id)copyWithZone:(NSZone *)zone` method. Remember that the NSObject protocol doesn't have a copy method declared, but NSObject does Here's an example
    ``` 
    -(id)copyWithZone:(NSZone *)zone{
    		Stroke *strokeCopy = [[[self class] allocWithZone:zone] init];
            [strokeCopy setSize:size_];
    		return strokeCopy;
        }
    ```
    ##### Summary
    The prototype pattern is one of the simplest and easiest patterns for object creation. This pattern is good for understanding the differences between shallow and deep copying
    
    ------
    
2. **Factory Method**: Unilke what we have seen from the Prototype Pattern, the Factory method is a creation pattern that doesn't use a copy method to create the same type of object. Rather, it uses a method that decides what type of object to create. It is particularly useful for framework designers.

	In the Factory method, there are 2 abstractions to make: the _factory_ is the creator and the "_producer_" is the magic word needed for the factory to create somehthing. The Factory Method pattern is useful in the following scenarios
	* The exact class of the objects created can't be anticipated at compile time
    * A class wants its subclasses to decide what to create at runtime
    * A class has some helper classes as its subclasses and you want to localize the knowledge of which one to return


	#####So what _is_ a Factory method pattern?
	A factory method pattern is also called a virtual constructor. It's useful when a class can't anticipate the class of objects it must create and wants its subclasses to specify the objects it creates. In short, you define an **interface** for creating an object, but you let the _subclasses_ decide which class to instantiate. You are thus deferring isntantiation to the subclasses.
    
    #####Example
    
    #####Summary
    Use a factory method to decouple application-specific classes from you code. This happens through class inheritance.
    
    ------

3. **Abstract Factory**
	When I think of an Abstract Factory, I like to think of a pizza chef. There are many styles of pizza to make. Pepperoni, New York Style, Chicago Style, etc. But the point is, that at the end of the idea, that there are some basic characteristics that all pizza should share. So pizza is a food with a high level perspective, aka an _abstract food type_. In software, if a client wants to create an object of a class manually, then the client needs to know the details of the class in question to create it. 
    This can be solved by using the _Abstract Factory Pattern_, which is good for providing a consistent interface for creating families of related or dependent objects without specifying their concrete classes or any details about how to create them. The client is decoupled from any of the specifics of concrete objects obtained from the factory.

| Abstract Factory        | Factory Method           | 
| ------------- |:-------------:| 
| Abstract product creation through object composition      | Abstract product creation through class inheritance | 
| Creates families of products      | Creates one type of product      |   
| The parent interface needs to be changed for supporting new products | Subclass the Creator and override the factory method to create new products     |   

	------
    
4. **Builder**

    ------
    
5. **Singleton**

	------
    
###Interface Adaptation
------
- **Adapter**
- **Bridge**
- **Façade**

###Decoupling of Objects
------
- **Mediator**
- **Observer**

###Abstract Collection
------
- **Composite**
- **Iterator**

###Behavioral Extension
------
- **Visitor**
- **Decorator**
- **Chain of Responsibility**

###Algorithm Encapsulation
------
- **Template Method**
- **Strategy**
- **Command**

###Performance and Object Access
------
- **Flyweight**
- **Proxy**

###State of the Object
- **Memento**
