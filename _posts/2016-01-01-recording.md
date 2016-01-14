---
layout: post
date:   2016-01-01 00:00:00 +0000
permalink: recording
---

## Recording Streams

The EMS is able to record streams as MP4, FLV or MPEG Transport Stream (TS) files. Any incoming stream type can be recorded. Recording a stream can be done using the following steps:

1. Bring a new stream into the EMS. In this case we are pulling a new RTSP stream:  

        pullStream uri=rtsp://<STREAM_ADDRESS> localStreamName=RTSPTest

    We now have a stream named RTSPTest in the server.  
2. To record it, we issue the record command:  

        record localstreamname=RTSPTest pathtofile=../media/ type=mp4

    This will cause the EMS to record the source RTSP stream into an MP4 file. The file will be placed in the media folder of the EMS installation (as per the "../media" parameter value). The file will be named as `RTSPTest.mp4`.

    In general, the format usually followed is `<localStreamName>.<type>`.

Users may issue the record command before the desired stream is actually available, essentially queuing the recording. In other words, the previous two commands (pullstream, record) can be issued in reverse order and still achieve the same result.

## Stopping Streams

There will likely come a time where stopping a stream is needed. There are two general types of streams: Inbound Streams and Outbound Streams. The convention being used for the direction is always from the perspective of the EMS. So therefore an Inbound Stream can also be considered a source stream.

**Notes:**

- Inbound Streams have both a localStreamName and an ID.
- Outbound Streams have only an ID.
-	Stopping an Inbound Stream will automatically shut down all associated Outbound Streams.  

### Stopping a Stream

There are two functions provided for stopping streams: **shutdownStream** and **removeConfig**

**shutdownStream** is intended for doing just what it says, shutting down a stream. By setting the permanently parameter to true, shutdownStream will also remove the configuration entry (if one exists) in the pullPushConfig.xml file.

    shutdownStream localstreamname=RTSPTest

or  

    shutdownStream id=333 permanently=0

**removeConfig** is intended to remove the entry in pullPushConfig.xml, but it will also stop the associated stream.

    removeConfig id=22

**Note:**  The stream ID is not the same as the config ID. The `listStreams` command shows stream IDs. The `listConfig` command shows config IDs.


### Stopping a Recording

A recorded stream is just like any other stream in the EMS, it is simply directed to a file instead of towards the network. Users may therefore use either of the normal shutdown stream commands to stop a recording. This will cause the recording of this stream to stop, which will close the file that is being written to. All data that had previously been recorded will remain stored in that file. If the stream had not yet been recorded (because a stream with that name was not yet available) then the recording will be canceled.

