Containers and Values
=====================

C++ expose his **_STL_**, a collection of **_containers_** and **_algorithms_**.

The STL represents a powerful collection of programming work that's been done well. It provides containers (Generic data containers), Algorithms (That work with every container) and iterators ( The glue that holds all together).

A programmer should use this library in replace of other similar mechanism. Why? Because it's written and perform well. Do not reinvent the wheel, right?

A **container** define how _data_ should be _rappresented_/_disposed_. Each element of a container is represented as **iterator**. An \*\*algorithm \*\*_use this iterators to perform_ its **operations**.

Vector
------

A **_vector_** is an STL container that represents a dynamic array, an array that grow and shrink in size.

Advantages of STL vector from static arrays:

-   Its size can be redefined on execution and use the heap memory. Arrays only on compile time, its size is hardcoded in binary and use the stack memory.
-   Can be used with STL Algorithms. (Need an explanation? i think is much explanatory)
-   Are easy to implements and use in programs.

Disadvantages of STL vector from static arrays:

-   Because their size is dynamic, performance and memory usage can be worst when grows in size. Everytime the vector it's full of values, it grows about 100% of it's current size. In this way, the vector don't call resize everytime you need to put inside a new value. However, if you use already a great vector size, you may hit a memory issue. If you are a perfomance guy, you need to keep track the size of a vector.
-   STL may not be available on some game console system (I disagree, well why the fuck you work with that i say. I write that just for fun ).

From here, the book it's much useless. See here for more stimulating brain food: [](https://it.wikipedia.org/wiki/Standard_Template_Library)[https://it.wikipedia.org/wiki/Standard\_Template\_Library](https://it.wikipedia.org/wiki/Standard_Template_Library)

### Tips:

> Pay attention and don't delete iterators while you using it. You may **_invalidate_** your container. When you delete a container element, place your current iterator as the next iterator or the program may crash.

Planning your program.
======================

Why plan your program? In simple project it's overkill a waste of time. In more complex project it might be a lifesafer.

You can plan your code using diagrams, pseudocode and stepwise refinement (When you do diagrams or pseudocode, redo entirely basing on what you do, add details and explode your logic).

Stepwise refinement, in pseudocode, it's the process that approches the pseudocode to the real code.


[[Chapter 4 - Exercises and Questions]]