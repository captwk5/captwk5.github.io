---
layout: post
title:  Input,Output and Variable
date:   2020-05-17
image:  images/03.jpg
tags:   [Development_Python]
---
**STDIN** & **STDOUT**

{% highlight markdown %}

import sys

# STDIN
lines = sys.stdin.readlines()
# 끝내고 싶으면 ctrl + d

# STDOUT
hello = "Hello Python!!!"
sys.stdout.write(hello)
sys.stderr.write(hello)

{% endhighlight %}

**input** & **print**

{% highlight markdown %}

i = input('Input something :')
Input something : typing something
print(i) # output : typing something

{% endhighlight %}

stdin & stdout 과 input & print 의 차이?


입력 받거나 출력을 할 경우 위와 같은 방식으로 입출력을 할 수 있다.
그리고 이 과정에서 변수(Variable)를 사용하게 된다.

파이썬에서는 따로 변수의 자료형을 선언하지 않는다. 변수는 데이터가 저장된 메모리의 주소를 가리킨다.

{% highlight markdown %}

b = 4
id(b) # output : 4338185440 주소 동일
c = b
id(c) # output : 4338185440 주소 동일

{% endhighlight %}