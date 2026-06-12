---
title: "Display problem with Fallout 1"
date: 2012-02-24
forum: Wine
---

### Post by slackthumbz on 2012-02-24
> Hi, I'm running Fallout 1 with wine version 1.4-rc4 (although this problem occurred with wine 1.2.x on the same machine) on Xubuntu 11.10 and when in fullscreen mode only the bottom 2/3s of the image is shown, the screen seems to reset the display to Fallouts 640x480 without any hitches and the initial loading screen displays fine but once it gets into the opening video and the game menu screen the top 1/3 of the screen is just black. Executing it from the terminal gives me the following:
```
tiberious@clockwork:~$ fallout.sh 
fixme:iphlpapi:NotifyAddrChange (Handle 0xe9e8c8, overlapped 0xe9e8ac): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x32f07c,0x00000000), stub!

```

The fallout.sh script just contains this:
```
#!/bin/sh
cd ${HOME}/.wine/drive_c/Program\ Files/GOG.com/Fallout
wine falloutw.exe -no3d -doublebuffer

```

I've tried setting my windows version to 95 and 98 and the result is the same. Notably this issue doesn't occur when setting wine to emulate a virtual desktop.

Any help much appreciated.

OK, I seem to have fixed this by going into winecfg and changing my custom settings for falloutw.exe
> Set windows version to 95
> Go the graphics tab and make sure all the boxes at the top section are unchecked.
> Wap bap a loo bop a wap bam boom.

---

