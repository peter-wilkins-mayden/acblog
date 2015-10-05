---
layout: post
title:  "Belbin 1.0 has lift off"
date:   2015-09-25
author: Peter Wilkins
permalink: in-scrum-we-trust
---

## Oh where oh where has my $true_Love gone?

To my amazement, we have built a functional web application after only 2 days. Following the Scrum principle of Minimum viable product, we have taken 'our' shortest route to a product we can show our client and get feedback on.

![Our Belbin app's home page](http://peter-wilkins-mayden.github.io/acblog/belbinhome.png)

The challenge was to digitize the [Belbin Team Roles Test](http://belbin.com) that we all completed on paper during the interview process for the Academy. It's an interesting problem because the process of adding up the scores is quite convoluted - the answers have been randomly mixed in terms of the team roles to which they relate.

I dived into this problem that evening. Luckily I had previously seen a similar problem solved using a lookup table, plus there had been mention of something called arrays a few dozen times from Charlie and Connor. I also had to made up placeholder names of a few functions in PHP as I don't have broadband at home yet.



Next morning I found the correct function names, sorted the typos and got some code to run, but not with the results I wanted. I was encouraged by the fact that Luke had come up with a similar solution (albeit one more intuitive to write and easier to read). However my solution stubbornly refused to work as it should.

The matrix of Belbin role codes(an array of arrays):
{% highlight php5 %}
<?php
//  lookup table for belbin scores

 $BELBIN_CODES = array(
        array("RI", "TW", "PL", "CO", "CF", "SP", "SH", "IM", "ME"),
        array("IM", "CO", "SP", "RI", "ME", "SH", "TW", "PL", "CF"),
        array("CO", "CF", "SH", "PL", "TW", "RI", "CF", "ME", "IM"),
        array("TW", "SP", "SH", "ME", "IM", "PL", "CF", "RI", "CO"),
        array("ME", "IM", "TW", "SH", "RI", "CO", "CF", "PL", "SP"),
        array("SP", "PL", "TW", "CO", "CF", "ME", "IM", "SH", "RI"),
        array("SH", "ME", "CF", "RI", "IM", "PL", "CO", "SP", "TW"));

{% endhighlight %}



{% highlight php5 %}
<?php
// matrix of test scores
$test_scores = array(
 array(0,0,0,3,5,0,0,2,0),
 array(0,0,0,3,5,0,0,2,0),
 array(0,0,0,3,5,0,0,2,0),
 array(0,0,0,3,5,0,0,2,0),
 array(0,0,0,3,5,0,0,2,0),
 array(0,0,0,3,5,0,0,2,0),
 array(0,0,0,3,5,0,0,2,0));
{% endhighlight %}

Next I call my function and echo the results and what they should be but I don't get the results I expect....
{% highlight php5 %}
<?php
$result = add_up_scores($test_scores);

echo "SH should be  5. SH = " . $result['SH'] . "<br />";
echo "CF should be 10. CF = " . $result['CF'] . "<br />";
echo "IM should be 12. IM = " . $result['IM'] . "<br />";
echo "CO should be  6. CO = " . $result['CO'] . "<br />";
echo "RI should be 13. RI = " . $result['RI'] . "<br />";
echo "TW should be  5. TW = " . $result['TW'] . "<br />";
echo "PL should be  7. PL = " . $result['PL'] . "<br />";
echo "ME should be 10. ME = " . $result['ME'] . "<br />";
echo "SP should be  2. SP = " . $result['SP'] . "<br />";
{% endhighlight %}
Here are the disappointing results:

	SH should be 5. SH = 0
	CF should be 10. CF = 0
	IM should be 12. IM = 0
	CO should be 6. CO = 0
	RI should be 13. RI = 0
	TW should be 5. TW = 0
	PL should be 7. PL = 0
	ME should be 10. ME = 0
	SP should be 2. SP = 0

Why do all the scores = 0, whats going wrong? Answers on a postcard...





It turned out he problem was scope. The scope of a variable is the areas of a program where the variable can be accessed. I had written the main logic of my solution in a function so it could be called whenever needed but in non object orientated PHP, functions can only see what you pass them in their brackets (unless you use global variables, which is bad pratice). I wasn't giving the function the lookup table arrays so it was giving me a blank result when I performed a lookup code.

Calling the function, passing it the scores matrix and the Belbin roles matrix:
{% highlight php5 %}
<?php
$result = add_up_scores($test_scores, $BELBIN_CODES);
{% endhighlight %}

...and we get the correct results, woohoo!

	SH should be 5. SH = 5
	CF should be 10. CF = 10
	IM should be 12. IM = 12
	CO should be 6. CO = 6
	RI should be 13. RI = 13
	TW should be 5. TW = 5
	PL should be 7. PL = 7
	ME should be 10. ME = 10
	SP should be 2. SP = 2


A strongly typed language like Java would have spat it's dummy at this when trying to compile, but PHP was happy to let me hang by my own petard. An important lesson learned, one that will not be forgotten quickly. I learned an incredible amount in the two days, mostly about how much there is to learn and how much fun that is going to be.

I really enjoyed this project, it was impossible not to work on it every spare hour I had and I am brimming with ideas for Belbin 3.0 (2.0 was already canned due to it being fundamentally flawed). However, I should keep in mind that it's not about what I want. I'll have to see what the clients (in this case Mayden) want and plan the next version, if there is one, around that feedback.

Some of my ideas include
* put all the instructions, questions and results are on separate <divs> in one PHP page so no database is required, save to file or email the results.
* write the whole thing in javascript so now there is no need for a server. Export the results as a pdf.
Interesting thought experiments but PHP, Javascript, Mysql and CSS have enabled us to produce something pretty good, very quickly.

Another scrum principle is self managing teams. At times I felt quite insecure that nothing would get done if there wasn't someone 'experienced' managing things. Ok, Luke was keeping us on track so we didn't waste our time completely but I think he gave us enough freedom to say that this application is our own work. It was amazing how everyone in the team dived into what they thought they could do that would be useful and the results speak for themselves.

I think Scrum's greatest challenge is accepting that uncertainty. The process was great to see in action, how the chaos (and it was chaotic at times) would build and then suddenly, magically, dispirit parts would join up and we would have a result. The energy in the group was exceptional, although on the last afternoon I did go bibbledy. In Scrum we trust, Amen.
