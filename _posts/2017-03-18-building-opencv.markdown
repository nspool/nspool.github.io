---
layout: post
title:  "Building OpenCV 3.1.0 on macOS"
date:   2017-03-18 21:32:56 +1100
categories: opencv
---

Clone the OpenCV and OpenCV_Contrib repos and checkout release 3.1.0:

	git clone https://github.com/opencv/opencv.git
	git clone https://github.com/opencv/opencv_contrib.git
	cd opencv && git checkout 3.1.0 && cd ..
	cd opencv_contrib && git checkout 3.1.0 && cd ..

Create a build directory, configure and build the project:

	mkdir opencv_build && cd opencv_build
	cmake -D CMAKE_BUILD_TYPE=Release -D APPLE_FRAMEWORK=ON
 -D CMAKE_INSTALL_PREFIX=/usr/local -D WITH_CUDA=OFF -D OPENCV_EXTRA_MODULES_PATH=../opencv_contrib/modules ../opencv/
	make -j7 # runs 7 jobs in parallel
	cd ..


Copy the contrib modules into the OpenCV project: 

	cp -ri opencv_contrib/modules opencv/modules

To build an iOS framework:

	python opencv/platforms/ios/build_framework.py ios

Similarly, to build the macOS framework:

	python opencv/platforms/osx/build_framework.py osx


