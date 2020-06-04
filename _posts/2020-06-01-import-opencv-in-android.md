---
layout: post
title:  Import OpenCV Extra SDK
date:   2020-06-01
image:  images/08.jpg
tags:   [Development_Android]
---

안드로이드에서 OpenCV를 사용할 때 extra버젼을 사용하고 싶을 때가 있다.

아래와 같은 순서로 진행하면 된다(MacOS 기준)

참고 : [Android 용으로 OpenCV 4.1.1 빌드하는 방법 (Build OpenCV 4.1.1 for android )](https://webnautes.tistory.com/1268) 

1. bit.ly/2GzYimK -> SDK Tools 25.2.5 Download(기존 sdk tools 와 잠시 변경)
2. OpenCV 4.1.1 source code download
3. OpenCV_contrib 4.1.1 source code download
4. ninja install (brew)
5. openjdk adopt download
6. ant install (brew)
7. OpenCV build with below 
cmake -GNinja -DCMAKE_INSTALL_PREFIX=/Users/wkh/OpenCV-android-sdk -DANDROID_PROJECTS_BUILD_TYPE="ANT" -DBUILD_ANDROID_PROJECTS=ON -DBUILD_EXAMPLES=OFF  -DBUILD_TESTS=OFF -DBUILD_PERF_TESTS=OFF -DBUILD_JAVA=ON -DBUILD_opencv_java=ON -DBUILD_SHARED_LIBS=OFF -DBUILD_FAT_JAVA_LIB=ON -DBUILD_PYTHON=OFF -DINSTALL_ANDROID_EXAMPLES=OFF -DANDROID_EXAMPLES_WITH_LIBS=OFF -DBUILD_DOCS=OFF -DWITH_OPENCL=ON -DANDROID_NDK_HOST_X64=ON -DCMAKE_TOOLCHAIN_FILE=/Users/wkh/Library/Android/sdk/ndk-bundle/build/cmake/android.toolchain.cmake -DANDROID_NDK=/Users/wkh/Library/Android/sdk/ndk-bundle -DANDROID_SDK=/Users/wkh/Library/Android/sdk -DANDROID_TOOLCHAIN=clang -DANDROID_STL=c++_static -DANDROID_ARM_NEON=ON -DANDROID_ABI=arm64-v8a -DANDROID_NDK_HOST_X64=ON -D OPENCV_EXTRA_MODULES_PATH=/Users/wkh/opencv-source/opencv_contrib-4.1.1/modules -DOPENCV_ENABLE_NONFREE=ON -DANDROID_NATIVE_API_LEVEL=16 -DANDROID_SDK_TARGET=29 ..
8. ninja -j4
9. ninja install
10. sdk tool 복귀
11. OpenCV-android-sdk/sdk 에 libcxx_helper 생성
12. CMakeLists.txt 생성 후 아래  
cmake_minimum_required(VERSION 3.6)
add_library(opencv_jni_shared STATIC dummy.cpp)
13. dummy.cpp 에 //empty 입력
14. Manifest 서 uses-sdk 삭제
15. Android import with below
android {
    defaultConfig {
        ndk {
            abiFilters 'arm64-v8a'
        }
    }
}