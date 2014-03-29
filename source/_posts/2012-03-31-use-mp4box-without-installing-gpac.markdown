---
layout: post
title: "Use MP4Box without installing GPAC"
date: 2012-03-31 19:42:00 -0400
comments: true
categories: [mp4box]
---
[MP4Box](http://gpac.wp.mines-telecom.fr/mp4box/) is an essential tool to manipulate ISO base media file formats, such as MP4, 3GP, etc. Currently it is better than FFmpeg. Later on it is packed in GPAC, a multimedia framework of which the other parts don't appear to be that useful.

To use MP4Box without installing the entire GPAC framework, you can extract relevant files from the installer using a extractor such as 7-Zip:

* js32.dll
* libeay32.dll
* libgpac.dll
* MP4Box.exe
* ssleay32.dll

And add the directory to your path. Then you are good to go.
