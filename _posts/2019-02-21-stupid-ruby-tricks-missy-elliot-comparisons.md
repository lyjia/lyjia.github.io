---
title: "Stupid Ruby Tricks: Missy Elliot Comparisons"
bigtitle: Blog
categories: blog
layout: post
department: "Mad Hacks"
tags: ruby programming stupid.ruby.tricks
---

{% include postintros/stupid-ruby-tricks.html %}

<div align="center"><a href="https://xkcd.com/153/" target="_blank"><img src="https://imgs.xkcd.com/comics/cryptography.png"></a></div>

I don't know what else to call this, and I didn't come up with it, but it does reminds me of [the above XKCD comic](https://xkcd.com/153/), hence the name. It's pretty simple -- when comparing equality against some [scalar](https://softwareengineering.stackexchange.com/questions/238033/what-does-it-mean-when-data-is-scalar) value, *flip the comparators:*

{% highlight ruby %}
# Divine
if 42 == the_meaning_of_life
	satisfy_existential_crisis
end
{% endhighlight %}

As opposed to:

{% highlight ruby %}
# SACRILEGE
if the_meaning_of_life == 42
	satisfy_existential_crisis
end
{% endhighlight %}

#### Why would we do this?

The short answer is that it prevents us from getting our comparison `==`s mixed up with our assignment `=`s: when you flip the comparators. For example, in the snippet below:

{% highlight ruby %}
if the_meaning_of_life = 42
	satisfy_existential_crisis
end
{% endhighlight %}

`the_meaning_of_life` will *always* be 42, regardless of whatever it was before you thought you were testing it. You may as well write:

{% highlight ruby %}
the_meaning_of_life = 42
satisfy_existential_crisis
{% endhighlight %}

which, while valid, means something entirely different.

The longer answer is that when a value is mentioned in a comparison *first*, the Ruby interpreter will raise an error because you can't assign to values -- only variables! If the variable is first, and you accidentally type `=` when you meant `==`, then you will *accidentally assign a new value to your variable*, and then who knows what will happen later on in your program!

It's important to note that a Missy Elliot Comparison should only be used for tests of equality ("`==`"); if you do this with other types of comparisons you can create some weird-looking and confusing code. (For example, this would cause you to reverse all your `>` and `<` comparisons...)

This technique is most useful if you or a member of your team frequently confuse assignments and comparisons.

Missy Elliot Comparisons pair well with another Stupid Ruby Trick I will be describing, called [Conditional Assignment](#conditional-assignment)

#### Alternate Approach: Freeze Your Variables

In some circumstances you can also avoid accidental assignment by `.freeze`-ing variables you treat as constants. This will be expanded upon in another Stupid Ruby Trick, tentatively titled [Constants... on Ice!](#constants-on-ice)