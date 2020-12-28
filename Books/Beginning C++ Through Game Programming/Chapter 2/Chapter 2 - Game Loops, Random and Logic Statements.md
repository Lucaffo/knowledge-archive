Loops
-----

A loop is a way to repeat code sections in multiple ways, without writing and repeat the same code. You can see loops as while, for or do while.

While → Define a loop that finish only when the condition is false.

```cpp
while(<condition>){<statement>}
```

For → Define a loop that finish only when the condition is false. Also allow the initialization of variables and execution of a final statement before the loop check.

```cpp
for(<initialization>; <condition>; <finalstatement>)
{
	<statement>
}
```

Do while → First enter into the loop, **do** the statement, second check as while.

```cpp
do{
	<statement>
}while(<condition>);
```

### UNDERSTANDING THE GAME LOOP

The _game loop_ is a generalized representation of the flow of events in a game. The core of the game repeats until it's stopped by the player. It's "generalized" because exists a ton of types of game loops.

The loops envolves the entire collection of components or systems of the games. It may exists game loops nested inside others game loops. It's the crude macro and micro game logic.

![game loop](gameloop.png "Gameloop")

### SWITCH STATEMENT

A switch statement is a type of selection control mechanism that use a variable to branch into a case. An optimizer compiler, may compile a switch statement into a branch table or a binary search.

Pros and Cons of a switch statement.

(Pro) Easier to understand by people and compiler, especially generated code.

(Cons) Only works with int and does not work with "Range". ex: from 0 to 20, including alle the numbers between them.

(Cons) IN MANY MANY Design patterns, is not used because is an alarm (Code smell) for bugs or poor implementation of the logic.

### (PSEUDO) RANDOM

Random is first of all, a concept. Is the indetermination, of an attribute or a value. In computer science, the randomness is difficult to achieve. Why?

_*Since a truly random number needs to be completely unpredictable, it can never depend on deterministic input.*_[](https://stackoverflow.com/questions/4156907/why-is-random-not-so-random#:~:text=Since%20a%20truly%20random%20number,know%20the%20input%20and%20algorithm.)

It _"looks random"_. For many purposes, this is enough! In summary, the overall is: Because we want to be able to predict what computers do, they can't generate unpredictable numbers (without special hardware).

That's why we call it pseudo-random, it's a function that takes an input or a seed ( A value ), use it, and return a number based on that value. It's pseudo randomically determined by a number or an algorithm.


[[Chapter 2 - Exercises and Questions]]
[[Triangular Inequity.cpp]]