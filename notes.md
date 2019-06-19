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
