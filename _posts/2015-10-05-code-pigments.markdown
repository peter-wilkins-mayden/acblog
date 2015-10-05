---
layout: post
title:  "Highlight your code using Pigments in Jekyll"
date:   2015-09-30
author: Peter Wilkins
permalink: highlight-code-with-pigments-jekyll
---

##How to use Pygments in jekyll.

Pygments is a python tool that can apply colors to over 100 different programming syntaxes - really useful if you are writing a blog about learning the basics of all the parts of the stack from HTML to php to javascript and so on.

In the \_config.yml file in your jekyll site folder add the line `highlighter: pygments` .

In your post:

	{% raw %}
	{% highlight php5 %}
	<?php
	$result = add_up_scores($test_scores, $BELBIN_CODES);
	{% endhighlight %}
	{% endraw %}

shows some php code with colors:
{% highlight php5 startinline True %}
$result = add_up_scores($test_scores, $BELBIN_CODES);
{% endhighlight %}

[more information on the various arguments for the different languages is  here](http://pygments.org/docs/lexers/#lexers-for-various-text-formats)

If you check out my [previous post about Belbin 1.0](http://peter-wilkins-mayden.github.io/acblog/in-scrum-we-trust) you will now find only one image. The code snippets are now in \<code> tags and you can now cut and paste this code which you couldn't do when it was an image. Search engines will also read the code so hopefully more people will find my posts and find them useful.
