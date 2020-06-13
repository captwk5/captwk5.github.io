---
layout: post
title:  Cuda C Programming
date:   2020-06-03
image:  images/03.jpg
tags:   [Programming_GPU]
---

딥러닝을 하면서 GPU를 사용하지 않을 수는 없다. 요새 GPU 컴퓨팅을 그래픽스, 이미지 연산 뿐 아니라 응요 프로그램 계산에서도 사용할 수 있도록하는 GPGPU 기술도 많이 있다.
대표적인게 NVIDIA의 CUDA, KronosGroup의 OpenCL 등이 있다.
이중 가장 보편적인 CUDA를 좀 익혀보려 한다. 물론 NVIDIA의 그래픽카드 위에서만 동작한다.

기본적인 CUDA C Programming을 적어보려 한다.

1. Host & Device
CUDA에서는 CPU와 GPU를 분리해서 HOST(CPU), DEVICE(GPU)로 부른다.
데이터는 기본적으로 CPU에 있기 때문에 GPU에 요청하여 메모리를 할당하는 것이다.