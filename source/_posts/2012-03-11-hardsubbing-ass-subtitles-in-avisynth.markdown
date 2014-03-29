---
layout: post
title: "Hardsubbing ASS subtitles in AviSynth"
date: 2012-03-11 00:27:00 -0500
comments: true
categories: [ass, avisynth, hardsubbing, video]
---
I find that this job can be nicely done by [assrender](http://srsfckn.biz/assrender/), which is based on libass. It even renders karaoke well. Its usage will be like:

	LoadCPlugin("assrender.dll")
	assrender("subtitles.ass", hinting=3, fontdir="font")

The fontdir option is a directory holding fonts used to render the subtitles, which you don't want to install on your system.
