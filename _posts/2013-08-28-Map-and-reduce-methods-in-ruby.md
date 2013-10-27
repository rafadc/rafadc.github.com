---
layout: post
title: Map and reduce methods in Ruby
cover: map_addict.jpg
cover_attribution: http://www.flickr.com/photos/sarahgb/4518082475
---

There are two methods in Ruby's Enumerable module that often people coming 
from an object oriented background find confusing but are indeed very 
useful: .map and .reduce.

They both are constructions taken from functional programming so they
both take a block as a parameter. 

There are also .collect and .inject aliases for them. They are there
only to use whatever one the domain you are working thinks is best.

__.map / .collect__

Map takes a function and returns the array that has in each position
the result of applying that function to the corresponding element of the
original array.

![Graphical explanation of map](/images/2013-08-28/map.png)

This is a highly practical method. Imagine that, for example, you have
an array of people and you want to get an array of the names. It is
as easy as:

{% highlight ruby %}
people_array.map { |person| person.name }
{% endhighlight %}

__.reduce / .inject__

Reduce is similar to map but instead of receiving a function that takes
only one parameter it receives a function that receives an accumulator and
the value. Instead of returning an array it just returns the accumulator.
We can say that this method reduces the array to a single value.

![Graphical explanation of reduce](/images/2013-08-28/reduce.png)

Imagine now that with our array of people we want to get the total number
of letters that all the names have. We can do:

{% highlight ruby %}
people_array.reduce(0) { |sum, person| sum + person.name.length }
{% endhighlight %}

