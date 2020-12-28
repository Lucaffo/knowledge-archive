## Chapter 1 - Discussion Questions

### Questions:

1.  How does having a widely adopted C++ standard help game programmers?
2.  What are the advantages and disadvantages of employing the using directive?
3.  Why might you define a new name for an existing type?
4.  Why are there two versions of the increment operator? What's the difference between them?
5.  How can you use constants to improve your code?

### Responses:

1.  The standard library can help programmers to not reinvent the wheel everytime for the common programming tasks like dealing with common data structures or interact with common system components. Another reason to use C++ is because is flexible and performance oriented. A game must have in a hand all the resources and optimize the cpu cycles to run faster, and c++ is perfect to achieve this.
    
2.  The advantages to use a _using_ directive is to call functions from library writing less code, and make the code more readable and clean. A disadvanges can be that, if you use more than one namespace, from which library the function is called. In this case it can be better if you don't use the directive. In most of the cases it's your choice, does not change your life too much. Sometimes you can have to deal with coding convention in your company that are restricive to not use namespace. In the other hands, you have to deal with the standard library to many times.
    
3.  C++ support mixed types. You can type unsigned short int everytime or call it ushort with a typedef. It's your choice even this time. But you can save your time to write everytime a long type and calling it with a short name.
    
4.  There are two versions of the increment operator because solves two different task.
    
    ++sum increment the number by one before the entire operation is solved. sum++ increment by one the sum variable after the operation is solved. If used as increment operator (to only increment by one) is useless and there are not difference in use.
    
    ```cpp
    // Sum is equal 0 by default
    int sum = sum++ + 1; // 1 
    int sum = ++sum + 1; // 2
    ```
    
5.  A constants rappresent a not changing variable; after the value is assigned the first time, it becomes read-only. If you use in your code a fixed value frequently, you can make a constant on top of your code, assign that value and use it. This is useful when you have to change that value in every part of the code in a fastest way.

## Chapter 1 - Exercises

### Exercises

1.  Create a list of six legal variable names, 3 using wrong naming conventions.
    
2.  What's displayed by each line in the following code snippet? Explain eash result.
    
    ```cpp
    cout << "Seven divided by three is " << 7 / 3 << endl;
    cout << "Seven divided by three is " << 7.0 / 3 << endl;
    cout << "Seven divided by three is " << 7.0 / 3.0 << endl;
    ```
    
3.  Write a program that gets three game scores from the user and displays the average.
    

### Responses

1.  There are a lot of C++ naming convention out there, so the recommendation is to use something that you might think is minimal, consistent and simple to read.
	
	For example:
    
	```cpp
	// Good variable
	string playerName;
	bool hasPlayerWin;
	bool toRead;

	// Not good variable
	float NumberOfWinningPlayerInThePreviousGame; // too long, wrong type...
	char* PippoButItsActuallyAUsefulVariable; // Too long, what is its purpose?
	int a; // Even a short name is bad, what is its purpose? what means "a"?
	2.  line 1 - 2, line 2 - 2.3333, line 3 - 2.3333, that's because the first result is casted as int (the first digit is the more important). Following this rule, the second one is not truncated because the first digit is a float type of variable. The third one as the second one.
	```

2. line 1 - 2, line 2 - 2.3333, line 3 - 2.3333, that's because the first result is casted as int (the first digit is the more important). Following this rule, the second one is not truncated because the first digit is a float type of variable. The third one as the second one.

	```cpp
	#include<iostream>

	using namespace std;

	/**
		TODO: 1) Does not check the input type
					2) Replace all the average function with an vector/array and 
						 an iterator, to support any number of parameters.
	**/

	int main()
	{
		float n1, n2, n3;

		// Get from the input stream the 3 required numbers
		cout << "Insert the first number: "; cin >> n1; cout << endl;
		cout << "Insert the second number: "; cin >> n2; cout << endl;
		cout << "Insert the third number: "; cin >> n3; cout << endl;	

		// Calculate the average, between n1, n2, n3
		float average = (n1 + n2 + n3) / 3;
		cout << "The average is: " << average << endl;
	}
	```

[Chapter 1 - Exercise 3.cpp](<https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c8947a40-8f49-4ab3-9ea4-82c4f046c7c1/Chapter_1_-_Exercise_3.cpp>)

```cpp
#include<iostream>
#include<vector>
#include<numeric>

using namespace std;

float GetAverage(vector<float> numbers)
{
	if(numbers.size() != 0)
		// Sum all the vector numbers using the iterator, starting from a def value of 0.0f, and calculate the average
		return accumulate(numbers.begin(), numbers.end(), 0.0f) / numbers.size();
	else
		return 0.0f; // It's not correct. Need a way to report an error, variable error or pointer return parameter
}

int main()
{
	vector<float> numbers;
	float inputNumber;

	cout << "Insert a number: ";
	
	// While you enter a number, the program ask you other number
	while(cin >> inputNumber){
		numbers.push_back(inputNumber);
		cout << "Insert a number: ";
	}

	// Programs ends and print the average of the input numbers
	cout << "The average is: " << GetAverage(numbers) << endl;
}
```