---
title: "xine-ui use wrong skin directory"
date: 2008-04-22
forum: x86 64-bit Users
---

### Post by chris_pmf on 2008-04-22
With Kubuntu Hardy RC1 I can't get xine-ui running like it should (with skins)... with hardy 32-bit this worked!

I build xine-lib like this:
```
./configure --prefix=/opt/xine --with-xv-path=/usr/lib --enable-antialiasing
```and xine-ui this way:
```
./configure --prefix=/opt/xine --enable-vdr-keys
```The problem is, that xine-ui looks ugly because it's not using the skin.

xine-check shows me why:
```
$ xine-check
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.24-16-generic)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ good ] found the player at /opt/xine/bin/xine
[ good ] /home/chris/bin/xine is in your PATH
[ good ] found /home/chris/bin/xine-config in your PATH
[ good ] plugin directory /opt/xine/lib/xine/plugins/1.1.10 exists.
[ good ] found unknown plugin: xineplug_post_audiochannel.so
[ good ] found unknown plugin: xineplug_post_autocrop.so
[ good ] found input plugins
[ good ] found demux plugins
[ good ] found decoder plugins
[ good ] found video_out plugins
[ good ] found audio_out plugins
[OUCH!!] no skin directory (/opt/xine/share/skins)
         The skin-directory doesn't exist. xine-config claims that there
         is a skin directory at /opt/xine/share/skins.
         However, there is no such directory.
         You probably need to reinstall xine-ui.
         press <enter> to continue...

[ good ] /dev/cdrom points to /dev/scd0
[ good ] /dev/dvd points to /dev/scd0
[ hint ] Your DVD drive seems not to be attached via ATAPI.
         This might be due to the use of an ide-scsi emulation.
         If you really have a SCSI DVD drive, your SCSI controller is likely
         to do perfect DMA, so there's no reason to worry about this.
         However, if you're using ide-scsi, there is a chance that DMA is
         disabled for the DVD drive. Moreover, I don't know how to enable
         DMA in that case, so you probably have to live with some performance
         loss. (FIXME: check for /proc/ide, provide solution)
         press <enter> to continue...

[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  YUY2 YV12 UYVY I420
```But why is xine looking in **/opt/xine/share/skins** and not in **/opt/xine/share/xine/skins** for the skin :confused:

PS: I compile xine by myself, because I need the libxineout-plugin for my VDR

Thanks in advance :)

---

### Post by warp99 on 2008-04-23
> But why is xine looking in **/opt/xine/share/skins** and not in **/opt/xine/share/xine/skins** for the skin :confused:

PS: I compile xine by myself, because I need the libxineout-plugin for my VDR

Thanks in advance :)

So either move the skins into /opt/xine/share/skins or just put a symlink:
```
sudo ln -s /opt/xine/share/xine/skins /opt/xine/share/skins
```
problem solved.

---

### Post by chris_pmf on 2008-04-23
Unfortunately the problem still exist (see screenshot) though xine-check say everything is ok.

---

