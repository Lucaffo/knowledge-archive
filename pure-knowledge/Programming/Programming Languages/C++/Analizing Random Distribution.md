Verify Random distribution
===
write a general mathematical formula with a randomic output in \[a, b\].

1d6 random distribution
-----------------------

```cpp
#include <cstdlib>
#include <ctime>
#include <iostream>

using namespace std;

// Generate a random number in [a, b]
// f(a,b,r) = a + r % ( b - a + 1 )
// plus one because i need to include b
int RandomBetween(int a, int b) 
{
	// Setup and generate a random number
	return a + rand() % (b - a + 1); 
}

int main()
{
    srand(time(NULL));
    for(int i = 0; i < 1000; i++){
	    cout << RandomBetween(1, 6) << endl;
    }
}
```

Results:

![[Images/1d6.png]]

2d6 random distribution
-----------------------

```cpp
#include <cstdlib>
#include <ctime>
#include <iostream>

using namespace std;

// Generate a random number in [a, b]
// f(a,b,r) = a + r % ( b - a + 1 )
// plus one because i need to include b
int RandomBetween(int a, int b) 
{
	// Setup and generate a random number
	return a + rand() % (b - a + 1); 
}

int main()
{
    srand(time(NULL));
    for(int i = 0; i < 1000; i++){
	    cout << RandomBetween(1, 6) + RandomBetween(1, 6) << endl;
    }
}
```

Results:

![[Images/2d6.png]]