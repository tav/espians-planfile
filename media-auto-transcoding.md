---
id: media-auto-transcoding
tags: TODO
title: Media Auto-Transcoding
---

Due to the fragmented support of media formats by the various browser vendors, we need to transcode media uploads into alternative formats suitable for each browser.

The audio formats we need to support are:

* AAC/MP3
* Vorbis

And the video formats we need to support are:

* H.264
* WebM

Whilst it's only supported on Firefox at the moment, it looks likely that [Opus](http://www.opus-codec.org/) might win out as a universally supported audio codec. We should also start supporting Opus as soon as Zencoder support it as an output format.