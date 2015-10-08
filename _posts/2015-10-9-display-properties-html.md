---
layout: post
title:  "The Display: properties in html/css"
author: Peter Wilkins
date:   2015-10-09
permalink: display-property-in-html
comments: true
---

There are four display properties that apply to html tags.

You set the property in css using the name value pair format for example: ```display: block```

The are four possible values:
* Block
* Inline
* Inline-Block
* none

HTML tags that are *block* by default include div, p, section, nav, image, header, footer. It pertains to elements that are structural. Block elements always take 100% of the width of their parent container whatever their actual width. As they are boxes they have height, width, border, padding and margin properties.

In contrast *display:inline* elements are not boxes and do not have these properties. Inline pertains to elements such as text, links, and elements that apply style such as strong, span, em and so on.

Using visibility:hidden is one way to hide an element but it remains in the document flow by default so an empty space will occur. *display:none* will take the element right out of the document flow. By default the only element with display:none is the input tag of type hidden.

Sometimes you may want to have boxes nest one along side another rather than take up 100% of the container. For these occasions use *inline-block*, the boxes now arrange themselves beside each other if there is enough space horizontally. There are no elements that are inline-block by default. If you use the float property on a block element it will automatically become inline-block the only differences being that margins are maintained with *inline-block* and float removes the element from the document flow. This requires overflow:auto to be set on the parent container if it is to 'see' the floated element and expand to contain it.

It is generally good practice to build html in the direction of document flow and maintain elements default display property. This maintains code clarity and avoids confusion or unpredictable behavior in the browser.
