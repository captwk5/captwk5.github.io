---
layout: post
title:  Basic of Docker
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

#### 이미지 & 컨테이너
도커에는 이미지와 컨테이너라는 개념이 있다. 막상 사용해보면 어렵지 않은데 처음엔 개념이 헷갈렸다.
이미지는 리눅스 배포판 환경을 구성할 수 있는 최소 단위로 ubuntu, centos등 특정 프레임워크 및 라이브러리까지 얹은 환경까지도 포함될 수 있다.

{% highlight markdown %}
~ docker search ${image}
~ docker pull ${image}
~ docker images
{% endhighlight %}

받을 수 있는 이미지를 검색하고 원하는 이미지를 받을 수 있꼬 받은 이미지들은 위 명령어로 볼 수 있다.

![]({{site.baseurl}}/post_images/docker_images.jpg)

그리고 이러한 이미지를 실행시켜 컨테이너로 만들게 되는데 이러한 컨테이너를 다시 이미지화 시켜 새로운 컨테이너로 만들기도 한다.
그러면 컨테이너에 대해 조금 알아보기로 하자.

{% highlight markdown %}
~ docker run -i -t -v /docker_workspace/:/workspace --name test_docker ubuntu:18.04 /bin/bash
{% endhighlight %}

위와 같이 실행하면 우분투 18.04 버전의 test_docker 라는 이름을 가진 컨테이너가 하나 생성 된다.
옵션들을 하나하나 살펴 보면
* -i : 표준 입력을 유지한다.
* -t : pseudo-tty를 할당 한다.(tty는 리눅스 환경에서 일반적인 콘솔의 한 종류)
* -v : 로컬 환경의 디렉토리를 도커위의 디렉토리와 Binding.(${로컬 디렉토리}:${도커 디렉토리})
* -n : 컨테이너의 이름

이렇게 컨테이너를 생성하고 컨테이너를 실행시면 작업할 수 있는 기본적인 환경이 생성 된다.

{% highlight markdown %}
~ docker ps -a
~ docker start [Container Name]
~ docker attach [Container Name]
{% endhighlight %}

![]({{site.baseurl}}/post_images/docker_container.jpg)

실행중인 컨테이너의 목록이 나오고 쉘이 우분투 쉘로 변한 것을 볼 수 있다.

이미지를 실행하여 컨테이너를 만들게 되면 그 안에서 많은 작업들이 이루어질 수 있다. 실제로 소스를 빌드하고 서버가 돌아가기도 한다.
도커 이미지가 커다란 뼈대를 잡고 있으면 컨테이너는 그 이미지 위에서 변경될 수 있는 정보들을 사용하여 개발/운영을 하는 것으로 보면 될 것 같다.

조금 더 적어보면 개발을 하다보면 OS버전, Framework버전에 영향을 받게 된다. 그리고 이러한 변수들은 에러를 발생시키기도 하고 복잡하게 얽혀있는 프로그램에
충돌이 일어나게 하기도 한다. 하지만 이미지를 통해 특정 버전의 OS, Framework등으로 뼈대를 잡아놓고 그위에서 빌드하고 배포하고 또 그렇게 만든 컨테이너를
다시 이미지로 만들어 다시 개발을 하고 운영을 하고 할 수 있는 것이다. 즉 의존성에 대하여 관리가 더 엄격해질 수 있다는 것이다. 그리고 프로젝트에 포함되는 코드, 환경, 라이브러리등이 모두 이미지화가 될 수 있다.