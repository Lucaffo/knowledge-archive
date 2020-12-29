Introduction
------------

C++ is a low level language used to develops software, from industrial application, phones, to even games. C++ is also the standard language for AAA games. Is a directed descendant of the C language, in fact the C++ language use almost all the subset of C.

### C# and C++

Each of them are the most used programming language used game programming. The main difference among them are in performance and in life saving.

C# is the main language used by the Unity Engine and C++ is the main language used in the Unreal Engine.

### Main differences

C# is more easy to learn comparing to C++. This easiness it's the strong point but also the weak one. C# allows to deploy application almost everywhere without change too much from the code, c++ in the other side doesn't support this and you should import library from the used device or deploy different version of the code to support differents platform. C# run in the .Net framework that use a garbage collector, like java. This one use a lot of resources in background, because handle the memory allocation for you. In C++ dynamic memory is allocated and deallocated by you and no other and this allow you to squeeze more performance from hardware.

### Why C++ for Games

-   Is blazingly FAST. One of the goal of the C++ language is performance. Compiling code in the lowest possible level of the machine language to perform more efficently with the hardware.
-   It's flexible, supporting multi paradigm, style of programming and object oriented programming (OOP).
-   It's well supported, from decades people develops open source library to extends the language functionality and make the other developer life more simple. It's useless and a time lost to reinvent the wheel everytime.

How to make and executable
--------------------------

What is the process and steps that a c++ code follow to be transformed as executable? The code, first of all, is written in some way using a text editor or a code editor are the most common way to do that. When you want to compile the code, you must use the c++ compiler, a software that read your code and translates it into an object file. The object file are all the function (Not linked yet) written in machine code, that allows to the software to perform on that machine. Next step is to use a linker; as we written before, you need to link the object file to the code file, this allow to the software to know the calling logic of the software that you write and compact all of this into an executable file.


C++ Introduction
============

The standard library is a set of standard compontents specified into the ISO of C++.

### Which problems it solve

It allows you to use generic constructs, already implemented, tested and almost bug-free at no cost. This functionality are mantained not from you but from the C++ standard.

In long term scope, you don't have to reinvent the wheel, saving time and money.

The STL is huge: The standars is written in 785 pages, excluding the c standard.
Reading at all is unnecessary. 

His objective is clear:
Make sure that developer can use the most efficent solutions for data storing and algorithms operations. 

The standard is splitted in 3 parts:

-   Containers
-   Algorithms
-   Iterators