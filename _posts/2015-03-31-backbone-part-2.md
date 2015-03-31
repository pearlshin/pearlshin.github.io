---
title: "Events in BackBone.js - Part 2"
layout: post
---


I've been learning Backbone.js by building a project that simply lists a contact list and filters by order of type (friend, family, colleague, etc). It's a very simple app that allows me to get a basic understanding of Backbone.js. You can view my code on my repo <a href="https://github.com/pearlshin/contacts_manager">here</a>.

Now that I've already gone over the very groundlevel basics in <a href="">Part 1</a>, the next thing I'll be discussing here in Part 2 is Events.

Backbone.js is known for its views that listen for events, reacting accordingly and connecting it to your existing restful JSON interface.

The event attribute accepts an object of key/value wheres where the key states the type of event and a selector to bind the event handler to.


{% highlight ruby %}

  events: {
    "change #filter select": "setFilter"
  }


{% endhighlight %}

The example above shows how to create a dropdown menu (from my contacts list project) on the menu page to filter contacts by types. 'change' is the event that Backbone is listening to. If the select changes, trigger the setFilter function, which grabs the type of contact that it is.<br>


Another attribute of a Backbone event is click.

{% highlight ruby %}

<script type="text/template" id="search_template">
  <label>Search</label>
  <input type="text" id="search_input" />
  <input type="button" id="search_button" value="Search" />
</script>

<div id="search_container"></div>

<script type="text/javascript">
    SearchView = Backbone.View.extend({
        initialize: function(){
            this.render();
        },
        render: function(){
            var template = _.template( $("#search_template").html(), {} );
            this.$el.html( template );
        },
        events: {
            "click input[type=button]": "doSearch"
        },
        doSearch: function( event ){
            // Button clicked, you can access the element that was clicked with event.currentTarget
            alert( "Search for " + $("#search_input").val() );
        }
    });

    var search_view = new SearchView({ el: $("#search_container") });
</script>

{% endhighlight %}

This example (taken from <a href="http://backbonetutorials.com/what-is-a-view/">this tutorial</a>) has a click listener to the button.

You can also place bindings on collections, like so: <br>

```
object.on(event, callback, [context])
```

You bind a callback to an object that will be invoked once an event is triggered. The event may also be a string of space-delimited list of several events (```book.on("change:title change:author", ...);```).
The third argument, the context value for ```this```, is included to refer back to it's relation to the object.