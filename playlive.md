## Playing/Retrieving Live Streams

Once a stream has been added to EMS, it can be accessed in a variety of ways. Through the streaming protocol translation offered by EMS, it is just a matter of requesting the stream in the format that the target player can accept, and the EMS will take care of the rest.

The **localStreamName** that was provided in the **pullStream** command (or that was pushed to the EMS) is used to identify the stream that will be played or retrieved.

The basic commands in playing streams in EMS are the following:

### RTMP

The format of the RTMP URI is as follows:

    rtmp[t|s]://[username[:password]@]ip[:port]/<appName>/<stream_name>

As an example, to play an RTMP stream, use the following URI in the Flash enabled player:

    rtmp://<EMS_IP_ADDRESS>/live/localStreamName

### RTSP

The format of the RTSP URI is as follows:

    rtsp://[username[:password]@]ip[:port]/[ts|vod|vodts]/<stream_name or MP4 file name>

**Note:**

The command is very similar to RTMP, except for the absence of the "appName" field.

As an example, to play an RTSP stream, the following URI in an RTSP enabled player can be used:

    rtsp://<EMS_IP_ADDRESS>:5544/localStreamName

By default, the EMS will send the video/audio payload data via RTP. If MPEG-TS is needed instead, simply specify it in the request URI:

    rtsp://<EMS_IP_ADDRESS>:5544/ts/localStreamName

