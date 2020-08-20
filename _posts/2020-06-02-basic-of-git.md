---
layout: post
title:  Basic of Git
date:   2020-06-02
image:  images/03.jpg
tags:   [Development_Git]
---

혼자가 아닌 여럿이서 하나의 프로젝트를 진행할 때 관리의 중요성은 더 높아진다.
프로젝트에 대한 형상관리는 퍼포먼스를 내는데에 중요한 요소로 작용될 수 있다.
여럿이 개발을 할 때 대부분 깃을 사용해서 프로젝트를 관리하고 진행하기에 깃의 다양한 기능에 대하여 정리를 해보려 한다.

{% highlight markdown %}
깃(Git)은 컴퓨터 파일의 변경사항을 추적하고 여러 명의 사용자들 간에 해당 파일들의 작업을 조율하기 위한 분산 버전 관리 시스템이다. 소프트웨어 개발에서 소스 코드 관리에 주로 사용되지만 어떠한 집합의 파일의 변경사항을 지속적으로 추적하기 위해 사용될 수 있다. 기하학적 불변 이론을 바탕으로 설계됐고, 분산 버전 관리 시스템으로서 빠른 수행 속도에 중점을 두고 있는 것이 특징이며 데이터 무결성, 분산, 비선형 워크플로를 지원한다.
                                        - 위키피디아 -
{% endhighlight %}

#### Local Repository
{% highlight markdown %}
~ git init
{% endhighlight %}

해당 프로젝트 경로에서 위 명령을 통해 프로젝트를 관리할 수 있는 뼈대를 만든다.(.git 숨김파일 생성)

#### Tracked & Untracked
저장소를 만들고 나면 같은 디렉토리에는 Tracked 와 Untracked 로 나누어진다.
말 그대로 관리 대상과 비대상으로 나누어지는 것이다.

{% highlight markdown %}
~ git add [file]
{% endhighlight %}

위 명령을 통해 file을 Tracked 상태로 만들 수 있다.
Tracked 상태로 들어오면 Unmodified, Modified, Staged 세 가지의 상태가 있다.
* Unmodified : 관리대상이지만 수정이 하나도 안된 파일
* Modified : 관리대상이자 수정된 파일
* Staged : 수정되고 add를 통해 commit할 준비가 된 상태

{% highlight markdown %}
~ git status
{% endhighlight %}

위 명령을 통해 현재 파일들의 상태를 확인할 수 있다.

#### Staged & Unstaged
파일을 add 하고 Staged가 된 상태에서 파일이 변경 되었으면 Modified고 변경이 없으면 Unmodified라고 했다.
하지만 보통은 add를 하기 전에 모든 작업을 하고 add를 하게 된다. 그렇게 Staged상태로 해놓고 난 다음에 commit을 하여
Unstaged로 바꾸게 되는 것이다. add를 하지 않은 파일은 Staged상태로 바꾸지도 않고 commit이 되지도 않는다. 자동적으로 추적되고 반영된다.

#### Logging
변경 되거나 수정된 내용을 저장소에 기록하는 작업을 커밋이라고 한다.
그리고 커밋은 시간순으로 저장 되고 사전에 add를 한 파일에 한해서만 커밋된다. 여러번 커밋 할 수 있기에 각 커밋에 대한 comment를 적을 수 있다.

{% highlight markdown %}
~ git commit -m "Comment"
~ git log
{% endhighlight %}

이렇게 커밋하고 로그를 통해 커밋에 대한 내용을 확인 할 수 있다.

#### Remote Repository
각 로컬에서 작업된 내용을 원격 저장소에 저장을 해야한다. 그래야 멀리 떨어진 사람과도 작업을 같이 할 수 있고 프로젝트를 저장하고 관리 할 수 있다.
깃허브 또는 깃랩등을 통해 저장소를 만들고 clone 혹은 pull을 하게 되면 기본적으로 origin 이라는 원격 저장소가 자동 등록 된다.

{% highlight markdown %}
~ git remote -v
~ git push origin master
{% endhighlight %}

위 명령어를 통해 원격 저장소의 주소와 이름을 보고 작업후 커밋을 통해 기록된 내용들이 원격 저장소에 저장되고 적용되게 된다.

일단 깃에 대한 기본적인 것들을 알아봤다. 이외에도 브랜치를 생성하고 병렬로 작업하여 Merge를 하고 수정, 롤백등 깃으로 유용하고 많은 기능들을 사용할 수 있다.