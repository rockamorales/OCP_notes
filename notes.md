# Primitive datatypes

## Autoboxing rules
## Overriding methods with primitive datatypes are return types
## Overriding methods with primitives data type when autoboxing applies
## 

# Rules of overridden
### About return types
?
### About exceptions
?


# Questions:

### Can static classes have a non-static method?
### Can static classes have a constructor?
### What is the purpose of static classes?

# Interfaces
Interfaces can be considered contracts that rule how software components interact. In the java programming language, interfaces are reference types that can be implemented by clases and extended by other interfaces, but cannot be instantiated

can contains abstract, default and static methods. 

#### Static methods can be hidden by the implementer. So does it means that static method is also accessible thru the implementer instance or class reference? 

* according to the content it can be only accessed thru the interface type only. not sure about thru instances of the implementer

* Abtract methods can override a default method and a default method can override an abstract method

* Static methods can be hidden by create a method with the same signature in the subinterface that can be either static, default or abstract

* All fields declared in an interfaces are static and final even if those modifiers/keywords are not specified

* Be aware of the modifiers and default behavior. Interfaces methods are by default public, classes methods are by default package. when overridden a method, the overridding method cannot be more restrictive than the method it overrides. So if two methods one declared in class and other declared in an interface have no access modifier specified. they are actually having different access restrictions (be wary of this)

* A static method cannot override a non-static method.

* A non-static method can hide a static method but not override it.

# Lambda Expressions
* Functional interfaces are interfaces consisting of a single abstract method. 
* Java 8 API provides an informative annotation, @FunctionalInterface, to indicate that the annotated type is intended to be a functional interface
* Even when the @FunctionalInterface annotation is not specified the compiler will still treat the interface as functional if it contains only one abstract method
* Can contains default and static methods. as long as the interface only has one abstract method, it will be treated as functional interface
* Lambda expressions are a consice construct providing implementations for functional interfaces, allowing you to treat functionality as data
* it consists of three elements
  1. A comma-separated list of formal parameters, enclosed in parentheses
  2. The arrow token (->)
  3. A body, which consists of a single expression or a statement block
* Can take any number of arguments
* Parameter types can be explicitly declared or inferred from the context; as long as the compiler can determine the type of a lambda exression, you don't need to specify the types of the expression's parameters
* The number of parameters of a lambda expression must match that of the corresponding functional interfaces's method.
* If the body of a lambda expression consists of only a single statement, the enclosing curly brackets can be left off; in that case, the ending semicolon of the statement and the return keyword, if any, must also be removed.
* The type is determine by the context where it is used
* Supporting contexts:
  - Variable assignments
  - Return statements
  - Array initializers
  - Method/constructor arguments
  - Lambda expression bodies
  - Conditional expressions,
  - Ternary operators (? :)
  - Cast expressions
* when using a lambda expression in place of a functional interface parameter types of the expression must be exactly the same as types of the interfaces methods. this means that even related types cannot be replacing the functional interface method defined parameters (primitive vs wrappers | supertype vs subtype)

# Generics
* Allows a stronger type checks at compile time
* Elimination of casting
* Enabling you to implement generic algorithms on collections

 ### Defining a Generic class
 ```
 modifiers class class-name<T1, T2,..., Tn>{ /* Class body*/}
 ```
 ### referencing a Generic class
  ```
    Person<String, Integer> person;
    // Instantiating the class
    Person<String, Integer> person = new Person<String, Integer>();
    //As of java SE 7
    Person<String, Integer> person = new Person<>();
  ```
### Bounded Type Parameters
* To declare a bouded type parameters, specify the type parameter's name, then the extends keyword and the upper bound
```
  public class Persona<S, T extends Number>{
    private S name;
    private T age;
    public Person (S name, T age){
      this.name = name;
      this.age = age;
    }
    public S getName(){return name;}
    public int getAge(){ return age.intValue(); }
  }
  
```
* Two generic class are considered superclass and subclass of each other if their raw types are in the same inheritance chain and the type arguements are no different

# Create and use Objects of Several Collection Subtypes
## ArrayList
  * Is a resizable-array implementation of the List interface
  * When elements are added to an ArrayList instance, its capacity grows automatically
  * The ArrayList offers constant time for the _size_, _isEmpty_, _get_, _set_, _iterator_, and _listIterator_ operations, amortized constant time for the add operation, and linear time for the others
### Constructors
  * ``` ArrayList() ```: contructs and empty list with the initial capacity of ten
  * ``` ArrayList(int initialCapacity) ``` : Contructs an empty list with the specified initial capacity
  * ``` ArrayList(Collection<? extends E> c) ``` : Constructs a list containing the elements of the specified collection, in the order they are returned by the collection's iterator
### Methods specified in the List interface
  * _add_: Inserts an element to the list
  * _set_: Replaces the element at the specified position in the list with the specified element
  * _remove_: Removes an element from the list
  * _get_: Returns the element at the specified position in the list
  * _indexOf_: Returns the index of the first ocurrence of the specified element in the list (-1 if the list does not contain the element)
  * _listIterator_: Returns a list iterator over the elements in the list
### ArrayList specific methods
  * ensureCapacity: Increases the capacity of the list, if necessary, to ensure that it can hold at least the number of elements specified by the minimun capacity argument
  * trimToSize: Trims the capacity of the list ot its current size
  * **default capacity is 10**
## TreeSet 
  * An implementation of the Set interface that sorts elements based on their ordering
  * Elements of the TreeSet instance are ordered using their natural ordering, or by a Comparator provided at creation time, depending on which constructor is used
  * The ordering maintained by a TreeSet instance should be consistent with the _equals_ method
  ### Creating TreeSet
    * ```TreeSet()```: Constructs a new, empty tree set, sorted according to the natural ordering of its elements
    * ```TreeSet(SortedSet<E> s```: Constructs a new tree set containing the same elements and using the same ordering as the specified sorted set
    * ```TreeSet(Collection<? extends E> c)```: Construnct a new tree set containing elements in the specified collection, sorted according to the antural ordering of its elements
    * ```TreeSet(Comparator<? super E> comparator)```: Construnct a new, empty tree set sorted according to the specified comparator
    
