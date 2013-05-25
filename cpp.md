Q: How do you link a C++ program to C functions?

A: By using the **extern "C"** linkage specification around the C function declarations.


Q: Explain the scope resolution operator.

A: It permits a program to reference an identifier in the global scope that has been hidden by another identifier with the same name in the local scope.

Q: What are the differences between a C++ struct and C++ class?

A: The default member and base-class access specifiers are different.

Q: How many ways are there to initialize an int with a constant?

A: Two.

There are two formats for initializers in C++ as shown in the example that follows. The first format uses the traditional C notation. The second format uses constructor notation.
```C++
int foo = 123;

int bar (123);
```

Q: How does throwing and catching exceptions differ from using setjmp and longjmp?

A: The throw operation calls the destructors for automatic objects instantiated since entry to the try block.

Q: What is your reaction to this line of code?
```C++
delete this;
```

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



##[My Interview Questions](http://codingproblem.blogspot.com.au/2011/01/my-interview-questions.html)

by ANAND RAI  MAY 25, 2013


You can visit below wbsite for your Interview preparation.
www.cplusplus.com
http://www.geeksforgeeks.org
http://www.java2s.com
http://c-faq.com

* what is copy constructor, and where it's require?

A copy constructor is a special constructor in the C++ programming language used to create a new object as a copy of an existing object. The first argument of such a constructor is a reference to an object of the same type as is being constructed (const or non-const), which might be followed by parameters of any type (all having default values).

Normally the compiler automatically creates a copy constructor for each class (known as a default copy constructor) but for special cases the programmer creates the copy constructor, known as a user-defined copy constructor. In such cases, the compiler does not create one.

A user-defined copy constructor is generally needed when an object owns pointers or non-shareable references, such as to a file, in which case a destructor and an assignment operator should also be written (Rule of three).

```c++
X (const X& copy_from_me);

X (X& copy_from_me);

X (const volatile X& copy_from_me);

X (volatile X& copy_from_me);

X (const X& copy_from_me, int = 10);

X (const X& copy_from_me, double = 1.0, int = 40);
```

The following cases may result in a call to a copy constructor:


When an object is returned by value

When an object is passed (to a function) by value as an argument

When an object is thrown

When an object is caught

When an object is placed in a brace-enclosed initializer list

These cases are collectively called copy-initialization and are equivalent to:T x = a;

The copy assignment operator differs from the copy constructor in that it must clean up the data members of the assignment's target (and correctly handle self-assignment) whereas the copy constructor assigns values to uninitialized data members.

My_Array first;                // initialization by default constructor

My_Array second(first);   // initialization by copy constructor

My_Array third = first;     // Also initialization by copy constructor

second = third;                 // assignment by copy assignment operator




what 's difference between calloc and malloc ?

Last 14 Mar 2011(004)

http://c-faq.com/malloc/calloc.html

calloc(m, n) is essentially equivalent to



p = malloc(m * n);

+
memset(p, 0, m * n);



There is no important difference between the two other than the number of arguments and the zero fill.

Malloc:

Allocates a block of size bytes of memory, returning a pointer to the beginning of the block.

The content of the newly allocated block of memory is not initialized, remaining with indeterminate values.

Calloc:

Allocate space for array in memory

Allocates a block of memory for an array of num elements, each of them size bytes long, and initializes all its bits to zero.

The effective result is the allocation of an zero-initialized memory block of (num * size) bytes.



Last 16 Mar 2011(002)

A reference variable is an alias, that is, another name for an already existing variable. Once a reference is initialized with a variable, either the variable name or the reference name may be used to refer to the variable.

C++ References vs Pointers:

References are often confused with pointers but three major differences between references and pointers are:


You cannot have NULL references. You must always be able to assume that a reference is connected to a legitimate piece of storage.

Once a reference is initialized to an object, it cannot be changed to refer to another object. Pointers can be pointed to another object at any time.

A reference must be initialized when it is created. Pointers can be initialized at any time.

Creating References in C++:

Think of a variable name as a label attached to the variable's location in memory. You can then think of a reference as a second label attached to that memory location. Therefore, you can access the contents of the variable through either the original variable name or the reference. For example, suppose we have the following example:





We can declare reference variables for i as follows.





Read the & in these declarations as reference. Thus, read the first declaration as "r is an integer reference initialized to i" and read the second declaration as "s is a double reference initialized to d.". Following example makes use of references on int and double:



#include



using namespace std;



int main ()

 // declare simple variables

 int    i;

 double d;



 // declare reference variables

 int&    r = i;

 double& s = d;

 i = 5;

 cout << "Value of i : " << i << endl;

 cout << "Value of i reference : " << r  << endl;



 d = 11.7;

 cout << "Value of d : " << d << endl;

 cout << "Value of d reference : " << s  << endl;

 return 0;



When the above code is compiled together and executed, it produces following result:



Value of i : 5

Value of i reference : 5

Value of d : 11.7

Value of d reference : 11.7



References are usually used for function argument lists and function return values. So following are two important subjects related to C++ references which should be clear to a C++ programmer:






what is difference enum and union?

Last 14 Mar 2011(004)

Enumerations (enum)

Enumerations create new data types to contain something different that is not limited to the values fundamental data types may take. Its form is the following:



enum enumeration_name {
 value1,
 value2,
 value3,
 .
 .
} object_names;



For example, we could create a new type of variable called colors_t to store colors with the following declaration:



enum colors_t {black, blue, green, cyan, red, purple, yellow, white};



Notice that we do not include any fundamental data type in the declaration. To say it somehow, we have created a whole new data type from scratch without basing it on any other existing type. The possible values that variables of this new type color_t may take are the new constant values included within braces. For example, once the colors_t enumeration is declared the following expressions will be valid:



colors_t mycolor;
mycolor = blue;
if (mycolor == green) mycolor = red;



Enumerations are type compatible with numeric variables, so their constants are always assigned an integer numerical value internally. If it is not specified, the integer value equivalent to the first possible value is equivalent to 0 and the following ones follow a +1 progression.Thus, in our data type colors_t that we have defined above, black would be equivalent to 0, blue would be equivalent to 1, green to 2, and so on.



We can explicitly specify an integer value for any of the constant values that our enumerated type can take. If the constant value that follows it is not given an integer value, it is automatically assumed the same value as the previous one plus one. For example:



enum months_t { january=1, february, march, april, may, june, july, august, september, october, november, december} y2k;



In this case, variable y2k of enumerated type months_t can contain any of the 12 possible values that go from january to december and that are equivalent to values between 1 and 12 (not between 0 and 11, since we have made january equal to 1).



Unions

Unions allow one same portion of memory to be accessed as different data types, since all of them are in fact the same location in memory. Its declaration and use is similar to the one of structures but its functionality is totally different:



union union_name {
 member_type1 member_name1;
 member_type2 member_name2;
 member_type3 member_name3;
 .
 .
} object_names;



All the elements of the union declaration occupy the same physical space in memory. Its size is the one of the greatest element of the declaration. For example:



union mytypes_t {
 char c;
 int i;
 float f;
 } mytypes;



defines three elements:



mytypes.c
mytypes.i
mytypes.f



each one with a different data type. Since all of them are referring to the same location in memory, the modification of one of the elements will affect the value of all of them. We cannot store different values in them independent of each other.



What is virtual function?

Last 16 Mar 2011(005)

Virtual Functions

What is a Virtual Function?
A virtual function is a member function of a class, whose functionality can be over-ridden in its derived classes. It is one that is declared as virtual in the base class using the virtual keyword. The virtual nature is inherited in the subsequent derived classes and the virtual keyword need not be re-stated there. The whole function body can be replaced with a new set of implementation in the derived class.

What is Binding?
Binding refers to the act of associating an object or a class with its member. If we can call a method fn() on an object O of a class C, we say that the object O is binded with the method fn(). This happens at compile time and is known as static or compile - time binding. The calls to the virtual member functions are resolved during run-time. This mechanism is known as dynamic binding. The most prominent reason why a virtual function will be used is to have a different functionality in the derived class. The difference between a non-virtual member function and a virtual member function is, the non-virtual member functions are resolved at compile time.

How does a Virtual Function work?
Whenever a program has a virtual function declared, a V - table is constructed for the class. The v-table consists of addresses to the virtual functions for classes that contain one or more virtual functions. The object of the class containing the virtual function contains a virtual pointer that points to the base address of the virtual table in memory. Whenever there is a virtual function call, the v-table is used to resolve to the function address. An object of the class that contains one or more virtual functions contains a virtual pointer called the vptr at the very beginning of the object in the memory. Hence the size of the object in this case increases by the size of the pointer. This vptr contains the base address of the virtual table in memory. Note that virtual tables are class specific, i.e., there is only one virtual table for a class irrespective of the number of virtual functions it contains. This virtual table in turn contains the base addresses of one or more virtual functions of the class. At the time when a virtual function is called on an object, the vptr of that object provides the base address of the virtual table for that class in memory. This table is used to resolve the function call as it contains the addresses of all the virtual functions of that class. This is how dynamic binding is resolved during a virtual function call.

The following code shows how we can write a virtual function in C++ and then use the same to achieve dynamic or runtime polymorphism.



#include

class base

public:

virtual void display()

 cout<<”\nBase”;

class derived : public base

 public:

 void display()

    cout<<”\nDerived”;



void main()



 base *ptr = new derived();

 ptr->display();



In the above example, the pointer is of type base but it points to the derived class object. The method display() is virtual in nature. Hence in order to resolve the virtual method call, the context of the pointer is considered, i.e., the display method of the derived class is called and not that of the base. If the method was non virtual in nature, the display() method of the base class would have been called.

What is Virtual Constructors and Destructors
A constructor cannot be virtual because at the time when the constructor is invoked the virtual table would not be available in the memory. Hence we cannot have a virtual constructor.

A virtual destructor is one that is declared as virtual in the base class and is used to ensure that destructors are called in the proper order. It is to be remembered that destructors are called in the reverse order of inheritance. If a base class pointer points to a derived class object and we some time later use the delete operator to delete the object, then the derived class destructor is not called. Refer to the code that follows:



#include

class base

  public:

  ~base()





class derived : public base

  public:

  ~derived()



void main()



  base *ptr = new derived();

  // some code

  delete ptr;

In this case the type of the pointer would be considered. Hence as the pointer is of type base, the base class destructor would be called but the derived class destructor would not be called at all. The result is memory leak. In order to avoid this, we have to make the destructor virtual in the base class. This is shown in the example below:



#include

class base

public:

virtual ~base()





class derived : public base

  public:

  ~derived()







void main()



  base *ptr = new derived();

  // some code

  delete ptr;



Conclusion:

Virtual methods should be used judiciously as they are slow due to the overhead involved in searching the virtual table. They also increase the size of an object of a class by the size of a pointer. The size of a pointer depends on the size of an integer. Note that in DOS based systems the size of a pointer is 2 bytes whereas in UNIX based systems it is 4 bytes.



What is deep copy shallow copy difference?

Last 16 Mar 2011(004)

C++ Notes: Shallow vs Deep Copies

A shallow copy of an object copies all of the member field values. This works well if the fields are values, but may not be what you want for fields that point to dynamically allocated memory. The pointer will be copied. but the memory it points to will not be copied -- the field in both the original object and the copy will then point to the same dynamically allocated memory, which is not usually what you want. The default copy constructor and assignment operator make shallow copies.

A deep copy copies all fields, and makes copies of dynamically allocated memory pointed to by the fields. To make a deep copy, you must write a copy constructor and overload the assignment operator, otherwise the copy will point to the original, with disastrous consequences.

Deep copies need ...

If an object has pointers to dynamically allocated memory, and the dynamically allocated memory needs to be copied when the original object is copied, then a deep copy is required.

A class that requires deep copies generally needs:




class Vector

public:

  Vector() { x = 0; y = 0; } // Standard constructor



  Vector(const Vector& other) // Copy constructor

      x = other.x;

      y = other.y;



  Vector& operator=(const Vector& other) // Assignment operator

      x = other.x;

      y = other.y;



      return *this;



  // [Other member functions needed to make class useful]



private:

  int x, y;



void foo(Vector v)

  // [Some code here]



void bar()

  Vector v1; // v1 will be constructed by the standard constructor



  foo(v1); // The copy constructor will be used to create a copy of v1



  Vector v2 = v1; // v2 will typically be constructed by the copy constructor



  Vector v3;

  v3 = v1; // The assignment operator will be used here



What is friend function(also write a program )?

Last 10 Mar 2011(003)

http://www.cprogramming.com/tutorial/friends.html
http://www.java2s.com/Tutorial/Cpp/0180__Class/FriendClasses.htm
Friend Functions and Friend Classes

It is often useful for one class to see the private variables of another class, even though these variables should probably not be made part of the public interface that the class supports. For instance, if you were writing a binary tree, you might want to use a Node class that has private data, but it would still be convenient for the functions that actually combine nodes together to be able to access the data directly without having to work through the Node interface. At times, it may not even be appropriate for an accessor function to ever give even indirect access to the data.



Friend Classes

C++ provides the friend keyword to do just this. Inside a class, you can indicate that other classes (or simply functions) will have direct access to protected and private members of the class. When granting access to a class, you must specify that the access is granted for a class using the class keyword:





Note that friend declarations can go in either the public, private, or protected section of a class--it doesn't matter where they appear. In particular, specifying a friend in the section marked protected doesn't prevent the friend from also accessing private fields. Here is a more concrete example of declaring a friend:

class Node

  private:

  int data;

  int key;

  // ...



  friend class BinaryTree; // class BinaryTree can now access data directly



Now, Node does not need to provide any means of accessing the data stored in the tree. The BinaryTree class that will use the data is the only class that will ever need access to the data or key. (The BinaryTree class needs to use the key to order the tree, and it will be the gateway through which other classes can access data stored in any particular node.) Now in the BinaryTree class, you can treat the key and data fields as though they were public:



class BinaryTree

  private:

  Node *root;



  int find(int key);

int BinaryTree::find(int key)

  // check root for NULL...

  if(root->key == key)

      // no need to go through an accessor function

      return root->data;

  // perform rest of find



Friend Functions

Similarly, a class can grant access to its internal variables on a more selective basis--for instance, restricting access to only a single function. To do so, the entire function signature must be replicated after the friend specifier, including the return type of the function--and, of course, you'll need to give the scope of the function if it's inside another class:



friend return_type class_name::function(args);




For instance, in our example Node class, we would use this syntax:



class Node

  private:

  int data;

  int key;

  // ...



  friend int BinaryTree::find(); // Only BinaryTree's find function has access



Now the find function of BinaryTree could access the internals of the Node class, but no other function in BinaryTree could. (Though we might want a few others to be able to!) Note that when friends are specified within a class, this does not give the class itself access to the friend function. That function is not within the scope of the class; it's only an indication that the class will grant access to the function.

friend and Encapsulation

Some people believe that the idea of having friend classes violates the principle of encapsulation because it means that one class can get at the internals of another. One way to think about this, however, is that friend is simply part of a class's overall interface that it shows the world. Just like an elevator repairman has access to a different interface than an elevator rider, some classes or functions require expanded access to the internals of another class. Moreover, using friend allows a class to present a more restrictive interface to the outside world by hiding more details than may be needed by anything but the friends of the class. Finally, friends are particularly common in cases of operator overloading because it is often necessary for an overloaded operator to have access to the internals of the classes that are arguments to the operator.



Last 12 Jan 2011(001)

http://www.cplusplus.com/doc/tutorial/typecasting/

Type Casting

Converting an expression of a given type into another type is known as type-casting.

Implicit conversion

Implicit conversions do not require any operator. They are automatically performed when a value is copied to a compatible type. For example:



short a=2000;

int b;

b=a;



Explicit conversion

C++ is a strong-typed language. Many conversions, specially those that imply a different interpretation of the value, require an explicit conversion. We have already seen two notations for explicit type conversion: functional and c-like casting:



short a=2000;

int b;

b = (int) a; // c-like cast notation

b = int (a); // functional notation



The functionality of these explicit conversion operators is enough for most needs with fundamental data types. However, these operators can be applied indiscriminately on classes and pointers to classes, which can lead to code that while being syntactically correct can cause runtime errors. For example, the following code is syntactically correct:



In order to control these types of conversions between classes, we have four specific casting operators: dynamic_cast, reinterpret_cast, static_cast and const_cast. Their format is to follow the new type enclosed between angle-brackets (<>) and immediately after, the expression to be converted between parentheses.



dynamic_cast (expression)

reinterpret_cast (expression)

static_cast (expression)

const_cast (expression)



The traditional type-casting equivalents to these expressions would be:



(new_type) expression

new_type (expression)



but each one with its own special characteristics:

dynamic_cast



dynamic_cast can be used only with pointers and references to objects. Its purpose is to ensure that the result of the type conversion is a valid complete object of the requested class.



Therefore, dynamic_cast is always successful when we cast a class to one of its base classes:



class CBase { };

class CDerived: public CBase { };



CBase b; CBase* pb;

CDerived d; CDerived* pd;



pb = dynamic_cast(&d); // ok: derived-to-base

pd = dynamic_cast(&b); // wrong: base-to-derived




The second conversion in this piece of code would produce a compilation error since base-to-derived conversions are not allowed with dynamic_cast unless the base class is polymorphic.

contd...



what is singleton class(and how will u write this)?

Last 28 Mar 2011(005)

http://en.wikibooks.org/wiki/C%2B%2B_Programming/Code/Design_Patterns
Singleton

The term Singleton refers to an object that can only be instantiated once. This pattern is generally used where a global variable would have otherwise been used. The main advantage of the singleton is that its existence is guaranteed. Other advantages of the design pattern include the clarity, from the unique access, that the object used is not on the local stack. Some of the downfalls of the object include that, like a global variable, it can be hard to tell what chunk of code corrupted memory, when a bug is found, since everyone has access to it.



Let's take a look at how a Singleton differs from other variable types.

Like a global variable, the Singleton exists outside of the scope of any functions. Traditional implementation uses a static member function of the Singleton class, which will create a single instance of the Singleton class on the first call, and forever return that instance. The following code example illustrates the elements of a C++ singleton class, that simply stores a single string.



class StringSingleton

public:

// Some accessor functions for the class, itself

std::string GetString() const

{return mString;}

void SetString(const std::string &newStr)

{mString = newStr;}



// The magic function, which allows access to the class from anywhere

// To get the value of the instance of the class, call:

// StringSingleton::Instance().GetString();

static StringSingleton &Instance()

// This line only runs once, thus creating the only instance in existence

static StringSingleton *instance = new StringSingleton;

// dereferencing the variable here, saves the caller from having to use

// the arrow operator, and removes tempation to try and delete the

// returned instance.

return *instance; // always returns the same instance



private:

// We need to make some given functions private to finish the definition of the singleton

StringSingleton(){} // default constructor available only to members or friends of this class



// Note that the next two functions are not given bodies, thus any attempt

// to call them implicitly will return as compiler errors. This prevents

// accidental copying of the only instance of the class.

StringSingleton(const StringSingleton &old); // disallow copy constructor

const StringSingleton &operator=(const StringSingleton &old); //disallow assignment operator



// Note that although this should be allowed,

// some compilers may not implement private destructors

// This prevents others from deleting our one single instance, which was otherwise created on the heap

~StringSingleton(){}

private: // private data for an instance of this class

std::string mString;




whats a preprocessor in c?

Last 20 Dec 2010(002)

Preprocessor directives are lines included in the code of our programs that are not program statements but directives for the preprocessor. These lines are always preceded by a hash sign (#). The preprocessor is executed before the actual compilation of code begins, therefore the preprocessor digests all these directives before any code is generated by the statements.



These preprocessor directives extend only across a single line of code. As soon as a newline character is found, the preprocessor directive is considered to end. No semicolon (;) is expected at the end of a preprocessor directive. The only way a preprocessor directive can extend through more than one line is by preceding the newline character at the end of the line by a backslash (\).



macro definitions (#define, #undef)

Conditional inclusions (#ifdef, #ifndef, #if, #endif, #else and #elif)

Line control (#line)

Error directive (#error)

Source file inclusion (#include)

Pragma directive (#pragma)



what are all Program compilation steps in c language?

Last 20 Dec 2010(002)

http://www.cprogramming.com/compilingandlinking.html

When programmers talk about creating programs, they often say, "it compiles fine" or, when asked if the program works, "let's compile it and see". This colloquial usage might later be a source of confusion for new programmers. Compiling isn't quite the same as creating an executable file! Instead, creating an executable is a multistage process divided into two components: compilation and linking. In reality, even if a program "compiles fine" it might not actually work because of errors during the linking phase. The total process of going from source code files to an executable might better be referred to as a build.

Compilation

Compilation refers to the processing of source code files (.c, .cc, or .cpp) and the creation of an 'object' file. This step doesn't create anything the user can actually run. Instead, the compiler merely produces the machine language instructions that correspond to the source code file that was compiled. For instance, if you compile (but don't link) three separate files, you will have three object files created as output, each with the name .o or .obj (the extension will depend on your compiler). Each of these files contains a translation of your source code file into a machine language file -- but you can't run them yet! You need to turn them into executables your operating system can use. That's where the linker comes in.

Linking

Linking refers to the creation of a single executable file from multiple object files. In this step, it is common that the linker will complain about undefined functions (commonly, main itself). During compilation, if the compiler could not find the definition for a particular function, it would just assume that the function was defined in another file. If this isn't the case, there's no way the compiler would know -- it doesn't look at the contents of more than one file at a time. The linker, on the other hand, may look at multiple files and try to find references for the functions that weren't mentioned.



You might ask why there are separate compilation and linking steps. First, it's probably easier to implement things that way. The compiler does its thing, and the linker does its thing -- by keeping the functions separate, the complexity of the program is reduced. Another (more obvious) advantage is that this allows the creation of large programs without having to redo the compilation step every time a file is changed. Instead, using so called "conditional compilation", it is necessary to compile only those source files that have changed; for the rest, the object files are sufficient input for the linker. Finally, this makes it simple to implement libraries of pre-compiled code: just create object files and link them just like any other object file. (The fact that each file is compiled separately from information contained in other files, incidentally, is called the "separate compilation model".)



To get the full benefits of condition compilation, it's probably easier to get a program to help you than to try and remember which files you've changed since you last compiled. (You could, of course, just recompile every file that has a timestamp greater than the timestamp of the corresponding object file.) If you're working with an integrated development environment (IDE) it may already take care of this for you. If you're using command line tools, there's a nifty utility calledmake that comes with most *nix distributions. Along with conditional compilation, it has several other nice features for programming, such as allowing different compilations of your program -- for instance, if you have a version producing verbose output for debugging.


Knowing the difference between the compilation phase and the link phase can make it easier to hunt for bugs. Compiler errors are usually syntactic in nature -- a missing semicolon, an extra parenthesis. Linking errors usually have to do with missing or multiple definitions. If you get an error that a function or variable is defined multiple times from the linker, that's a good indication that the error is that two of your source code files have the same function or variable.



http://www.acm.uiuc.edu/sigmil/RevEng/ch02.html
The compilation Process
All 5 stages are implemented by one program in UNIX, namely cc, or in our case, gcc (or g++). The general order of things goes gcc -> gcc -E -> gcc -S -> as -> ld.




What is Wild pointer and Dangling Pointer?

Last 17 Mar 2011(004)

http://en.wikipedia.org/wiki/Dangling_pointer

{
  char*dp = NULL;
  /* ... */
  {
      char c;
      dp =&c;
  }/* c falls out of scope */
    /* dp is now a dangling pointer */
}




#include 
void func()
{
   char*dp = malloc(A_CONST);
   /* ... */
   free(dp);/* dp now becomes a dangling pointer */
   dp = NULL;/* dp is no longer dangling */
   /* ... */
}



int*func(void)
{
   int num =1234;
   /* ... */
   return&num;
}



int f(int i)
{
   char*dp;/* dp is a wild pointer*/
   staticchar*scp;/* scp is not a wild pointer:
                       * static variables are initialized to 0
                       * at start and retain their values from
                       * the last call afterwards.
                       * Using this feature may be considered bad
                       * style if not commented */
}






Explain the scope resolution operator?

Last 17 Mar 2011(002)

http://en.wikipedia.org/wiki/Scope_resolution_operator

The scope resolution operator (::) in C++ is used to define the already declared member functions (in the header file with the .hpp or the .h extension) of a particular class. In the .cpp file one can define the usual global functions or the member functions of the class. To differentiate between the normal functions and the member functions of the class, one needs to use the scope resolution operator (::) in between the class name and the member function name i.e. ship::foo() where ship is a class and foo() is a member function of the class ship.

The other uses of the resolution operator is to resolve the scope of a variable when the same identifier is used to represent a global variable, a local variable, and members of one or more class(es). If the resolution operator is placed between the class name and the data member belonging to the class then the data name belonging to the particular class is referenced. If the resolution operator is placed in front of the variable name then the global variable is referenced. When no resolution operator is placed then the local variable is referenced.



#include

using namespace std;



int n = 12; // A global variable



int main() {

int n = 13; // A local variable

cout << ::n << endl; // Print the global variable: 12

cout << n   << endl; // Print the local variable: 13




What is structure and class difference?

http://www.parashift.com/c++-faq-lite/classes-and-objects.html

The members and base classes of a struct are public by default, while in class, they default to private. Note: you should make your base classes explicitly public, private, or protected, rather than relying on the defaults.

struct and class are otherwise functionally equivalent.

OK, enough of that squeaky clean techno talk. Emotionally, most developers make a strong distinction between a class and a struct. A struct simply feels like an open pile of bits with very little in the way of encapsulation or functionality. A class feels like a living and responsible member of society with intelligent services, a strong encapsulation barrier, and a well defined interface. Since that's the connotation most people already have, you should probably use the struct keyword if you have a class that has very few methods and has public data (such things do exist in well designed systems!), but otherwise you should probably use the class keyword.



Can a structure contain a pointer to itself ?

Last 17 Mar 2011(005)

http://c-faq.com/struct/selfref.html
Most certainly. A problem can arise if you try to use typedefs;



15)    What's the difference between using a typedef or a #define for a user-defined type?

Last 17 Mar 2011(003)

http://c-faq.com/decl/typedefvsdefine.html

In general, typedefs are preferred, in part because they can correctly encode pointer types. For example, consider these declarations:



           typedef char *String_t;
    #define String_d char *
    String_t s1, s2;
    String_d s3, s4;



s1, s2, and s3 are all declared as char *, but s4 is declared as a char, which is probably not the intention. (See also question1.5.)
#defines do have the advantage that #ifdef works on them (see also question10.15). On the other hand, typedefs have the advantage that they obey scope rules (that is, they can be declared local to a function or block).


Last 17 Mar 2011(002)



Polymorphism is the ability to use an operator or function in different ways. Polymorphism gives different meanings or functions to the operators or functions. Poly, referring to many, signifies the many uses of these operators and functions. A single function usage or an operator functioning in many ways can be called polymorphism. Polymorphism refers to codes, operations or objects that behave differently in different contexts.



Polymorphism is a powerful feature of the object oriented programming language C++. A single operator + behaves differently in different contexts such as integer, float or strings referring the concept of polymorphism. The above concept leads to operator overloading. The concept of overloading is also a branch of polymorphism. When the exiting operator or function operates on new data type it is overloaded. This feature of polymorphism leads to the concept of virtual methods.



Polymorphism refers to the ability to call different functions by using only one type of function call.  Suppose a programmer wants to code vehicles of different shapes such as circles, squares, rectangles, etc. One way to define each of these classes is to have a member function for each that makes vehicles of each shape. Another convenient approach the programmer can take is to define a base class named Shape and then create an instance of that class. The programmer can have array that hold pointers to all different objects of the vehicle followed by a simple loop structure to make the vehicle, as per the shape desired, by inserting pointers into the defined array. This approach leads to different functions executed by the same function call. Polymorphism is used to give different meanings to the same concept. This is the basis for Virtual function implementation.



In polymorphism, a single function or an operator functioning in many ways depends upon the usage to function properly. In order for this to occur, the following conditions must apply:



All different classes must be derived from a single base class. In the above example, the shapes of vehicles (circle, triangle, rectangle) are from the single base class called Shape.

The member function must be declared virtual in the base class. In the above example, the member function for making the vehicle should be made as virtual to the base class.

Applications are Easily Extendable:

Once an application is written using the concept of polymorphism, it can easily be extended, providing new objects that conform to the original interface. It is unnecessary to recompile original programs by adding new types. Only re-linking is necessary to exhibit the new changes along with the old application. This is the greatest achievement of C++ object-oriented programming. In programming language, there has always been a need for adding and customizing. By utilizing the concept of polymorphism, time and work effort is reduced in addition to making future maintenance easier.



Helps in reusability of code.

Provides easier maintenance of applications.

Helps in achieving robustness in applications.




Types of Polymorphism:

C++ provides three different types of polymorphism.


Virtual functions

Function name overloading

Operator overloading




In addition to the above three types of polymorphism, there exist other kinds of polymorphism:


run-time

compile-time

ad-hoc polymorphism

parametric polymorphism



Other types of polymorphism defined:



run-time:

The run-time polymorphism is implemented with inheritance and virtual functions.



compile-time:

The compile-time polymorphism is implemented with templates.



ad-hoc polymorphism:

If the range of actual types that can be used is finite and the combinations must be individually specified prior to use, this is called ad-hoc polymorphism.



parametric polymorphism:

If all code is written without mention of any specific type and thus can be used transparently with any number of new types it is called parametric polymorphism.



In general, there are two main categories of Polymorphism namely


Ad Hoc Polymorphism

Pure Polymorphism



Overloading concepts fall under the category of Ad Hoc Polymorphismand Virtual methods. Templates or parametric classes fall under the category of Pure Polymorphism.



What is the semantics of data?

Last 12 Mar 2011(001)

If we have an empty class

class X ;



Her size is 1 byte, because the compiler insert a char. If we now have the next sentences:



class Y : public virtual X ;

class Z : publicvirtual X ;

class A : public Y, public Z ;



The size for both classes Y and Z is 8. This size is partially machine dependent. It is also dependent in part of the compiler implementation being used. The size, in both classes (Y and Z) is the interplay of three factors:

1.- Language support overhead. There is an associated overhead incurred in the language support of virtual base classes. Within the derived class, this overhead is reflected as some form of pointer (4 bytes).



2.- Compiler Optimization of recognized special cases. There is the 1 byte size of the virtual base class X subobject also present within Y and Z.



3.- Alignment constraints. The size of the classes at in this point is 5 bytes. On most of the machines aggregate structures have an alignment constraint so that they can be efficiently loaded from and stored to memory. Classes Y and Z requires 3 bytes of padding.

The result is a final size of 8.

The size of the class A is determined by the following:

* The size of the single shared instance of class X: 1 byte.

* The size of its base classes Y and Z minus the storage allocated for class X : 4 bytes each (8 bytes total).

* The size of class A itself : 0 bytes.

* Class A must align on 4 bytes boundary, thus it requires 3 bytes of padding. This results in a total size of 12 bytes.



Last 17 Mar 2011(002)



The simplest way to reuse a class is to just use an object of that class directly, but you can also place an object of that class inside a new class. We call this “creating a member object.” Your new class can

be made up of any number and type of other objects, in any combination that you need to achieve the functionality desired in your new class. Because you are composing a new class from existing classes, this concept is called composition (or more generally, aggregation).

Composition is often referred to as a “has-a” relationship, as in “a car has an engine.”

Composition comes with a great deal of flexibility. The member objects of your new class are usually private, making them inaccessible to the client programmers who are using the class. This allows you to change those members without disturbing existing client code. You can also change the member objects at runtime, to dynamically change the behavior of your program. Inheritance, which is described next, does not have this flexibility since the compiler must place compile-time restrictions on classes created

with inheritance.


What is Function Overloading?

Last 17 Mar 2011(003)

Function overloading is the practice of declaring the same function with different signatures. The same function name will be used with different number of parameters and parameters of different type. But overloading of functions with different return types are not allowed.

For example in this C++ Tutorial let us assume an AddAndDisplay function with different types of parameters.



//C++ Tutorial - Sample code for function overloading

    void AddAndDisplay(int x, int y)

       cout<<" C++ Tutorial - Integer result: "<<(x+y);



    void AddAndDisplay(double x, double y)

       cout<< " C++ Tutorial - Double result: "<<(x+y);



    void AddAndDisplay(float x, float y)

       cout<< " C++ Tutorial - float result: "<<(x+y);



Some times when these overloaded functions are called, they might cause ambiguity errors. This is because the compiler may not be able to decide what signature function should be called.



If the data is type cast properly, then these errors will be resolved easily. Typically, function overloading is used wherever a different type of data is to be dealt with. For example this can be used for a function which converts farenheit to celsius and vice versa. One of the functions can deal with the integer data, other can deal float for precision etc.,



Last 17 Mar 2011(003)

http://www.codersource.net/C/CTutorials/CTutorialthispointer.aspx

The this pointer is used as a pointer to theclass object instance by the member function. The address of the class instance is passed as an implicit parameter to the member functions. The sample below, in this c++ Tutorial shows how to use it. It is a common knowledge that C++ keeps only one copy of each member function and the data members are allocated memory for all of their instances. This kind of various instances of data are maintained use this pointer. Look at the sample below, in this c++ Tutorial.
C++ Tutorial - important notes on this pointer:


this pointer stores the address of the class instance, to enable pointer access of the members to the member functions of the class.

this pointer is not counted for calculating the size of the object.

this pointers are not accessible for static member functions.

this pointers are not modifiable.

  Look at the following example to understand how to use the 'this' pointer explained in this C++ Tutorial.



    class this_pointer_example // class for explaining C++ tutorial

       int data1;

    public:

       //Function using this pointer for C++ Tutorial

       int getdata()

           return this->data1;

     //Function without using this pointer

     void setdata(int newval)

          data1 = newval;



  Thus, a member function can gain the access of data member by either using this pointer or not.



What do know about “Const Data” “Const pointer”?

Last 17 Mar 2011(005)

CONSTANT KEYWORD



char *p       = "Hello"// non-const pointer, non-const data

const char *p  = "Hello";// non-const pointer, const data

char * const p = "Hello";// const pointer non-const data

const char * const p = "Hello";// const pointer, const data



I have this explanation I wrote a long time ago stored away in a file, so to elaborate:



This file explains how const works.



The following declarations are identical:



const char* p;

char const* p;



Both declare a pointer to a constant character. The second is slightly better in the sense that the declaration can be read from right-to-left: "p is a pointer to a const char". Read as such, it is easy to see that the line *p = 'c'; will not compile.



The following declaration:






declares p to be a constant pointer to a character. That is:



p = "foo"; // Does not compile

*p = 'f'; // Compiles!



And thus:



const char* const p;

char const* const p;



both declare p to be a constant pointer to a constant character, and so none of the following lines of code compile:



p = "foo";// Does not compile

*p = 'f';// Does not compile



Now throw another pointer into the mix:



const char** p;

char const** p;



These are equivalent and declare p to be a pointer to a pointer to a

constant character. That is:



p = ptr-to-ptr-to-char; // Compiles

*p = ptr-to-char; // Compiles

**p = 'f'; // Does not compile



Or how about creative placement of const:





This declares p to be a pointer to a constant pointer to a character.

That is:



p = ptr-to-constptr-to-char; // Compiles

*p = ptr-to-char; // Does not compile

*p = constptr-to-char; // Does not compile

**p = 'f'; // Compiles




And the ever-popular:






Which declares p to be a constant pointer to a pointer to a character.

Or:



p = ptr-to-ptr-to-char; // Does not compile

p = constptr-to-ptr-to-char; // Does not compile

*p = ptr-to-char; // Compiles

**p = 'f'; // Compiles




And now we get just plain const happy:





p is a pointer to a constant pointer to a constant character. The only

thing you can do with this one (besides remove the code and rewrite) is:

p = ptr-to-constptr-to-constchar;





p is a constant pointer to a pointer to a constant character. The only thing you can do with this is:

*p = ptr-to-constchar;



And this beast:



const char* const* const p;



Well, it won't pass code review since nobody will understand it, but at any rate... We've achieved maximum constant-ness with this line. You can't do anything at all with p, what it points to, what that points to, or what "what that" points to. You can print it. That's about it.




Last 17 Mar 2011(005)



Abstract classes (C++ only)

An abstract class is a class that is designed to be specifically used as a base class. An abstract class contains at least one pure virtual function. You declare a pure virtual function by using a pure specifier    (= 0) in the declaration of a virtual member function in the class declaration.



class AB {

public:

virtual void f() = 0;



Function AB::f is a pure virtual function. A function declaration cannot have both a pure specifier and a definition.



You cannot use an abstract class as a parameter type, a function return type, or the type of an explicit conversion, nor can you declare an object of an abstract class. You can, however, declare pointers and references to an abstract class.



Virtual member functions are inherited. A class derived from an abstract base class will also be abstract unless you override each pure virtual function in the derived class.

For example:

class AB {

public:

virtual void f() = 0;



class D2 : public AB {

void g();



int main() {

D2 d;



The compiler will not allow the declaration of object d because D2 is an abstract class; it inherited the pure virtual function f()from AB. The compiler will allow the declaration of object d if you define function D2::g().



Note that you can derive an abstract class from a non-abstract class, and you can override a non-pure virtual function with a pure virtual function.



A base class containing one or more pure virtual member functions is called an abstract class.



The members of a class declared with the keyword class are private by default. A class is inherited privately by default.

The members of a class declared with the keyword struct are public by default. A structure is inherited publicly by default.

The members of a union (declared with the keyword union) are public by default. A union cannot be used as a base class in derivation.



Operators that Cant be overloaded?

http://www.tutorialspoint.com/cplusplus/cpp_overloading.htm

1) :: 2) .* 3) . 4) ?:


What are Storage Classes in C++?

http://www.tutorialspoint.com/cplusplus/cpp_storage_classes.htm

A storage class defines the scope (visibility) and life time of variables and/or functions within a C++ Program. These specifiers precede the type that they modify. There are following storage classes which can be used in a C++ Program


auto

register

static

extern

mutable





#include

using namespace std;

int main()

    cout<< "Odd Number" << endl ;

    for ( int j=0; j50>

 cout<2>

     return 1;


