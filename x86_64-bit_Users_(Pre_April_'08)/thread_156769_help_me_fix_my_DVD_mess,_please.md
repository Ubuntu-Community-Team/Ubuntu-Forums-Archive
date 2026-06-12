---
title: "help me fix my DVD mess, please"
date: 2006-04-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by seatea on 2006-04-07
After giving things  a rest for a couple of months after multiple failed attempts to get DVD playback, I decided  to try again. Unfortunately, I still haven't learned enough to get any  of  the  DVD players working on  my  setup. Almost all the players will quit or freeze and leave my monitor colors yellow and blue, a very ugly sight, but everything still functions. It then takes logging out and then back in again  to correct things. I can get sound with xine-ui, but no picture and the same color problem occurrs.  Does anyone have a suggestion? 


Also, I still can't get RealPlayer to work with the websites I need it to. Of course, none of the other players will work as a replacement. Are these players just impossible to get to work well on ppc systems?

---

### Post by gerbman on 2006-04-07
[QUOTE=seatea]After giving things  a rest for a couple of months after multiple failed attempts to get DVD playback, I decided  to try again. Unfortunately, I still haven't learned enough to get any  of  the  DVD players working on  my  setup. Almost all the players will quit or freeze and leave my monitor colors yellow and blue, a very ugly sight, but everything still functions. It then takes logging out and then back in again  to correct things. I can get sound with xine-ui, but no picture and the same color problem occurrs.  Does anyone have a suggestion? 


Also, I still can't get RealPlayer to work with the websites I need it to. Of course, none of the other players will work as a replacement. Are these players just impossible to get to work well on ppc systems?[/QUOTE]Hi there, let's start with something simple. Have you tried the wiki article on [dvd playback]("https://wiki.ubuntu.com/RestrictedFormats?highlight=%28dvd%29%7C%28playback%29#head-cd84b8e23927ccdb4bb55ffd3074687abec0cf3b")?

---

### Post by seatea on 2006-04-08
I have visited that page and followed all the recommendations. I even went over everything there again, but it still didn't work.

I don't know if this helps narrow down the problem, but here is my xine-check output: 

"Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.12-10-powerpc)
[ hint ] Architecture is ppc (not intel), assuming there is no MTRR.
         MTRR (Memory Type Range Registers) are used on intel CPUs to
         control caching mechanisms for special memory ranges. There is
         probably nothing like this on ppc CPUs...
         press <enter> to continue...

[ good ] found the player at /usr/bin/xine
[ hint ] multiple xine executables found in your PATH
         I have found more than one occurance of 'xine' in your PATH:
         /usr/bin/X11/xine
         /usr/bin/xine
         You have probably installed xine-ui more than once, or the directory
         where you have installed xine occurs more than once in your PATH.
         Technically, this is not really a problem, but it's probably
         somewhat confusing, as it's not obvious, which xine you're using.
         You should probably uninstall the copies that you don't use...
         Further tests assume, you're using /usr/bin/X11/xine
         press <enter> to continue...

[ hint ] several instances of xine-config found in your PATH
         xine-config executables have been found in these places:
         /usr/bin/X11/xine-config
         /usr/bin/xine-config
         This probably means you have several versions of xine-lib installed.
         It's probably best to uninstall all unused xine-libs.
         Further tests will use /usr/bin/X11/xine-config.
         press <enter> to continue...

[ good ] plugin directory /usr/lib/xine/plugins/1.0.1 exists.
[ good ] found unknown plugin: xineplug_flac.so
[ good ] found input plugins
[ good ] found demux plugins
[ good ] found decoder plugins
[ good ] found video_out plugins
[ good ] found audio_out plugins
[ good ] skin directory /usr/share/xine/skins exists.
[ good ] found logo in /usr/share/xine/skins
[ good ] I even found some skins.
[ good ] /dev/cdrom points to /dev/hdc
[ good ] /dev/dvd points to /dev/hdc
[ good ] DMA is enabled for your DVD drive
[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  2YUY YVYU 21VY 024I" 

I tried removing the alleged duplicate files that weren't used. That was a big mistake and took me hours to correct as I had  so much trouble re-installing the correct xine-config files. I am still not  sure what finally restored them, but it didn't  make  any difference.

---

### Post by seatea on 2006-04-09
I have had partial success  with my DVD player problem. I went through  the  xine FAQ(DUH!) and found this partial fix:

"The image looks strange, it is shifted, cropped or shows weird lines!

This points to a problem with the Xv extension, which is used by xine to display the video image. To verify this, try running xine with the XShm video output plugin: 
***xine -V XShm

If that works fine, you just proved, that the Xv extension is buggy. xine will remember the last used video output plugin, so the setting will stay at XShm. You could simply continue using this, but XShm is a lot slower than Xv, so read on and see if you can get it working. Usually you should look for updated versions of the XFree driver module that belongs to your graphics card. 

Other possibilites are limitations in either your XFree driver module or your graphics hardware. If your card could somehow be running out of ressources (graphics RAM perhaps) and displays an incorrect Xv overlay because of that, try reducing the display resolution and/or colour depth. 

Consult the next question for more details on Xv. 
------------------------------------------------------------------------
How can I make xine use the Xv extension and what drivers do I need?

xine will normally use Xv by default if it is available. In some cases you might need to choose Xv playback manually (when the ~/.xine/config file for some reason says that you want to use XShm): 
***xine -V Xv

If this doesn't work for you, it may be possible that Xv is not present on your system. 

First you need to install/use XFree 4.x. Once you got that you have to make sure the XFree drivers you're using are supporting Xv on your hardware. Here are some hints for individual gfx chips: 


*	

3Dfx: if all you get is a solid black window, upgrade at least to XFree 4.1.0 

*	

ATI: if you only get "half a picture", try lowering your resolution or bit depth, disable DRI (looks like you ran out of video RAM)	

*	

Trident card: If you see vertical bands jumbled, upgrade to the latest xfree/experimental trident drivers (for the CyberBlade XP a driver exists here: [http://www.xfree86.org/~alanh/](http://www.xfree86.org/~alanh/) ) 

*	

nVidia: With newer GeForce cards, Xv should work with XFree 4.2.0 or newer, for older RivaTNT cards use the binary drivers from nvidia (of course the binary drivers work as well for GeForce cards) 

*	

Mach64/Rage3D (not Rage128/Radeon) cards/chips get no XVideo with standard drivers, try GATOS drivers instead 

*	

intel: i815 has Xv support in XFree 4.x, others unknown 

*	

Permedia 2/3 has Xv support in XFree 4.x 

*	

Savage: at least some older drivers tend to lock up the whole machine, try the drivers available from [http://www.probo.com/timr/savage40.html](http://www.probo.com/timr/savage40.html) . 

*	

SIS: certain controllers (more info needed!) have Xv support in XFree 4.x 

*	

Chips and Tech 6555x, 68554, 69000, 69030 have Xv support in XFree 4.x 

*	

NeoMagic: certain controllers (more info needed!) have Xv support in Xfree 4.x 

*	

SiliconMotion: certain controllers (more info needed!) have Xv support in Xfree 4.x 

*	

Matrox: G200 or newer (but not Parhelia) have Xv support in XFree 4.x. For Parhelia, use the binary only drivers available from matrox' website. "

I have an ATI Technologies Inc. Rage Pro 128 video card. My computer, PM G4 400 576MB RAM, uses an AGP slot. The picture will play, but the  images  are out  of  focus. After a few seconds, the  screen becomes unresponsive to the controls and it is prone to quit. If i don't use the "xine -V XShm" command each time, the color problem will return. I have looked  throught the documentation, but I am stumped as to how to proceed to fix the image quality problem and run xine without using terminal. I may be mistaken, but doesnt Ubuntu ppc use Xorg instead of  XFree or am I just confused about  these programs?**

---

