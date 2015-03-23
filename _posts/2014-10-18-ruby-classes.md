---
title: Ruby Classes
layout: post
---

Ruby is an object oriented programming language that use classes and objects. Classes are like blueprints for creating objects. I'll use a person's information as an example in object-oriented terms. A "name" is an instance of the class of objects known as a "person". The name, age, and birthday are a few charactersistics of the person that define him or her. There are different functions you can do with the information that the parameter takes in. A class is essentially a combination of characteristics and functions of an object(s).
Instance variables are variables that are available for methods within the class. Instance variables are preceded by the "@" sign and are defined in the initialize method. A method is like a recipe that tells you what you need (instance variables that you may need) and what it produces.

<pre><code>
class Person
  def initialize(name, age, birthday)
    @name = name
    @age = age
    @birthday = birthday
  end

  def intro
    puts "Hello! My name is #{@name}, I am #{@age} years old, and my birthday is #{birthday}."
  end
end
pearl = Person.new("pearl", "24", "februrary 18th, 1990")
</code></pre>

Whenever you want to put a new person in the person class, you create a new object of the class by writing the class name followed by ".new" and parenthesis containing the name, age, and birthday.