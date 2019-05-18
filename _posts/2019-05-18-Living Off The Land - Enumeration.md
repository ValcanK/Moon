---
layout: post
title: Living Off The Land - Enumeration
date: 2019-05-18
excerpt: "Enumerating a Target or Network with Living Off The Land Techniques."
tags: [windows, cmd, penetration testing, emulation]
comments: true
---

## The Point

* As a Penetration Tester or Red Team Member and even a defender, it’s essential that
you understand how to use the various capabilities of a system that you’ve gained access to.
You may be thinking, I’ll just find a way to get a meterpreter shell on to the target. Well I hate
to burst you’re bubble but often times you won’t have that option. If you’re goal is to remain as
quiet as possible then your best bet it to use what’s already available.
It may be that you have limited access to the windows command line or an instance of
powershell. If you’re lucky it will be powershell, but once again that’s in a perfect world.
Personally, I want to be able to move throughout a system or target environment
without getting caught. Often times you won’t have the option to load your tool set on the
compromised host.


## In this post I'll be covering various techniques that you can use to conduct Enumeration



## Video Walkthrough 
<iframe width="560" height="315" src="//www.youtube.com/embed/SU3kYxJmWuQ" frameborder="0"> </iframe>

Video embeds are responsive and scale with the width of the main content block with the help of [FitVids](http://fitvidsjs.com/).

Not sure if this only effects Kramdown or if it's an issue with Markdown in general. But adding YouTube video embeds causes errors when building your Jekyll site. To fix add a space between the `<iframe>` tags and remove `allowfullscreen`. Example below:

{% highlight html %}
<iframe width="560" height="315" src="//www.youtube.com/embed/SU3kYxJmWuQ" frameborder="0"> </iframe>
{% endhighlight %}
