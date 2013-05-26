**1. What do you mean by implicit conversion?**  
***Ans:*** Whenever data types are mixed in an expression then c++ performs the conversion automatically.  
Here smaller type is converted to wider type.  
Ex- in case of integer and float integer is converted into float type.


**2. What is the difference between method overloading and method overriding?**  
***Ans:*** Overloading a method (or function) in C++ is the ability for functions of the same name to be defined as long as these methods have different signatures (different set of parameters). Method overriding is the ability of the inherited class rewriting the virtual method of the base class.


**3. Inline function **  
***Ans:*** An inline function is a function that is expanded inline when invoked.ie. the compiler replaces the function call with the corresponding function code. An inline function is a function that is expanded in line when it is invoked. That is the compiler replaces the function call with the corresponding function code(similar to macro).


**4. Static method **  
***Ans:*** By using the static method there is no need creating an object of that class to use that method. We can directly call that method on that class. For example, say class A has static function f(), then we can call f() function as A.f(). There is no need of creating an object of class A.


**5. Differentiate between a template class and class template? **  
___Ans:___  
**Template class**: A generic definition or a parameterized class not instantiated until the client provides the needed information. It’s jargon for plain templates.
**Class template**: A class template specifies how individual classes can be constructed much like the way a class specifies how individual objects can be constructed. It’s jargon for plain classes.


**6. How to handle exception? **  
___Ans:___ Yes we can handle exception in C++ using keyword :**try**, **catch** and **throw**. Program statements that we want to monitor for exceptions are contained in a try block. If an exception occurs within the try block,it is thrown (using throw).The exception is caught,using catch,and processed.