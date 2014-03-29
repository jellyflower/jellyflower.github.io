---
layout: post
title: "黑客如何给 B 站投稿"
date: 2013-02-12 00:03:00 -0500
comments: true
categories: [bilibili, multimedia]
---
今天一时兴起给哔哩哔哩投稿，研究了一下发现还真有些门道。这里把我的研究成果发出来，起到抛玉引砖的作用。（是的我的方法是最好的，你的方法只能是砖。）

众所周知，哔哩哔哩并没有自己的服务器，其视频全部是盗链其他的视频站。按目前的状况，用新浪视频是最好的选择。

使用新浪视频，一个问题是审核，貌似现在新浪视频是先发后审。所以你的视频要能存活一天才能说是过了审核。但偶尔也有两三天后被和谐的。

至于过审核没什么技巧，视频标题胡乱填，别的信息能不填就不填，一般来说问题不大。

最大的问题是，新浪视频会不分青红皂白把你上传的视频重编码。重编码的结果往往是渣画质和渣音质。所以哔哩哔哩众把新浪视频称为“渣浪”。而我们的目的就是要防止视频被重编码，就是所谓的“战渣浪”。

<!-- more -->

{% pullquote %}
“战渣浪”的要诀很简单，就是一条：{"如果你上传的文件平均比特率不到 1 Mib/s，就不会被“渣浪”重编码。"}注意这里是整个文件的比特率，包括音频流。
{% endpullquote %}

其实你被我骗了，上面这条只是最重要的一条。其他还要注意，容器格式只能是 FLV，其中包含 AVC 编码的视频流和 AAC 编码的音频流。AVC 和 AAC 编码有很多 profiles 啊什么的，我没有具体测试支持哪些。

所以可以先看看要上传的文件，如果比特率和编码格式达到要求，恭喜你，不用重编码了。只用确保容器是 FLV 就可以上传了。换容器可以用 FFmpeg 很简单的办到：

	ffmpeg -i INPUT -vcodec copy -acodec copy OUTPUT

要重编码的话，我们就得规划一下，音频流的比特率 ~ 140 Kib/s 左右足矣，然后视频流就 ~ 800 Kib/s 吧。

编码视频用 x264：

	x264 INPUT -o video.mkv --pass 1 --bitrate 800
	x264 INPUT -o video.mkv --pass 2 --bitrate 800

{% pullquote %}
{"使用 x264 的平均比特率模式和二次通过方法能相当精准的达到既定的比特率目标。"}这里中间视频流存在 MKV 容器里面，不用容器的话，最后一步 mux 成 FLV 会出问题，具体原因没研究。
{% endpullquote %}

音频部分要先抽出原视频的音频：

	ffmpeg -i INPUT -vn -acodec pcm_s32le -ac 2 audio.wav

然后用 Nero AAC Codec 编码：

	neroaacenc -q 0.4 -lc -ignorelength -if audio.wav -of audio.m4a

最后 mux 就行了：

	ffmpeg -i video.mkv -i audio.m4a -vcodec copy -acodec copy OUTPUT

这样就成功了。把得到的 FLV 传到新浪视频，就可以给哔哩哔哩投稿了。
