---
layout: post
title: "Om, clojure based reactive interfaces"
date: "2014-05-18 12:31:08 +0200"
cover: om.png
---

These days I'm enjoying writing some web toys in clojure using [Om](https://github.com/swannodette/om). It is a web reactive clojurescript framework and guys. I'm so excited about it that I need to write a small tutorial for it in my blog :P

We will write a dumb REPL. Something really complex that is very easy to write in Clojurescript.

## CREATING A PROJECT

## One single state

The state in your web application is described by an atom. 

{% highlight clojure %}
(def app-state
  (atom {}))
{% endhighlight %}

The side effect of this is that it is very easy to think of our application in terms of a series of transformations happening to our global state. We will see later how this is turned into DOM changes in an effective way.

## Meet the root

Your entry point in the application (you can have more than one, but for simplicity we will only have one root in this tutorial) is the root. A root is created using

{% highlight clojure %}
(om/root
  evaluator
  app-state
  {:target (. js/document (getElementById "content"))})
{% endhighlight %}

As you can see here we need to look for an element in our HTML and put our root inside it. You'll be thinking: "what is that evaluator there?" It's a component. Om, builds interfaces based in components that are rendered based in application state. How do we define one?. Let's go to the next step

## Our shiny new component

Om provides us with some functions to build components. There is one of the that is the swiss army of component building and there are a lot of shortcuts to write more concise code. We will use the complex one everywhere and then we will introduce the simpler ones. I found easier to learn Om that way.

{% highlight clojure %}
(defn- evaluator [app owner]
  (reify
    om/IRender
    (render [this]
      (dom/div nil
               (dom/h3 nil "Evaluator"))))
{% endhighlight %}

Now you should be able to compile and run this. If everything is OK you will find a H3 in you HTML that says "Evaluator". Of course this is far from impressive so let's start adding behaviour.

