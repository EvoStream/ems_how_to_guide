## Adaptive Bitrate Streaming

Adaptive bitrate streaming requires files to be generated from a live stream. Because of this, HLS, HDS, MSS, DASH streams must be started within the EMS before they can be accessed.

These files must be written into the `../evo-webroot` folder which for the native webserver of EMS (also called EWS).

**Note:**

User may still opt to use other web root such as Apache or Internet Information Services (IIS).

