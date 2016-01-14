### HTTP Dynamic Streaming (HDS)

#### Creating an HDS Stream

From the local streams in EMS, issue the **createHDSStream** command:

    createHDSStream localstreamnames=myStream targetfolder=[../webroot/path] groupname=myHdsGroup

To use multiple localStreamNames using one **createHDSStream** command do the following:

    createHDSStream localstreamnames=myStream1,myStream2,myStream3 targetFolder=[../webroot/path] groupName=myHdsGroup

The created files will automatically save in the targetFolder path.

    ../evo-webroot/
    myHdsGroup/
      myStream/
        bootstrap
        myStream.f4m
        f4vSegxx-Fragxx
      manifest.f4m
      manifest_v1.f4m

#### Playing an HDS Manifest File

The corresponding link to play this stream would then be:

    http://<EWS_IP_ADDRESS>:8888/myHdsGroup/manifest.f4m

This URL breaks down to: http:// My Web Server / HDS Group Name / Subfolder / manifest file name

