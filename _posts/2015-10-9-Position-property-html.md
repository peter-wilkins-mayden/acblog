---
layout: post
title:  "The Position property in html/css"
author: Peter Wilkins
date:   2015-10-09
permalink: position-property-in-html
comments: true
---

There are four possible values for the position property of an html tag. They pertain to how the element behaves in regards to the document flow.
The default value for all elements is **position:static** where the elements are positioned in the document flow, left to right, top to bottom.

On occasions you may wish to fix an element such as a nav bar to the browser window so that in remains in view at all times however far down the document is scrolled. Setting **position:fixed** takes the element out of the document flow so in the case of the nav bar you would add padding-top to the body element to avoid the next elements from being hidden by the fixed element.

 **Position:absolute** gives an element similar behavior but fixes it to the first non-static parent rather than to the browser window. This may be useful for sidebar headers and so on.

 **Position:relative** moves where an element is displayed but as far as the other elements are concerned it is still in the document flow and a space will appear where the element would have otherwise been. To move such an element use the left, right, top and bottom properties giving values in positive or negative pixels. The **position:relative** property is useful when aligning divs and letters to [create a logo out of CSS](http://codepen.io/peter-wilkins-mayden/pen/JYJYqQ).
