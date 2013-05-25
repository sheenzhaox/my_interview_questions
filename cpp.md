Q: How do you link a C++ program to C functions?

A: By using the extern "C" linkage specification around the C function declarations.


Q: Explain the scope resolution operator.


A: It permits a program to reference an identifier in the global scope that has been hidden by another identifier with the same name in the local scope.

Q: What are the differences between a C++ struct and C++ class?

A: The default member and base-class access specifiers are different.

Q: How many ways are there to initialize an int with a constant?

A: Two.

There are two formats for initializers in C++ as shown in the example that follows. The first format uses the traditional C notation. The second format uses constructor notation.

int foo = 123;

int bar (123);

Q: How does throwing and catching exceptions differ from using setjmp and longjmp?

A: The throw operation calls the destructors for automatic objects instantiated since entry to the try block.

Q: What is your reaction to this line of code?

delete this;

A: It’s not a good practice.

Q: What is a default constructor?

A: A constructor that has no arguments.

Q: What is a conversion constructor?

A: A constructor that accepts one argument of a different type.

Q: What is the difference between a copy constructor and an overloaded assignment operator?

A: A copy constructor constructs a new object by using the content of the argument object. An overloaded assignment operator assigns the contents of an existing object to another existing object of the same class.

Q: When should you use multiple inheritance?

A: There are three acceptable answers: "Never," "Rarely," and "When the problem domain cannot be accurately modeled any other way."

Q: What is a virtual destructor?

A: The simple answer is that a virtual destructor is one that is declared with the virtual attribute.

Q: Explain the ISA and HASA class relationships. How would you implement each in a class design?

A: A specialized class "is" a specialization of another class and, therefore, has the ISA relationship with the other class. An Employee ISA Person. This relationship is best implemented with inheritance. Employee is derived from Person. A class may have an instance of another class. For example, an employee "has" a salary, therefore the Employee class has the HASA relationship with the Salary class. This relationship is best implemented by embedding an object of the Salary class in the Employee class.

Q: When is a template a better solution than a base class?

A: When you are designing a generic class to contain or otherwise manage objects of other types, when the format and behavior of those other types are unimportant to their containment or management, and particularly when those other types are unknown (thus, the genericity) to the designer of the container or manager class.

Q: What is a mutable member?

A: One that can be modified by the class even when the object of the class or the member function doing the modification is const.

Q: What is an explicit constructor?

A: A conversion constructor declared with the explicit keyword. The compiler does not use an explicit constructor to implement an implied conversion of types. It’s purpose is reserved explicitly for construction.

Q: What is the Standard Template Library?

A: A library of container templates approved by the ANSI committee for inclusion in the standard C++ specification.

A programmer who then launches into a discussion of the generic programming model, iterators, allocators, algorithms, and such, has a higher than average understanding of the new technology that STL brings to C++ programming.

Q: Describe run-time type identification.

A: The ability to determine at run time the type of an object by using the typeid operator or the dynamic_cast operator.

Q: What problem does the namespace feature solve?

A: Multiple providers of libraries might use common global identifiers causing a name collision when an application tries to link with two or more such libraries. The namespace feature surrounds a library’s external declarations with a unique namespace that eliminates the potential for those collisions.

This solution assumes that two library vendors don’t use the same namespace identifier, of course.

Q: Are there any new intrinsic (built-in) data types?

A: Yes. The ANSI committee added the bool intrinsic type and its true and false value keywords.

