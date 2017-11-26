---
id: 400
title: mp4 on my Samsung D840
date: 2007-04-04T21:36:54+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/2007/04/mp4-on-my-samsung-d840/
permalink: /2007/04/mp4-on-my-samsung-d840/
tmac_last_id:
  - ""
categories:
  - English
  - Linux
---
With some trial and error, I finally found how to encode videos to play on my Samsung D840.

Here is a shell script that does a good job thanks to the ffmpeg encoder. Hope the codecs and bitrates will be useful to others:

[python]#!/bin/sh
  
\# This shell script encodes a decrypted VOB into a
  
\# mp4 file that is playable on Samsung mobile
  
#
  
#author Regis Decamps
  
#
  
f=$1

VIDEO_BITRATE=112
  
VIDEO\_FRAME\_RATE=12
  
VIDEO_SIZE=cif

AUDIO_FREQ=24000
  
AUDIO_BITRATE=96

ffmpeg -i « $f » \
  
-vcodec mpeg4 \
  
-r $VIDEO\_FRAME\_RATE \
  
-b $VIDEO_BITRATE \
  
-s $VIDEO_SIZE \
  
-acodec aac \
  
-ar $AUDIO_FREQ \
  
-ab $AUDIO_BITRATE \
  
-map 0.0 \
  
-map 0.2 \
  
« $(basename $f .vob).mp4 »
  
[/python]