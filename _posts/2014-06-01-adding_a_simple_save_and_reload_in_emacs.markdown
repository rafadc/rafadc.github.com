---
layout: post
title: "Adding a simple save and reload in emacs"
date: "2014-06-01 12:52:11 +0200"
cover: chrome_logo.jpg
---

I'm starting to like emacs. It's really simple to extend it with new commands.
One simple use case is to save a file and reload the browser. It is very useful
when editing a web page or some source for a web application. I've done this
for Chrome but it will for sure be easy to adapt this solution for emacs.

First of all install [chrome-cli](https://github.com/prasmussen/chrome-cli).
This allows us to control chrome from the command line. Then, the rest is just
piece of cake. In your .emacs file you can add the following code:

{% highlight lisp %}
(defun save-and-reload () "Save and reload browser" (interactive)
    (save-buffer)
    (shell-command "chrome-cli reload")
  )
{% endhighlight %}

This will add a *save_and_reload* command that you can try with *M-x
save-and-reload*.

I also added a keybinding with the following

{% highlight lisp %}
(define-key global-map "\C-x\C-r" 'save-and-reload)
{% endhighlight %}

So I can save and reload with *C-x C-r*. Awesome.

Happy coding!
