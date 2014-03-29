---
layout: post
title: "Fraps video too dark? How to: Decode Fraps video correctly"
date: 2012-08-02 23:59:00 -0400
comments: true
categories: [video, fraps, avisynth]
---
The video stream in the multimedia file recorded by Fraps is encoded in Fraps’ own codec. The color space of the video stream can be either YV12 or RGB24. There is an option in Fraps which lets you choose which color space to use.

Currently, many decoders fail to handle Fraps videos in the YV12 color space correctly, resulting in decoded pictures that appear very dark.

In either case, the video stream can be decoded correctly using AviSynth. For YV12, use:

	FFIndex(INPUT)
	AudioDub(FFVideoSource(INPUT), FFAudioSource(INPUT))
	ColorYUV(levels="PC->TV")
	ColorMatrix(mode="rec.709->rec.601", clamp=0)

For RGB24, use:

	FFIndex(INPUT)
	AudioDub(FFVideoSource(INPUT), FFAudioSource(INPUT))

Don’t use the following script:
	
	AviSource(INPUT)
	
That uses Fraps’ own decoder, which converts YV12 to RGB24. If you later encode the video to YV12, the whole process, YV12 → RGB24 → YV12, causes quality loss. In the above two scripts, there is no unnecessary color space conversion.

It is said that by using the right parameters, both FFmpeg and x264 can decode the video stream correctly. But I haven’t tried yet.
