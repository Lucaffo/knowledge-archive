Classes and Objects
-------------------

A **_Class_** is a user defined data-type which has data members and member functions. Data members are the data variables and member functions are the functions used to manipulate these variables and together these data members and member functions defines the properties and behavior of the objects in a Class.

An **_Object_** is an instance of a Class. When a class is defined, no memory is allocated but when it is instantiated (i.e. an object is created) memory is allocated.

```cpp
class Person
{ 
    // Access specifier 
    public: 
				
    // Data Members 
    string name; 

		void printName();
  
    // Member Functions() 
    string getName() 
    { 
       return this->name; 
    } 
};
```

There are 2 ways to define a member function:

-   Inside class definition
-   Outside class definition

To define a member function outside the class definition we have to use the scope resolution :: operator along with class name and function name.

```cpp
// Definition of printname using scope resolution operator :: 
void Person::printname() 
{ 
    cout << "Geekname is: " << geekname;  
}
```

Overloading the arithmetic operators using friend functions
-----------------------------------------------------------

Some of the most commonly used operators in C++ are the arithmetic operators -- that is, the plus operator (+), minus operator (-), multiplication operator (\*), and division operator (/). Note that all of the arithmetic operators are binary operators -- meaning they take two operands -- one on each side of the operator. All four of these operators are overloaded in the exact same way.

It turns out that there are three different ways to overload operators: the member function way, the friend function way, and the normal function way. In this lesson, we’ll cover the friend function way (because it’s more intuitive for most binary operators).

```cpp
class Cents
{
  private:
		int m_cents;
 
	public:
		Cents(int cents) { m_cents = cents; }
 
		// add Cents + Cents using a friend function
		friend Cents operator+(const Cents &c1, const Cents &c2);
 
		int getCents() const { return m_cents; }
};
 
// note: this function is not a member function!
Cents operator+(const Cents &c1, const Cents &c2)
{
	// use the Cents constructor and operator+(int, int)
	// we can access m_cents directly because this is a friend function
	return Cents(c1.m_cents + c2.m_cents);
}
 
int main()
{
	Cents cents1{ 6 };
	Cents cents2{ 8 };
	Cents centsSum{ cents1 + cents2 };
	std::cout << "I have " << centsSum.getCents() << " cents.\\n";
 
	return 0;
}
```


[[Chapter 3 - Exercises and Questions]]