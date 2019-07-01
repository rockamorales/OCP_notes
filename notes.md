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
 ``` java
 modifiers class class-name<T1, T2,..., Tn>{ /* Class body*/}
 ```
 ### referencing a Generic class
  ``` java
    Person<String, Integer> person;
    // Instantiating the class
    Person<String, Integer> person = new Person<String, Integer>();
    //As of java SE 7
    Person<String, Integer> person = new Person<>();
  ```
### Bounded Type Parameters
* To declare a bouded type parameters, specify the type parameter's name, then the extends keyword and the upper bound
``` java
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
  * As an implementation of a Set it does not accept duplicate elements ???
  * An implementation of the Set interface that sorts elements based on their ordering
  * Elements of the TreeSet instance are ordered using their natural ordering, or by a Comparator provided at creation time, depending on which constructor is used
  * The ordering maintained by a TreeSet instance should be consistent with the _equals_ method
  ### Creating TreeSet
  * ```  TreeSet() ```: Constructs a new, empty tree set, sorted according to the natural ordering of its elements
  * ``` TreeSet(SortedSet<E> s) ``` : Constructs a new tree set containing the same elements and using the same ordering as the specified sorted set
  * ``` TreeSet(Collection<? extends E> c) ``` : Construnct a new tree set containing elements in the specified collection, sorted according to the natural ordering of its elements
  * ``` TreeSet(Comparator<? super E> comparator) ``` : Construct a new, empty tree set sorted according to the specified comparator
  ### Methods specified in the Set Interface
  * _add_: Adds ethe specified element to the set if it is not already present, returns a boolean value indicating whether the element was added or not 
  * _remove_: Removes the specified element from the set if it is present, and returns a bolean value indicating whether the element is present
  * _contains_: Returns true if the set contains the specified element
  * _iterator_: Returns an iterator over elements in the set in ascending order
  ### TreeSet specific methods
  * _ceiling_: Returns the least element in the set greater than or equal to the specified element, or null if there is no such element
  * _floor_: Returns the greatest element in the set less than or equal to the specified element
  * _headSet_: Returns a view of the portion of the set whose elements are less than the specified element
  * _tailSet_: Returns a view of the portion of the set whose elements are greater than the specified element
  * _descendingIterator_: Returns an iterator over elements in the set in descending order
  * _comparator_: Returns the comparator used to order elements in the set or null if the TreeSet is using the natural order

## TreeMap
  * Is an implementation of the Map interface
  * Elements of the TreeMap instance are ordered using the natural ordering of their key, or by a Comparator provided at creation time, depending on which constructor is used
  * The ordering maintained by a TreeMap instance should be consistent with the equals method
### Constructors
 * ``` TreeMap() ```: Creates a new, empty tree map, using the natural ordering of its keys
 * ``` TreeMap(SortedMap<K, ? extends V> m) ```: Constructs a new tree map containing the same mappings and using the same ordering as the specified sorted map
 * ``` TreeMap(Map<? extends K, ? extends V> m) ```: Constructs a new tree map containing the same mappings as the given map, ordered according to the natural ordering of its keys
 * ``` TreeMap(Comprator<? super K> comparator) ```: Constructs a new, empty tree map, ordered according to the given comparator
### Methods specified in the Map interface
  * _put_: Associates the specified value with the specified key in the map
  * _replace_: Replaces the entry for the specified key. Overloaded, two methods, method with one value parameter will replace the entry if it is currently mapped to any value, while the method with two parameters replaces the entry only if the key is currently mapped to the specified value in the second parameter
  * _remove_: remove the mapping for the specified key from the map. There are two overloaded version. the one that has only one parameter, removes the entry when the specified key exists, the one with two parameters removes the entry only if the key is mapped to the specified value.
  * _get_: Returns the value to which the specified key is mapped
  * _containsKey_: Returns true if the map contains a mapping for the specified key
  * _containsValue_: Returns true if the map maps one or more keys to the specified value
  * _entrySet_: Returns a Set view of the mappings contained in the map
  * _keySet_: Returns a Set view of the keys contained in the map
  * _values_: Returns a collection view of the values contained in the map
  * _ceilingEntry_: Returns a key-value mapping associated with the least key grester than or equal to the specified key
  * _floorEntry_: Returns a key-value mapping associated with the greatest key  less than or equal to the specified key
  * _descendingMap_: Returns a reverse order view of the mappings contained in the map
  * _comparator_: Returns the comparator used to order the keys in the map or null if map is using natural order to order the keys

## ArrayDeque
  * Is a resizable-array implementation of the Deque interface, supporting insertion, removal and retrieval of elements at both ends
  * Most ArrayDeque operations run in amortized constant time
  * ArrayDeque instances have no capacity restrictions, their capacity grows automatically to support usage
### Constructors
  * ``` ArrayDeque() ```: constructs an empty array deque with an initial capacity sufficient to hold 16 elements
  * ``` ArrayDeque(int numElements) ```: Constructs an empty array deque with an initial capacity sufficient to hold the specified number of elements
  * ``` ArrayDeque(Collection<? extends E> c) ```: Constructs a deque containing elements of the specified collection, in the order they are returned by the collection's iterator
### Methods specified in Deque interface
* _add*_: Inserts the specified element to the deque
* _remove*_: Removes the specified element from the deque
* _get*_: Returns the element at the specified position in the deque
* _peek*_: Retrieves, but does not remove, the first/last element of the deque
* _poll*_: Retrieves and removes the first/last element of the deque
* _offer*_: Inserts the speficied element at the begining or the end of the deque
* _iterator_: Returns an iterator over the elements in the deque
* _descendingIterator_: Returns an iterator over the elements in the deque in revers sequential order


 # Comparable and Comparator Interfaces
 ## Comparable
 * Imposed a total ordering on objects of an implementation class
 * defines a single method
  ``` java
    int compareTo(T object)
  ```
  * Objects of a class implementing the Comparable interface can be sorted in a collection or array
  * The behavior of the _compareTo_ and equal method should be consistent
  
  ``` java
    public class Person implements Comparable<Person> {
      private String name;
      private int age;
      public Person(String name, int age){
        this.name = name;
        this.age = age;
    }
    public String getName(){ return this.name; }
    public int getAge(){ return this.age; }
    public int compareTo(Person person){
      int comp = this.name.compareTo(person.name);
      return comp != 0 ? comp: person.age - this.age;
    }
  ```

  ## Comparator Interface
  * The Comparator interface imposes a total ordering on objects in a collection or array
  * The Comparator interface has only one abstract method:
    ``` java
      int compare(T object1, T object2);
    ```
  * An instance of a Comparator implementation class can be used to control the order of elements in a collection or Array
  * The behavior of the compare and equals method should be consistent
    
  ## Comparable vs Comparator
  * Both Comparable and Comparator are comparison functions comparing objects of the same type
  * Comparable is internal to objects in comparison, while Comparator is external
  **Scenarios where comparator is better than Comparable**
    * You don't have control over the source code of the class whose instances are compared
    * You want to compare objects in different ways
    
# Collections, Streams and Filters
  ## Predicate
   * In programming, a predicatet is an expression that evaluates to a boolean value
   * The Java SE 8 API defines a functional interface, named _Predicate_, often used for filtering operations; this interface has a single abstract method:
   ``` java
    booleean test(T t)
   ```
 ## Filtering Collection Elements
   * You can filter elements of a collection using the _removeIf_ method, a default method of the Colletion interface
   * The _removeIf_ method takes a Predicate argument and removes all elements of the collection that satisfy the specified predicate:
   ``` java
    boolean removeIf(Predicate<? super E> filter)
   ```
   * _Predicate_ is a functional interface, thus you can use a lambda expresion as the argument to the removeIf method
   **Example**
   ``` java
   Collection<Integer> collection = new ArrayList<>();
   collection.add(1); collection.add(2);
   collection.add(3); collection.add(4);
   collection.removeIf(new Predicate<Integer>(){
    public boolean test(Integer i){
      return i % 2 == 0;
    }
   }
   for (Integer number : collection) {
    System.out.println(number);
   }
   ```
 ## Filtering Stream Elements
  * You can filter elements of a Stream using the _filter_ method, which takes a _Predicate_ argument and returns a stream consisting of elements that match the specified predicate:
  ``` java
   Stream<T> filter (Predicate<? super T> predicate);
  ```
  * Similar to filtering elements of a collection, the _Predicate_ argument to the _filter_ method can be represented by a lambda expression
  * The _filter_ method is an intermediate operation, hence it needs to be followed by a terminal operation
  
  **Example**
  ``` java
    Stream<Integer> originalStream = Stream.of(0, -1, 1, -2, 2);
    Stream<Integer> filteredStream = originalStream.filter(i -> i > 0);
    filteredStream.forEach(i -> System.out.println(i));
  ```
  * Predicate is a generic interface, so it should be used specifying the type it will apply for. If type is not specified then Object is taken by default, which means that the order to override the test method from Predicate interface, test method should have Object type as parameter, if it has any other type, we are not overriding the test method defined in predicate, so code will fails to compile
  

# Iterate Using forEach Methods of Stream and List
## The Consumer interface
  * The _Consumer_ interface represents an operation that accepts a single inut argument and returns no result
  * Abstract method signature:
  ``` java
  void accept(T t);
  ```
  * _Consumer_ is a functional interface, thus its implementation can be represented by a lambda expression

## The Stream.forEach method 
  * method has a _Consumer_ parameter that acts on each element of the stream:
    ``` java
      void forEach(Consumer<? super T> action);
    ```
   * This method is a terminal operation, consuming the stream
   * The behavior of this method is nondeterministic
## List.forEach Method
   * The forEach method in the _List_ interface is a default method inherited from the Iterable interface with the signature:
     ``` java
      void forEach(Consumer<? super T> action)
     ```
   * This method performs the specified action on each element of the _List_
   * The behavior of this smethod is deterministic
   
# Stream Interface and Stream Pipeline
## The Stream Interface
  * Reprensents a sequence of elements and supports aggregate operations
  * A Stream instance can be created by a statuc method in the _Stream_ interface, or by a stream creation method invoked on a data source; a stram can be operated on only once
  * The source of a stream should not be modified while the stream is being processed
  * Operations on a stream are divided into intermediate and terminal operations, and combined into a stream pipeline
  * Intermediate operations return a new Stream; these operations are lazy and only triggered when the terminal operation is initiated
  * A terminal operation may traverse the stream to produce a result or a side-effect; after the terminal operation is performed, the stream pipeline is considered consumed. To use the stream again, you have to generate other stream from its original data source.
 
 **Example**
 ``` java
 Collection<Integer> collection = Arrays.asList(1,2,3,4,5,6);
 Stream<Integer> stream = collection.stream();
 stream.filter(i -> i%2 == 0).filter( i -> i%3 == 0).forEach(i -> System.out.println(i));
 ```
  * _forEach_ is pipeline terminal operation
  
  # Filtering a collection by using Lambda Expressions
  
