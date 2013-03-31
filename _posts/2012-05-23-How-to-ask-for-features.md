---
layout: post
title: How to ask for features
cover: contract.jpg
cover_attribution: http://www.flickr.com/photos/jsyk/2982312360/
---

### Requirements

Communication between stakeholders has always been a sticky issue in any software
development project. It's an art. If you can handle that, you have taken a big step
forward into building a successful product. 

I found that the problem arises early. When the whole team is "gathering requirements".
That's the first fallacy. There are no such thing as requirements. Well... almost. 
The word "requirement" means:

    _That which is required; an imperative or authoritative
            command; an essential condition; something needed or
            necessary; a need.
            [1913 Webster]_


A requirement is something essential. Something non negotiable and I don't like that idea.
I've seen a lot of such "requirements" pour like rair when there is no time or the
money is running out. I found  much better talking about features. Features are something
that adds value to your software. You can add or remove features depending on your 
resources and needs. That is, for sure, a better situation to deal with.

Also when you gather your features it is common to write use cases. Usually I found that
to be too much. Often the feature set you'll add to your application will change a lot
during the development. If you have a custome he will change his mind and if you don't 
you'll find that your users demand a different thing. Doing a big analysis first has
really proven to be unuseful. 

### User stories

For me it has proven of greater value to write simple __user stories__. What is a
__user story__?

    \[...\]a user story is one or more sentences in the everyday or business language 
    of the end user or user of a system that captures what a user does or needs to do as 
    part of his or her job function. \[...\] It captures the 'who', 'what' and 'why' 
    of a requirement in a simple, concise way, often limited in detail by what can be 
    hand-written on a small paper notecard.

Ok, so what do we have here?

* __A user story must use the language of the end user__. As developers we ussually
drive the user into talking about severs, java, data types and such. That is fundamentally
wrong. We must know what problem we are solving. That's why we are limited to the user
language. To avoid losing focus. We have not yet though about _how_ to solve the problem.
We are focusing in _what_ to solve. 
* __A user story must capture why we want to solve the problem__. Often we fix problems
that are not there just to "anticipate" and later we find out that we failed miserably in
our diagnosis. Also we will need to evaluate how important is a user story and knowing why
are we implementing it is a huge help. Also adding the _why_ forces us to write user
stories that provide __bussines value__ instead of just writing software without direction.
* __A user story must be short__. Writing user stories must not be a lot of work. Also
their scope must be limited. If we can't describe a problem in one or two sentences probably
we don't fully understand it yet or we need to decompose it into some smaller pieces.

So, to gather all the features we want in our software we don't want a 1000 pages document
nobody is going to read. We will do just fine with a bunch of small cards with some
text written on it. 

Looks simple? It isn't. In fact writing good user stories is somehow an art, but it has
proven to be one awesome skill to have. 

I often use a pattern to write user stories so I never forget anything. The pattern goes
like:

    As a ...
    I want to ...
    In order to ...

That way I don't forget to add 'who', 'what' and 'why'.

I also like to add a litte thing to the user story. In the same card, although not mandatory
I like to add how i'm going to check that the user story is completed, again using bussiness
language. That forces me to talk in specific terms instead of overgeneralizing making my
stories more useable and manageable. 

### Some examples

Let's see some examples:

    As a border control officer
    I want to be able to check if the passenger's passport number is in the control list
    In order to avoid criminals entering or exiting the country

    To test it we will start a transit with a blacklisted passport. The system must alert the
    officer. Then we will do the same transit with a non blacklisted passport.


If at that moment we don't have blacklist probably it's the moment to implement it. Mybe we 
already have a blacklist but it does not support yet passport numbers.

This makes us grow around software around features that give our software __bussiness value__.
We will make our changes as small as possible while fulfilling the stories to give the
most value in the least time. 

If I had written the story before as follows:

    As a border control officer
    I want to be able to check if the passenger is in the control list
    In order to avoid criminals entering or exiting the country

    To test it we will start a transit with a blacklisted passport. The system must alert the
    officer. Then we will do the same transit with a non blacklisted passport. Then we will
    try will a passenger whose name and nationality are blacklisted. Afterwards we will try
    a passenger with a blacklisted visa....

We see that this story is getting really difficult to test. This often indicates that we should
break the story into smaller stories. The real value in this is that we deal with smaller problems
and we can postpone some of the parts later on the development to have always the most important
feature set.

Also another patter for poorly written story is the following:

    As a shop owner
    I want the report on daily sales to look nicer
    In order to be able to search easily the amount sold every day

    To test it we will open the daily sales report and see if its nice.

Ok. I promise I've seen user stories like the one before. Imagine you are responsible for doing this. I'd think
to myself "What the hell am I supposed to do?" Often we find these "diffuse" histories. Usually the
problem is that we didn't dug deep enough into the problem:

- Why is difficult to search easily the sales report?: Because the totals are slow to find
- Why are they slow to find?: Because each of them is on a different place. 
- What can we do?: Align the numbers to the right of the report and add the sum of them at the end 
of the report.

And then we build again two user stories: one for aligning the numbers to the right and another
one for adding the total to the end of the page.

### Wrapping up

We've just seen a little glimpse of what user stories are. Keeping things simple is one of the
benefits we can get of using this way of features gathering. Also we get a lot of atomic pieces
we can reorder to get our priorities sorted out. In sum, I find easier to work with this kind
of features that with those big old UML use cases documents. 

Happy hacking!

