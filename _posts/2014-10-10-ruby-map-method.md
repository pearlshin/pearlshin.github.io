---
title: Ruby's Map Method
layout: post
---
The map method takes an enumerable object and a block. It runs the block of code on each item of the object. Let's say you had a method called array_to_string that takes an array as an argument and you want to make every item in the array a string.

Example:

<pre><code>
def array_to_string(array)<br>
end
</code></pre>

When you use the map method in the example array_to_string method above, you use the map method on the given argument (array).

<pre><code>
def array_to_string(array)
  array.map {|item| block }<br>
end
</code></pre>

Inside the curly braces are pipes with a special variable ("item") in between them and the block within the curly braces. The block is the line of code that runs on each item of the array. In this example, we want to change every item in the array into a string so you would write:

<pre><code>
def array_to_string(array)
  array.map {|item| item.to_s }
end
</code></pre>

One important thing to keep in mind about the map method is that it creates/outputs a new array. If you called the method like so:

<pre><code>
def array_to_string(array)
  array.map {|item| item.to_s }
end
puts array_to_string([1, 2, 3])
</code></pre>

The result would be: ```["1", "2", "3"]```