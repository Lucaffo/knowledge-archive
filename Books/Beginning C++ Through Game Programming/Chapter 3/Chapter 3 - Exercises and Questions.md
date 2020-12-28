## Chapter 3 - Discussion Questions

### Questions:

1.  What are some of the things from your favorite game that you could represent as objects? hat might their data members and member function be?
    
2.  What are advantages of using an array over a group of individual variables?
    
3.  What are some limitations imposed by a fixed array size?
    
4.  What are the advantages and disadvantages of operator overloading?
    
5.  What kinds of games could you create using string objects, arrays, and loops as your main tools?
    

### Responses:

1.  One of my favourite game is Destiny 2. I really like the weapon system, and how are composed. One of the data might be "light level", "base damage", "Weapon type", "Rateo". Sure all this data are private as they need to be temporanely modified.
    
2.  Array is a data structure that can be used to arrange a list of elements of the same type. Is very useful when you need to group of variable that represents the same thing, or a logic list of things. Using a group of variables make more difficult implementing algoritms based on list because every name of variable should be different.
    
3.  If you need to resize the array dinamically or extend it, it's impossible with static array.
    
4.  There ara multiple advantages on doing this:
    

-   You don't have to think a name for a function that do the same things but with different parameters.
-   You make more general the calling to the function, you don't have to think about parameters type, if you overload the function multiple times.
-   It's cool.

5.  Basically any game. But if the questions mean "Only this tools", basic textual game.

## Exercises

### Questions

1.  Improve the Word Jumple game by adding a scoring system. Make the point value for a word based on its length. Deduct points if the player asks for a hint.
2.  What's wrong with the following code?

	```cpp
	for(int i = 0; i <= phrase.size(); i++)
	{
	  cout << "Character at position " << i << " is: " << phrase[i] << endl;
	}
	```

3.  What's wrong with the following code?

	```cpp
	const int ROWS = 2;
	const int COLUMNS = 3;
	char board[COLUMNS][ROWS] = {{'O', 'X', 'O'},
															 {' ', 'X', 'X'}};
	```

### Chapter 3 - Responses

1.  Ok, i'll do with the exercise assigned by the professor.
2.  Nothing.
3.  You can't assign matrix values in this way. Either you could, there is missing the last row.