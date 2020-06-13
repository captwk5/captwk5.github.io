---
layout: post
title:  Git Basic
date:   2020-06-02
image:  images/03.jpg
tags:   [Development_Git]
---

혼자가 아닌 여럿이서 하나의 프로젝트를 진행할 때 관리의 중요성은 더 높아진다.
여럿이 개발을 할 때 대부분 깃을 사용해서 프로젝트를 관리하고 진행하기에 깃의 다양한 기능에 대하여 정리를 해보려 한다.

{% highlight markdown %}
깃(Git)은 컴퓨터 파일의 변경사항을 추적하고 여러 명의 사용자들 간에 해당 파일들의 작업을 조율하기 위한 분산 버전 관리 시스템이다. 소프트웨어 개발에서 소스 코드 관리에 주로 사용되지만 어떠한 집합의 파일의 변경사항을 지속적으로 추적하기 위해 사용될 수 있다. 기하학적 불변 이론을 바탕으로 설계됐고, 분산 버전 관리 시스템으로서 빠른 수행 속도에 중점을 두고 있는 것이 특징이며 데이터 무결성, 분산, 비선형 워크플로를 지원한다.
- 위키피디아 -
{% endhighlight %}

1. Git 저장소(Repository)
{% highlight markdown %}
~ git init
{% endhighlight %}
해당 프로젝트 경로에서 위 명령을 통해 프로젝트를 관리할 수 있는 뼈대를 만든다.(.git 숨김파일 생성)

2. Tracked & UnTracked
저장소를 만들고 나면 같은 디렉토리에는 Tracked 와 UnTracked 로 나누어진다. 말 그대로 관리 대상과 비대상으로 나누어지는 것이다.
{% highlight markdown %}
~ git add file
{% endhighlight %}
위 명령을 통해 file을 Tracked 상태로 만들 수 있다.
Tracked 상태로 들어오면 UnModified, Modified, Staged 세 가지의 상태가 있는데
- UnModified는 관리대상이지만 수정이 하나도 안된 파일
- Modified는 관리대상이자 수정된 파일
- Staged는 수정되고 add를 통해 commit할 준비가 된 상태
로 정리할 수 있다.

{% highlight markdown %}
~ git status
{% endhighlight %}
그리고 이러한 상태들은 위 명령을 통해 확인할 수 있다.