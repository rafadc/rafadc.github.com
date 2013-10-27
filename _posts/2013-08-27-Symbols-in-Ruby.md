---
layout: post
title: Differences between symbols and strings in Ruby
cover: symbol.jpg
---

You can think of a symbol as an immutable string. Since it can't
change each time you ask for a symbol using :name syntax the ruby
interpreter will return the same instance of the symbol.

First al all let's prove that.

{% highlight ruby %}
[1] pry(main)> "Yay".object_id
=> 70339464231200
[2] pry(main)> "Yay".object_id
=> 70339451753020
[3] pry(main)> :yay.object_id
=> 1204808
[4] pry(main)> :yay.object_id
=> 1204808
[5] pry(main)> "yay".to_sym.object_id
=> 1204808
[6] pry(main)> :"yay".object_id
=> 1204808
{% endhighlight %}

As you can see each time we write: "Yay", we are getting a different
object. Although they contain the same characters and they are equal
they are different objects

{% highlight ruby %}
[7] pry(main)> "yay" == "yay"
=> true
[8] pry(main)> "yay".object_id == "yay".object_id
=> false
{% endhighlight %}

But in the case of symbols

{% highlight ruby %}
[9] pry(main)> :yay == :yay
=> true
[10] pry(main)> :yay.object_id == :yay.object_id
=> true
{% endhighlight %}

Also, strings can be changed

{% highlight ruby %}
[11] pry(main)> my_string = "yay"
=> "yay"
[12] pry(main)> my_string << "\n"
=> "yay\n"
[13] pry(main)> my_string
=> "yay\n"
{% endhighlight %}

But symbols can't 

{% highlight ruby %}
[15] pry(main)> my_sym << "\n"
NoMethodError: undefined method `<<' for :yay:Symbol
from (pry):15:in `__pry__'
[16] pry(main)> my_sym = my_sym + "\n"
NoMethodError: undefined method `+' for :yay:Symbol
from (pry):16:in `__pry__'
{% endhighlight %}

This causes symbols to be often used as keys to hashes or to
be used as a substitute for enumerated types.

__Bonus points:__

You can freeze a string and cause it to be immutable with freeze method

{% highlight ruby %}
[17] pry(main)> my_string = "yay"
=> "yay"
[18] pry(main)> my_string.freeze
=> "yay"
[19] pry(main)> my_string << "\n"
RuntimeError: can't modify frozen String
from (pry):19:in `__pry__'
{% endhighlight %}

You can also define 'constants'. Ruby compiler will consider any variable
that is declared uppercased as a constant. It will raise a warning in 
case you change it. Anyway it will allow you to do so:

{% highlight ruby %}
[20] pry(main)> MY_CONST = "Yay"
=> "Yay"
[21] pry(main)> MY_CONST = "Yay\n"
(pry):21: warning: already initialized constant MY_CONST
(pry):20: warning: previous definition of MY_CONST was here
=> "Yay\n"
{% endhighlight %}

