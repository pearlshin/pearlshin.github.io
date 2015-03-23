---
title: Ruby Classes Vs. JavaScript Constructor Functions
layout: post
---

Ruby classes vs. JavaScript constructor functions Unlike Ruby, JavaScript does not have classes. Instead, they have prototypes. Ruby classes create new objects and define the behavior of the objects that they create. A constructor in JavaScript is a function. Here's an example of how constructors and prototypes work:

<pre><code>
function favMovieCharacter (firstName, lastName) {
  this.firstName = firstName;
  this.lastName = lastName;
};

favMovieCharacter.prototype.fullName = function () {
  return this.firstName + " " + this.lastNight;
};

var hg = new favMovieCharacter('Holly', 'Golightly')
// => {firstName: 'Holly', lastName: 'Golightly'}
</code></pre>

The function constructor in this example created the new object (this) and defined the behavior of it. Here, fullName is a method of movieCharacter's prototype. The methods in the prototype are the behaviors for movieCharacter objects. Here is how the example would look in a Ruby class:

<pre><code>
class favMovieCharacter
  def initialize(first_name, last_name)
    @first_name = first_name
    @last_name = last_name
  end

  def full_name
    "#{first_name} #{last_name}"
  end
end
</code></pre>

full_name is not a method of the favMovieCharacter class - classes have lots of other methods that are specific to the class that are not shared by other ordinary objects.
