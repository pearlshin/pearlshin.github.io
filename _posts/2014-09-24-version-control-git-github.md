---
title: Arrays & Hashes
layout: post
---

Arrays and hashes are both collections of objects, but are retrieved in slightly different ways. Let's first look at the syntax of an array and hash using the same collection of objects. You would write an array like so:

	my_info = ["Pearl", "Shin", "dog", 24, "blue"]

Hash syntax:

	my_info = { "first_name" => "Pearl",
	"last_name" => "Shin",
	"fav_animal" => "dog",
	"age" => 24,
	"fav_color" => "blue" }

As you can see, an array gives an ordered list of objects whereas hashes give key/value pairs. While arrays list values in a single variable, hashes assign a "meaning" to something. The keys for hashes in the example above are everything before the arrow and the values are on the right of the arrow. With arrays, you would have to count to a specific index to retrieve a specific value (i.e. my_info[2] would be "dog"). To get "dog" in the hash example, you would type "my_info["fav_animal"]" and you would get "dog" as the output.

One thing to note about hashes is that keys are unique and values are not. In other words, you can assign the same value to more than one key.

To explain more clearly how arrays and hashes work, I'll use information I gathered from Tubefilter to list their top 5 most viewed YouTube channels this month as an example.

| YouTube Channel|# of Views |
| --------|---------|
| 1. PewDiePie  | 449,209,605   | 
| 2. DisneyCollectorBR | 324,436,307 | 
| 3. KatyPerryVEVO  | 226,125,421 | 
| 4. stampylonghead  | 217,866,559 | 
| 5. EnriqueIglesiasVEVO  | 202,209,327 | 
To store this data in an array, I would have to store it in multidimentional arrays, which would look something like this:


	music = [["PewDiePie", 449,209,605], 
	["DisneyCollectorBR" 324,436,307], 
	["KatyPerryVEVO", 	226,125,421], 
	["stampylonghead", 217,866,559],
	["EnriqueIglesiasVEVO", 202,209,327]]

To retrieve how many views KatyPerryVEVO got with an array, I would have to count the indexes and write:

music[2][1]

The index 2 represents the second object in the array (array indexes start with 0) and the index 1 represents the second object within that array.

To retrieve this data with a hash, all I would have to write is:

	music["KatyPerryVEVO"]

and the output would give me 226,125,421.