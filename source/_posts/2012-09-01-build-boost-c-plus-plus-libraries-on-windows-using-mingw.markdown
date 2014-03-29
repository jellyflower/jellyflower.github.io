---
layout: post
title: "Build Boost C++ libraries on Windows using MinGW"
date: 2012-09-01 17:36:00 -0400
comments: true
categories: [boost, c++, mingw]
---
First, download the source code [here](http://www.boost.org/users/download/). Also download [zlib](http://zlib.net/) and [bzip2](http://www.bzip.org/). Extract them to separate directories and open a command prompt in the directory of Boost. Run

	bootstrap gcc
	b2 -s ZLIB_SOURCE=ZLIB_SOURCE -s BZIP2_SOURCE=BZIP2_SOURCE variant=debug,release link=shared,static threading=single,multi address-model=32,64 toolset=gcc

That will build all variants. Of course, you can pick and only build what you need.
