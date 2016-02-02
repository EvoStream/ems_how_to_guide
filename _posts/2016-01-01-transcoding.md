---
layout: post
title: Transcoding
date:   2016-01-01 00:00:00 +0000
permalink: transcoding
---

Transcoding with the EMS allows changing the resolution of a source stream, change the bitrate of a stream, change a VP8 or MPEG2 stream into H.264 and much more. It will also allow users to create overlays on the final stream as well as crop streams.

**Note:**

Transcoding requires **SIGNIFICANT** computing resources and will severely impact performance. A general conservative guideline is that to accomplish one transcoding job per CPU core for HD streams.



A. To transcode an RTMP source into different video bitrates and send back to EMS:

``` 
transcode source=rtmp://<RTMP server>/live/streamname groupName=group videoBitrates=100k,200k,300k destinations=stream100,stream200,stream300
```



B. To transcode an existing EMS stream into a different audio channel count and send to an RTMP server:

``` 
transcode source=stream1 groupName=group audioBitrates=copy audioChannelsCounts=1 destinations=rtmp://<RTMP server 2> targetStreamNames=streamMono
```



C. To use files as input and/or output:

``` 
transcode source=file://C:\videos\test.mp4 groupName=group videoBitrates=100k audioBitrates=copy destinations=file://C:\videos\out.mp4
```



D. To stop a running transcoding process(es):

``` 
removeConfig groupName=group
```



E. To force TCP for inbound RTSP:

``` 
transcode source=rtsp://<RTSP server>/live/streamname groupName=group videoBitrates=copy videoSizes=360x200 $EMS_RTSP_TRANSPORT=tcp
```