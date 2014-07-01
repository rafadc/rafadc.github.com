---
layout: post
title: "Procs, lambdas and blocks"
date: "2014-07-01 15:30:40 +0200"
cover: lambda.svg
---

One of my students at Ironhack asked me about blocks and procs so I'll take the chance to write a post in the blog.

A proc is a block of code that we can store for later use. This is the most basic form they might take.

```ruby
my_proc = Proc.new {puts "Hi!!!"}

my_proc.call
```

This will output Hi!!! in the standard output.

We have a syntactic sugared form for this

```ruby
my_proc = proc {puts "Hi!!!"}

my_proc.call
```

But we also have lambdas that have a similar syntax

```ruby
my_lambda = lambda {puts "Hello lambda!"}

my_lambda.call
```

We can also pass parameters to both of them:

```ruby
my_proc = proc {|param| puts "Hi from Proc with #{param}!!!"}

my_proc.call("my parameter")


my_lambda = lambda {|param| puts "Hello from lambda with #{param}!"}

my_lambda.call("my parameter")
```

This will output

```
Hi from Proc with my parameter!!!
Hello from lambda with my parameter!
```

We have also another syntactic form for lambdas which is used very often

```
my_lambda = -> param { puts "Hello from lambda with #{param}!"}

my_lambda.call("my parameter")
```

Then, what are the differences between a block and a lambda? There are two of them.

If you run the proc without the parameter it will set it to *nil*

``` ruby
my_proc = proc {|param| puts "Hi from Proc with #{param}!!!"}

my_proc.call
```

Outputs:

```
Hi from Proc with !!!
```

If you run the lambda without the parameter:

```ruby
my_lambda = -> param { puts "Hello from lambda with #{param}!"}

my_lambda.call
```

this will throw an exception

```
wrong number of arguments (0 for 1) (ArgumentError)
```

There is also a second difference that can be seen in the following script:

```ruby
def returning_from_proc
  puts "Proc method starting"
  proc {return}.call
  puts "Proc method finished"
end

returning_from_proc()


def returning_from_lambda
  puts "Lambda method starting"
  -> {return}.call
  puts "Lambda method finished"
end

returning_from_lambda()
```

This outputs

```
Proc method starting
Lambda method starting
Lambda method finished
```

This is because the return into the proc affects containing method and the return into the lambda affects only the lambda itself.

There is also a third inhabitant into this chunk-of-code world. It is the block. A Block is also a piece of code but in this case it is not an object and we can only use it encapsulated in a Proc. We can receive a block of code as a parameter in every function.

```ruby
def my_meth
  puts "My method"
  yield
end

my_meth {puts "Inside block"}
```

Since a block of code is not an object we need another special form to invoke it. This is the **yield** you can find there.

Anyway we can encapsulate that block and use it like any other object.

``` ruby
def my_meth(&block)
  puts "It is encapsulated in a #{block.class}"
  block.call
end

my_meth {puts "Inside block"}
```

This will output:

```
It is encapsulated in a Proc
Inside block
```
