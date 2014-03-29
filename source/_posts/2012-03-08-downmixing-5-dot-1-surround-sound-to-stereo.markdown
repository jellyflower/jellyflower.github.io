---
layout: post
title: "Downmixing 5.1 surround sound to stereo"
date: 2012-03-08 18:53:00 -0500
comments: true
categories: [audio, ffmpeg]
---
By far I think using FFmpeg is still the best way to do it. A command like this will finish the job:

	ffmpeg -i INPUT -vn -ac 2 -acodec CODEC OUTPUT
