---
layout: post
title:  Docker Basic
date:   2020-06-03
image:  images/02.jpg
tags:   [Development_Docker]
---

개발에 있어서 다양한 개발환경이 존재한다. OS(Linux, Window, osX...)부터 Programming언어(C/C++, Python, Java...), Framework(Django, Spring...)등등
각자 상황에 맞춰 적절한 환경을 구축하고 사용한다.
하지만 OS가 계속 업데이트가 되고 Framework의 버전이 달라지는등 환경이 계속 변할 수 있다.
특정 환경에 맞춰서 개발을 해놨는데 환경이 바뀌면 제대로 동작하지 않는 경우는 비일비재하다. 그래서 이러한 개발환경에 대한 대응으로 Docker에 대하여 공부를 해보려한다.

{% highlight markdown %}
도커 컨테이너는 일종의 소프트웨어를 소프트웨어의 실행에 필요한 모든 것을 포함하는 완전한 파일 시스템 안에 감싼다. 여기에는 코드, 런타임, 시스템 도구, 시스템 라이브러리 등 서버에 설치되는 무엇이든 아우른다. 이는 실행 중인 환경에 관계 없이 언제나 동일하게 실행될 것을 보증한다.
- 도커 웹 페이지 -
{% endhighlight %}

1. 이미지 & 컨테이너
도커에는 이미지와 컨테이너라는 개념이 있다. 막상 사용해보면 어렵지 않은데 처음엔 개념이 헷갈렸다.
이미지는 시스템과 서비스에 환경을 구성할 수 있는 최소 단위로 ubuntu, centos등 리눅스 환경을 구성할 수 있고 이러한 리눅스 환경에 특정 프레임웍까지 얹은 환경까지도 포함될 수 있다.

{% highlight markdown %}
~ docker search ${image}
{% endhighlight %}

원하는 이미지를 위 명령어로 검색할 수 있고 

{% highlight markdown %}
~ docker pull ${image}
{% endhighlight %}

원하는 이미지를 받을 수 있다.

{% highlight markdown %}
~ docker images
{% endhighlight %}

이렇게 받은 이미지들은 위 명령어로 볼 수 있다.
![]({{site.baseurl}}/post_images/docker_images.jpg)