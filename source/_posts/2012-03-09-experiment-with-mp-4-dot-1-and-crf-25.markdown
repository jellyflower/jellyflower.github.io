---
layout: post
title: "Experiment with MP 4.1 and CRF 25"
date: 2012-03-09 00:46:00 -0500
comments: true
categories: [video, x264]
---
I accidentally encoded the fifth episode of Gekijouban Kara no Kyoukai using x264. I used the following command:

	x264 --profile main --level 4.1 --preset veryslow --tune animation --crf 25 --output output.264 source.avs

And this is the comparison of Frame 16416 of the video:

![Comparison of Frame 16416](/img/16416.png)

Of course the quality is very shitty. The image is fuzzy. The grain is gone. The details cannot be seen clearly. But the bit rate is only 303 kbps for a 720p 8-bit H.264 video stream! That may be useful in preparing video for portable devices. I'll experiment more to get the balance between quality and size.
