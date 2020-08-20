---
layout: post
title:  Cuda Programming
date:   2020-06-03
image:  images/03.jpg
tags:   [Programming_Cuda]
---

딥러닝을 하면서 GPU를 사용하지 않을 수는 없다. 요새 GPU 컴퓨팅을 그래픽스, 이미지 연산 뿐 아니라 응요 프로그램 계산에서도 사용할 수 있도록하는 GPGPU 기술도 많이 있다.
대표적인게 NVIDIA의 CUDA, KronosGroup의 OpenCL 등이 있다.
이중 가장 보편적인 CUDA를 좀 익혀보려 한다. 물론 NVIDIA의 그래픽카드 위에서만 동작한다.

기본적인 CUDA C 프로그래밍 및 Convolution 연산을 해보았다.

<p class="view"><a href="https://github.com/captwk5/cuda_ex" style="color:blue">CUDA Example</a></p>

#### Host & Device
CUDA에서는 CPU와 GPU를 분리해서 HOST(CPU), DEVICE(GPU)로 부른다.
데이터는 기본적으로 CPU에 있기 때문에 GPU에 요청하여 메모리를 할당하는 것이다.
CPU와 GPU는 하드웨어적 구성 자체가 다르기 때문에 기본적인 개념만 이해하고 돌아가는 원리만 안다면
기본적인 연산을 할 수 있을 것이다.

![]({{site.baseurl}}/post_images/cpugpu.jpg)

그래서 기본적인 덧셈 연산과 컨볼루션연산을 해보려고 한다.

일단 Nvidia 드라이버를 설치하고 난 후 컴파일러를 nvcc로 사용하여 빌드하고 확장자는 .cu 다.

nvcc로 빌드를 하게 되면 cuda api를 컴파일 할 수 있게 되고
{% highlight markdown %}
__host__
{% endhighlight %}
, ___global___ 등의 키워드를 사용할 수 있게 된다.

간단하게 설명하면 __host_ 는 프로그램을 실행하는 장치 즉, cpu상에서 작동하게 하는 키워드이고 __global_, __device_들은 gpu위에서 작동하게 하는 키워드 이다.

__global_ 키워드를를 사용하여 함수를 호출 하려면 되면 <<<>>> 를 사용하여야 한다.

그리고 이렇게 호출 된 함수는 기본적으로 멀티스레딩으로 작동하게 된다.

- 작성중
