Functions
---------

Break your in code in multiple logic repeatable block. Accept values as arguments, return information from your functions, inline and overloading.

```cpp
// Sample function
float average(float n1, float n2)
{
		// not void functions always return something.
		// Each terminal state need a return statement.
		return (n1 + n2) / 2;
}

int main()
{
	// Simple function call
	cout << average(2, 5) << endl;
}
```

### Scopes

A scope is defined by its brakets, everywhere they are. The scope define the variable, class or function access.

```cpp
// A simple c++ scope
{
	int c = 0;
}
// You can't access c
cout << c; // Not allowed

// Function scope
void printC()
{
	int c = 0;
}
// You can't access c
cout << c; // Not allowed

// Class scope
class test{
	int c = 0;
		
	void printC();
};

test t = test();

// You can't access c directly
cout << c; // Not allowed
cout << t.c; // But like this you can
t.printC(); // And like this also
```

Default argument
----------------

If you are a bored, you can use this thing.

```cpp
void printC(int c = 0)
{
	cout << c; 
}
```

Now you may ask, "Where and when i can use this?". Almost never (Don't blame me, i said "Almost" never, this doesn't mean never). Maybe with some api things.

Overloading
-----------

Overload a function is a useful thing you must know and apply.

Overloading allows to assign the same function name at different function but with different parameter.

```cpp
void print(float number)
{
	cout << number << endl;
}

void print(string s)
{
	cout << string << endl;
}
```

I know it's a bad example.

Global Variables
----------------

Same as default arguments. Avoid using them. You can lose your code logic somewhere you don't remember.

```cpp
int c = 0;

int main()
{
	cout << c;
	modifyAVariableButYouCannotSee();
	modifyAVariableButYouCannotSee2();
	cout << c; // Who modify this variable
}

void modifyAVariableButYouCannotSee()
{
	// what a joke, lets find if someone notice that.
	// If you read this, you're a dumb. You spend your time to see
	// which function modify c
	c = 1;
}

void modifyAVariableButYouCannotSee2()
{
	// Do nothing wrong.
	// If you read this, you're a dumb. You spend your time to see
	// which function modify c
}
```

Now you know why.

Constants
---------

Use them when you want. Generally a constant is like a variable but it may only assigned at runtime, only one time and cannot be modified after.

The naming convention is quite simple. CAPS\_AND\_IF\_U\_NEED\_SPACE\_USE\_THIS\_UNDERSCORE\_LINE.

```cpp
// A simple value const
const string GAME_NAME = "Best brot.. game ever!";

// A const may be assigned at runtime.
const float GAME_VERSION = GetVersionFromServer();

// A simple api token
const string MAPS_API_TOKEN = "<api-token>";
```