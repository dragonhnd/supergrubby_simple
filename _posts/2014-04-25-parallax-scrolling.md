---
layout: article
title: "Parallax Scrolling"
categories: hack
modified: 2014-04-25 12:27:31
tags: [tech]
toc: true
comments: true
---

**Parallax Scrolling** can make your website more active and attractive if you can use it approriately.

##What is **Parallax Scrolling**?

> Parallax scrolling is a special scrolling technique in computer graphics, wherein background images move by the camera slower than foreground images, creating an illusion of depth in a 2D video game and adding to the immersion.

##How to create a parallax scrolling web page
###1. background-attachment: fixed || scroll || local
By this the backgroudn will be fixed when you scroll to read more contents(contents're scroll), creating a parallax effect.

<pre>
	<code>
.article{
  background-attachment: fixed;
  }
	</code>
</pre>

And you can add some cool animation to it which make the effect more vivid.

###2. Create  groups of elements with different scroll speed
This will create a 3d visual effect, like the Super Mario in FC.

<pre>
	<code>
function onScroll(e){
  var scrollTop = document.documentElement.scrollTop || document.body.scrollTop;
  sceneBack.style.top = old_top1+scrollTop*.9+'px';
  sceneCenter.style.top = old_top2+scrollTop*.7+'px';
  sceneFront.style.top = old_top3+scrollTop*.3+'px';
  }
	</code>
</pre>

And you can let some of the group move up and some of them move down to make constrast effect.

###3. Horizontal scrolling effect

Although common parallax scrolling acts vertically, you can make it horizontally by scrolling entire div or dom up or down.

<pre>
	<code>
var delta = Math.max(-1, Math.min(1, (e.wheelDelta || -e.detail)));
green_b.style.left = getOldStyle(green_b,'left') + delta*80 + 'px';
orange_b.style.left = getOldStyle(orange_b,'left') + delta*80 + 'px';
blue_b.style.left = getOldStyle(blue_b,'left') + delta*80 + 'px';
	</code>
</pre>

##When and Where to optimize the perfomance
###1. too many pics
You can combine the pics by group to decrease the amount while if the size of one pic is too big, do consider.
###2. add CSS3 transition to make the scroll more fluent
###3. don't abuse parallax scrolling
Though you can make a web page cooler by using this trick, too much parallax scrolling will will only make the website chaos and slow. The best practice is using no more than 2 div of parallax effect.

##Reference
[50 great parallax scrolling websites](http://www.creativebloq.com/web-design/parallax-scrolling-1131762)

[How to create a parallax scrolling website](https://ihatetomatoes.net/how-to-create-a-parallax-scrolling-website/)

[parallax-scrolling-love-story](http://www.alloyteam.com/2014/02/optimized-articles-of-parallax-scrolling-love-story/)
