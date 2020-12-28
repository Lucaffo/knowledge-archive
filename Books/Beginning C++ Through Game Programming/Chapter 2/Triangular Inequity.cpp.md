```csharp
// *****************************************************************
// Triangle inequity.cpp
//
// Created by Luca Raffo on Tue Oct 17 2020 
//
// Check triangle inequality
//
// ******************************************************************

#include <cstdlib>
#include <ctime>
#include <iostream>

using namespace std;

const int MAX_LENGTH = 100;
const int MIN_LENGTH = 0;

int RandomBetween(int a, int b) 
{
	// Setup and generate a random number
	return a + rand() % (b - a + 1); 
}

int main(){
	srand(time(NULL));

	// Generate the 3 side of the triangle
	int a = RandomBetween(MIN_LENGTH, MAX_LENGTH);
	int b = RandomBetween(MIN_LENGTH, MAX_LENGTH);
	int c = RandomBetween(MIN_LENGTH, MAX_LENGTH);
	
	// Check triangle inequity
	cout << "a("<<a<<") + b("<<b<<") > c("<<c<<") -> " << (a + b > c) << endl;
	cout << "a("<<a<<") + c("<<c<<") > b("<<b<<") -> " << (a + c > b) << endl;
	cout << "b("<<b<<") + c("<<c<<") > a("<<a<<") -> " << (b + c > a) << endl;
	cout << "Triangle inequity verified: " << (a + b > c) && (a + c > b) && (b + c > a)<< endl;

	return 0;
}
```