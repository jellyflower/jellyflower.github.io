---
layout: post
title: "Frame-accurate decoding and frameserving of video inside AVI"
date: 2012-03-11 00:13:00 -0500
comments: true
categories: [avisynth, frameserving, video]
---
Basically, AVI, MKV, MP4 and FLV are handled very well by [FFmpegSource2](http://code.google.com/p/ffmpegsource/). The script can be something like this:

	LoadCPlugin("ffms2.dll")
	FFVideoSource("source.mkv")

Note that I'm using the newer C plugin version.

For M2TS and TS, it seems that by far [DGAVCDec](http://www.videohelp.com/tools/DGAVCDec) is the best choice. Use DGAVCIndex to index the source and you will get a DGA index file. Then write a script like this:

	LoadPlugin("DGAVCDecode.dll")
	AVCSource("source.dga")
