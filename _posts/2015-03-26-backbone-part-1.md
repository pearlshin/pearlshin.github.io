---
title: Backbone Basics - Part 1
layout: post
---

I've had my good and bad days with JavaScript. Working on challenges where you build games proved to be very difficult for me during Phase 2 at DBC. Without a doubt, those challenges exercised some JS muscles. When it came to manipulating the DOM and using ajax calls, I began to appreciate JS for what it can do. I saw that there are many possibilities with JavaScript and to continue learning post DBC with JS, I decided to learn JS frameworks.

The three most popular JS frameworks I know off the top of my head are Angular, Backbone and Ember. Angular is a must-learn priority but I decided that learning Backbone first might be a good first step.

#What is Backbone?
Backbone is a JS library that is based off of the MV"C" application design paradigm. It is well known for its light-weight framework and has only one dependency on Underscore.js, a JS library.

#Some of the benefits of Backbone:

- it is imperative (tells the machine what to do. It focuses on describing how a program operates)
- features are collections and has a more minimalistic approach
- the download size is compressed and minified (6.4K)
	- this is because it depends on one JS library instead of several so it is very lightweight. Makes it good to build fast and responsive application.
- most effective at building web apps if they are small and single page, or part of a page.
- its framework is very hands off so experienced JS developers can get quickly started while less experiences developers might find themselves writing a lot of boilerplate code (repetitive code).
- no JS <a href="http://en.wikipedia.org/wiki/Spaghetti_code">spaghetti code</a>


I began with a tutorial that teaches you how to <a href="http://code.tutsplus.com/tutorials/build-a-contacts-manager-using-backbonejs-part-1--net-24277">build a contacts manager using Backbone.js.</a>

As I mentioned earlier, Backbone follows the MVC structure. However, instead of a controller, it is a collection. Let's go through each one.

#Model

Just like models in Ruby, it is the what retrieves and populates the data. As defined in <a href="http://backbonetutorials.com/what-is-a-model/">Backbone's tutorial</a>:<br>
	"Models are the heart of any JS application, containing the interactive data as well as a large part of hte logic surrounding it: conversions, validations, computed properties, and access control."



{% highlight ruby %}
var Person = Backbone.Model.extend({
	initialize: function() {
		alert("Hello World!"")
	};
})

var pearl = new Person;
{% endhighlight %}

You use 'extend' to create a model, view, or collection. It provides instance properties as well as classProperties. Extend sets up the prototype chain and you can create subclasses with it as well.

Here's an example from <a href="http://backbonejs.org/#Model-extend">Backbone.js</a>:

{% highlight ruby %}
var Note = Backbone.Model.extend({

  initialize: function() { ... },

  author: function() { ... },

  coordinates: function() { ... },

  allowedToEdit: function(account) {
    return true;
  }

});

var PrivateNote = Note.extend({

  allowedToEdit: function(account) {
    return account.owns(this);
  }

});
{% endhighlight %}

#View
The view is the component of a JS application that displays a model or collection. They reflect what your models looks like and are used to listen for events and react to them accordingly. This is where you would typically use Underscore.js's _.template.

{% highlight ruby %}
var Directory = Backbone.View.extend({
	initialize: function() {
		alert("this is the view.");
	}
})

var contacts_directory = new Directory();
{% endhighlight %}

#Collection
Collections are simply a collection of models. I like to think of collections as the name that describes the container that the model is in. For example, you can have situations such as the following:

- Model: Student, Collection: ClassStudents
- Model: Todo item, Collection: Todo list,
- Model: Horse, Collection: Barn

Your collection would typically use only one type of model but models can belong in many different collections.

- Model: Student, Collection: English Class
- Model: Student, Collection: Science Class
- Model: Student, Collection: Math Class

{% highlight ruby %}
var Song = Backbone.Model.extend({
	initialize: function() {
		console.log("When words fail, music speaks.");
	}
});

var Album = Backbone.Collection.extend({
	model: Song
});
{% endhighlight %}


