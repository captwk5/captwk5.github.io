---
layout: post
title:  First Posting
date:   2020-05-14
image:  images/02.jpg
tags:   [Development][Python]
---
STDIN & STDOUT in Python

{% highlight ruby %}

import sys

# stdin
lines = sys.stdin.readlines()

# stdout
hello = "Hello Python!!!"
sys.stdout.write(hello)

{% endhighlight %}
