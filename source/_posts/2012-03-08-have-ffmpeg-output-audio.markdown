---
layout: post
title: "Have FFmpeg output audio"
date: 2012-03-08 19:05:00 -0500
comments: true
categories: [audio, ffmpeg]
---
Of course the most straightforward way is to output PCM wrapped in WAV format. Things will go pretty well with pcm_s16le, pcm_s24le and pcm_s32le, but not with the unsigned, which I don't know why.
