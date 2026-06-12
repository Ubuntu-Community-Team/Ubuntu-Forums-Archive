---
title: "No sound in CNC3 with Wine"
date: 2007-08-20
forum: Wine
---

### Post by RudolfMDLT on 2007-08-20
Hi there,

I have installed CnC3 Tiberium Wars in Ubuntu with wine and I'm smiling bigtime! I just need sound though. I followed this guide:

[http://appdb.winehq.org/appview.php?iVersionId=7440](http://appdb.winehq.org/appview.php?iVersionId=7440)
>     * If you are unable to mount the DVD, make sure that /etc/fstab's entry for your cdrom has type auto.
    * You may need to copy the CD's contents to your hard disk to install.
    * When a white window pops up during installation, you must close it by killing EReg.exe.
    * The game needs a crack
    * Extract the contents of this archive into the directory where you installed the game
    * Run 'winecfg' and set the Windows version for 'cnc3.exe' to Windows XP. Then, go to the sound tab and select ALSA as the only sound driver, and set hardware acceleration to 'Full'
    * Create the file ~/.asoundrc, and put the following in it:
      pcm.cnc {
      type asym
      playback.pcm "hw:0"
      }
    * Run 'regedit', and navigate to 'HKEY_CURRENT_USER\Software\Wine', then add the key 'ALSA Driver'. In it, add the following strings with the values
      AutoScanCards = N
      DeviceCount = 1
      devicePCM1 = cnc
    * While still in regedit, navigate to 'HKEY_CURRENT_USER\Software\Wine\AppDefaults\cnc3.exe', then add a key 'Direct3D'. In it, add a string value named 'UseGLSL' and set it to 'enabled'
    * Place d3dx9_29.dll and gdiplus.dll in Wine's windows/system32 directory (usually ~/.wine/drive_c/windows/system32)
    * You must disable all compositing desktop managers before starting the game.
    * Once the game has started, go to the settings screen and set shader quality to 'low'. If your Wine version is older than 0.9.33, read the info below'



And I think I did everything right though the registry bit confused me a little, I'm not sure how deep to create the keys. I've attached a jpg showing what I've done.

The game plays fast enough - though shaders don't work. But there is NO sound.

I would really appreciate some help in getting the sound to work!

Thanks a lot,

EDIT: I got the sound working by setting AutoScanCard to Y but it screws with my frame rate! A better solution  would great! PLEASE! :)

Rudolf

---

