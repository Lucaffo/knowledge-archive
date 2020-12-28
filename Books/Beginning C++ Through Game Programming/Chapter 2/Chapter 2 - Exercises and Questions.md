## Chapter 2 - Discussion questions

### Questions:

1.  What kinds of things would be difficult to program without loops?
2.  What are the advantages and disadvantages of the switch statement versus a series of if statements?
3.  When might you omit a break statement from the end of a case in a switch statement?
4.  When should you use a while loop over a do loop?
5.  Describe your favorite game in terms of the game loop. Is the game loop a good fit?

### Responses:

1.  Everything that needs to be repeated for any purpose. Math operations, such as limits.
    
    The problem from the base is, if you need to repeat a process N times you don't have to copy paste each time the line for repeat that process, because without it the code would be a unmantainable mass of repeated things.
    
2.  The are different pros and cons to use them. I will list the most important:
    
    -   (PRO) **Compilation is faster**. Firstly, using an optimizing compiler, the switch case will be compiled faster than an if else cascade. Secondly, an if else cascade can be nested: this is not expected by the compiler, so the compilation is slower. Using swtch statements, the compiler knows how long the entire block is, the number of cases and how to enter in each of them. Using this info, the most optimized compilers can compile the switch statement using a binary tree or a table.
    -   (PRO) **The code is more readable.** Using the switch case makes the code more readable as we know that the switch case is not much longer and cannot be nested like an if else block.
    -   (CONS) **Using a switch case in OOP, is mostly a "code smell"**. If you use design patterns, you should deal with switch case rarely, as they could be replaced most of the time.
    -   (CONS) **Don't use a switch case if you have too many cases.** Sometimes you have to deal with too many cases. You might have to deal with the problem in other ways. For example, a thousand cases may be managed with a structure or a map.
    
    3.  You might want to omit it when you have to deal with a sort of "ending process" where you have to do an action only for determinated cases. For example, you might want to omit it when you want to include multiple cases for a process like:
    
    ```cpp
    switch(x){
    	
    	case 20: // Break omitted here
    	case 21:
    		cout << "hello 20 or 21" << endl;
    		break;	
    
    }
    ```
    
    4.  You should use a while loop over a do while loop when you want to check the condition of the loop first. If not, you should use a do while loop.
        
    5.  A Dark Souls like game loop.
        
    
    Kill, Level Up → Die → Respawn.
    
    Level Loop = Kill \[difficult\] enemy → get souls \[by difficulty\] → Level Up → Get stronger. If you kill stronger enemies, you earn more souls. When you level up, the souls required get increased. You can loop the process.
    
    A game is composed of many game loops, and sometimes are very complicated. The example up here is an "Approximation" of what the Darks Souls type of game loop is.
    
    A simpler game loop is the game of chess.
    
    Player1 turn → Resolve turn → Player2 turn → Resolve turn.
	
	 ## Chapter 2 - Exercises
	 
	 1.  Rewrite the Menu Chooser program from this chapter using an enumeration to represent difficulty levels. The variable choice will still be of type of int.
    
    [Chapter 2 - Exercise 1.cpp](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d592104f-547a-4c8c-820a-43ec16a7334f/Chapter_2_-_Exercise_1.cpp)
    
2.  What's wrong with the following loop?
    
    ```cpp
    int x = 0;
    while(x){
    	++x;
    	cout << x << endl;
    }
    ```
    
    It never enters into the loop.
    
3.  Write a new version of the Guess My Number program in which the player and the computer switch roles. That is, the player picks a number and the computer must guess what it is.
    
    [Chapter 2 - Exercise 3.cpp](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6006bb00-c081-4097-a732-0b12a896adad/Chapter_2_-_Exercise_3.cpp)