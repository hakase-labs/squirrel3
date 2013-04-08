The Squirrel Programming Language v3.0.4 (squirrel3)
====================================================

## Overview ##

Squirrel is a high level imperative, object-oriented programming language, designed to be a light-weight scripting language that fits in the size, memory bandwidth, and real-time requirements of applications like video games. Squirrel offers a wide range of features like:

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
* optional 16-bit character strings
* powerful embedding api:
 * function/classes can be defined by scripts or in C
 * objects can fully exist in the VM or be bound to native code
 * classes created in C can be extended by scripts or vice-versa
* and more

Squirrel is inspired by languages like Python, Javascript, and especially Lua (the API is very similar and the table code is based on the Lua one)

## Notes about this repository ##

This repository is made available with the author's permission.

__Please note:__ This repository is not an official mirror of the Squirrel programming language. Although the language remains the same this repository uses a different build system (cmake) than the original source bundle made available by the author. The author's source bundle can be found at the official Squirrel web site: http://squirrel-lang.org/.