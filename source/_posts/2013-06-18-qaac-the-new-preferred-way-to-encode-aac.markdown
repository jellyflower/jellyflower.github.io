---
layout: post
title: "qaac: The new preferred way to encode AAC"
date: 2013-06-18 23:13:00 -0400
comments: true
categories: [audio, aac, qaac]
---
It has long been widely believed that [Nero AAC Codec][neroaacenc] generally produces AAC of the best quality. However, recently several studies indicate that Apple encoder already surpasses Nero AAC Codec in terms of quality.

The actual encoding code is shipped with Apple Application Support as a form of a library. Apple doesn’t provide a more convenient way to invoke the encoder than using iTunes. Fortunately, there is an open source project called [qaac] fulfilling that role.

To produce AAC exactly equivalent to the so-called iTunes Plus quality, use the following command:

	qaac -v256 -q2 INPUT

I’m currently encoding in qaac’s True VBR mode to prepare music for my iPhone. The command is like this:

	qaac -V63 -q2 INPUT

[neroaacenc]: http://www.nero.com/enu/company/about-nero/nero-aac-codec.php
[qaac]: https://sites.google.com/site/qaacpage/
