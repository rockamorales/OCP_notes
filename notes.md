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

according to the content it can be only accessed thru the interface type only. not sure about thru instances of the implementer

Abtract methods can override a default method and a default method can override an abstract method

Static methods can be hidden by create a method with the same signature in the subinterface that can be either static, default or abstract

All fields declared in an interfaces are static and final even if those modifiers/keywords are not specified

Be ware of the modifiers and default behavior. Interfaces methods are by default public, classes methods are by default package. when overridden a method, the overridding method cannot be more restrictive than the method it overrides. So if two methods one declared in class and other declared in an interface have no access modifier specified. they are actually having different access restrictions (be wary of this)

#
