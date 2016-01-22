squirrel3
=========

The Squirrel programming language, version 3.0.7. This repository is made available with the author's permission.

## Overview ##

Squirrel is a high level imperative, object-oriented programming language, designed to be a light-weight 
scripting language that fits in the size, memory bandwidth, and real-time requirements of applications like 
video games. Although Squirrel offers a wide range of features like:

* open source MIT licence
* dynamic typing
* delegation
* classes & inheritance
* higher order functions
* lexical scoping
* generators
* cooperative threads (coroutines) 
* tail recursion
* exception handling
* automatic memory management (CPU bursts free; mixed approach ref counting/GC)
* both compiler and virtual machine fit together in about 7k lines of C++ code and add only around 100kb-150kb the executable size
* optional 16bits characters strings
* powerful embedding api
 * eg. function/classes can be defined by scripts or in C
 * eg. objects can fully exist in the VM or be bound to native code
 * eg. classes created in C can be extended by scripts or vice-versa
* and more

Squirrel is inspired by languages like Python, Javascript, and especially Lua (the API is very similar and the 
table code is based on the Lua one)
