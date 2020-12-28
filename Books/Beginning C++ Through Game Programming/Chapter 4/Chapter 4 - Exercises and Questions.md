## Chapter 4 - Discussion Questions

### Questions:

1.  Why should a game programmer use the STL?
2.  What are the advantages of a vector over an array?
3.  What types of game objects might you store with a vector?
4.  How do performance characteristics of a container type affect the decision to use it?
5.  Why is program planning important?

### Responses:

1.  A programmer should use the STL for common container and operations.
2.  Advantages over a common array are: Dynamic size and already implemented common method, using vector and algorithm.
3.  Every object you need to store as list of its type. Why this question exists?
4.  It's influenced in a way you insert the element inside or how are disposed. Generally talking it's a requirement of FIFO, LIFO etc...
5.  Program planning is important because if you work in a large and complex project, you may lose something in your way and your code logic could be a massy of spaghetti code.

## Chapter 4 - Exercises
1.  Write a program using vectors and iterators that allows a user to maintain a list of his or her facorite games. The program should allow the user to list all game titles, add a game title and remvoe a game title.

	```cpp
	#include <vector>
	#include <string>

	class Game
	{ 
		public:
			string name;
			bool& operator==(Game& left, Game& right)
			{
				return left.name == right.name;
			}
	}

	class GameList 
	{
		private:
			vector<Game> games;

		public:
			void Add(Game game)
			{
				this.games.push_back(game);
			}

			void Remove(Game game)
			{
				for(auto iter = games.begin(); iter != games.end(); iter++)
				{
					if(*iter == game)
					{
						// An iter that point to the next element
						iter = games.erase(iter);
					}
				}
			}
	};
	```

2.  Assuming that _scores_ is a vector that hold elements of type _int_ what's wrong with the following code snippet?

	```cpp
	vector<int>::iterator iter;

	for(iter = scores.begin(); iter != scores.end(); ++iter)
	{
		iter++;
	}
	```

	At last element, the loop may crash.

3.  Write pseudocode for the Word Jumble game from chapter 3.

	```cpp

	select the word to jumble. Jumble the word in another variable.

	while the player don't respond correctly
		ask the guessing word
		guessing word == word?
			you win
		else
			guess--

		guess <= 0?
			you lose
	```