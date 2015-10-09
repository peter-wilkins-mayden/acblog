---
layout: post
title:  "How to use Parsedown to convert your markdown to html"
author: Peter Wilkins
date:   2015-10-09
permalink: parsedown-md-to-html
comments: true
---

Pasredown is a PHP module that parses markdown and returns it converted to html.

To use it in your php file include the Parsedown.php file [available on github](https://github.com/erusev/parsedown).

{% highlight php5 startinline True %}

 include 'path/to/Parsedown.php';

 {% endhighlight %}


Then make a new Parsedown object and pass it your content as a string

{% highlight php5 startinline True %}

	$Parsedown = new Parsedown();
	echo($Parsedown->text($my_markdown));

{% endhighlight %}

Parsedown is tested in php 5.3+ and didn't work for me with php 5.2
