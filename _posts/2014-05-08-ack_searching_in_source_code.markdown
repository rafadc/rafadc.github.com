---
layout: post
title: "Ack, searching in source code"
date: "2014-05-09 16:03:08 +0200"
cover: ack.png
---

Ack is a command line tool specialized in searching into source code. I've giving it
a look this days since I'm switching to emacs and I need to polish some of the tools
I'm using. Since I'm pretty happy with this, I wanted to share a small post to show
how the tool works.

For basic usage you can just type from your shell:

{% highlight bash %}
ack --clojure core
{% endhighlight %}

and it will browse all clojure code starting your current folder looking for the text
_core_. It supports a lot of languages also such as Ruby or Python.

The first thing I'm surprised with is how awesomely fast it is. It is blazingly fast, to
be honest.

There are of course plugins for vim and emacs. I'm using [this plugin](https://github.com/leoliu/ack-el)
for emacs.

If you do clojurescript you'll see that by default only .clj files are traversed while
searching. You can edit your **~/.ackrc** and add the following line to support cljs

{% highlight bash %}
--type-add
clojure:ext:cljs
{% endhighlight %}

You can also exclude programming languages when searching

{% highlight bash %}
ack --noclojure licence
{% endhighlight %}

Another common problem you might face is that often we have folders where we don't want
to search. In my case, leiningen generates some clojurescript files in target folder.
To avoid this we can again use **~/.ackrc**

{% highlight bash %}
--ignore-dir=target/
{% endhighlight %}


Lastly, I dare you to run

{% highlight bash %}
ack --cathy
{% endhighlight %}

Have fun!
