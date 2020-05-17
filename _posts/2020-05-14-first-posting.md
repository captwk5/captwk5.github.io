---
layout: post
title:  In & Out in Python
date:   2020-05-17
image:  images/03.jpg
tags:   [Development]
---
**STDIN** & **STDOUT** in Python

{% highlight markdown %}

import sys

# STDIN
lines = sys.stdin.readlines()

# STDOUT
hello = "Hello Python!!!"
sys.stdout.write(hello)

{% endhighlight %}

Usage **input** & **print** method

{% highlight markdown %}

i = input('Input someting :')
# typing something

print(i)

{% endhighlight %}
