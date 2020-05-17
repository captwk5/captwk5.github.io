---
layout: post
title:  Input & Output in Python
date:   2020-05-17
image:  images/03.jpg
tags:   [Development, Python]
---
**STDIN** & **STDOUT**

{% highlight markdown %}

import sys

# STDIN
lines = sys.stdin.readlines()

# STDOUT
hello = "Hello Python!!!"
sys.stdout.write(hello)

{% endhighlight %}

**input** & **print**

{% highlight markdown %}

i = input('Input someting :')
# typing something
print(i)

{% endhighlight %}
