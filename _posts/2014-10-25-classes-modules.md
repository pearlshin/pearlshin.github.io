---
title: Classes Vs. Modules
layout: post
---

Everything in Ruby is an object. Just as objects have properties and functions in real life, Ruby is an object-oriented program that operates similarly in such a way. Classes allow objects to be initialized and assigned to a global constant. For example, you can create a new array (Array.new) because the class Array exists and runs the methods within it.

In other object-oriented programming languages, objects may inherit from other classes (a class may have traits from multiple classes). In Ruby, however, multiple inheritances are not allowed and can only have one superclass. Ruby only runs with single inheritance. In other words, a class can only belong (inherit from) to one superclass and this is where modules play a role. While classes are about objects, modules are about functions.

As you write bigger Ruby programs, it is common to find yourself reusing chunks of code. Using related methods to apply to your program can overrun each other. Modules provide a namespace (a container for a set of identifiers to give direction to specific identifiers) so that methods and constants can play without worrying about other methods and constants overrunning them.

Another useful element of modules is their ability to provide a mixing. A mixing eliminates the need for multiple inheritance if you include a module within a class definition. This allows the moduleâ€™s instance methods to be available as methods in the class (they get mixed in). Overall, modules provide an easy way to control functionality to classes.