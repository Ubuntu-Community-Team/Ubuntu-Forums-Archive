---
title: "Google Earth on AMD64?"
date: 2006-06-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by gadfium on 2006-06-13
I've downloaded the Google Earth linux beta, and installed it with no problems (as normal user), but when I try to run it it says 
"error while loading shared libraries: libXrender.so.1: cannot open shared object file: No such file or directory"

I have the normal /usr/lib/libXrender.so.1, which is a link to /usr/lib/libXrender.so.1.3.0, so I'm wondering if this is an AMD64 problem. Do I need to set up a chroot for Google Earth, or would it be simpler if I simply upgrade to 6.06 Kubuntu, which I understand is more willing to run 32-bit applications.

I plan to upgrade in a week or so anyway, so that would be no big deal.

---

### Post by skeff on 2006-06-19
It probably is an AMD64 problem, as /lib is the directory for 64bit libraries. So as Google Earth beta gives no choice in 64 or 32 bit, it probably is 32 bit and cannot link to 64bit libraries. 

So you need 32bit libXrender.

Whether this library is in one of the ia32-libs packages in official Ubuntu repositories, I don't know.

---

### Post by superm1 on 2006-06-23
I run it on my 6.06 amd64 ubuntu box no difficulties.  I have pretty much all the 32 bit libraries available in the repositories.

---

### Post by annihilation on 2006-11-04
Hi, how did you get it work though. Can you describe the installation procedure to me. It crashes every time I run it giving me the following error.

"Google Earth has caught signal 11.

Stacktrace from glibc:
  ./googleearth-bin(__gxx_personality_v0+0x21e) [0x804ab52]
  ./googleearth-bin [0x804b153]
  [0xffffe500]
  /usr/lib32/libX11.so.6(XQueryExtension+0x17) [0x573e3fc7]
  /usr/lib32/libX11.so.6(XInitExtension+0x3b) [0x573d854b]
  /usr/lib32/libXext.so.6(XextAddDisplay+0x49) [0x573b251c]
  /usr/lib32/libGL.so.1 [0x574f1394]
  /usr/lib32/libGL.so.1(__glXInitialize+0x1f) [0x574f1a5b]
  /usr/lib32/libGL.so.1(__glXSetupForCommand+0x47) [0x574f2a11]
  /usr/lib32/libGL.so.1(glXSwapIntervalSGI+0x9d) [0x574eff57]
  ./libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext15setSwapIntervalEi+0x100) [0x56be3730]
  ./libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext4openEv+0x568) [0x56c1f028]
  /home/rahul/google-earth/libevll.so(_ZN5earth4evll13VisualContext11openContextEN3Gap3Gfx25igRenderDestinationFormatERKNS0_8InitInfoE+0xff) [0x5b01bf1f]
  /home/rahul/google-earth/libevll.so(_ZN5earth4evll13VisualContext4initERKNS0_8InitInfoE+0x255) [0x5b01daa5]
  /home/rahul/google-earth/libevll.so(_ZN5earth4evll17RenderContextImpl4initERKNS0_8InitInfoE+0x3f) [0x5afc752f]
  ./librender.so(_ZN12RenderWidget6setApiEPN5earth4evll3APIE+0x47) [0x570d01f7]
  ./librender.so(_ZN5earth6render12RenderWindow12createWidgetEv+0x8a) [0x570b4e5a]
  ./libgoogleearth.so(_ZN5earth6client12ModuleWidget9showEventEP10QShowEvent+0x7d) [0x55d0c7ed]
  ./libqt-mt.so.3(_ZN7QWidget5eventEP6QEvent+0x277) [0x563591f7]
  ./libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0xa1) [0x562ae691]
  ./libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xc9) [0x562af179]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x266) [0x56358156]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56357eab]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x563580f7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56357eab]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x563580f7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56357eab]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x563580f7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56357eab]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x563580f7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56357eab]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x563580f7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56357eab]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x563580f7]
  ./libqt-mt.so.3(_ZN7QWidget12showChildrenEb+0x11b) [0x56357eab]
  ./libqt-mt.so.3(_ZN7QWidget4showEv+0x207) [0x563580f7]
  ./libqt-mt.so.3(_ZN11QMainWindow4showEv+0x93) [0x5642c223]
  ./libqt-mt.so.3(_ZN7QWidget10showNormalEv+0x33) [0x563517c3]
  ./libgoogleearth.so(_ZN10MainWindow18readScreensizeInfoEv+0x7cb) [0x55ccd97b]
  ./libgoogleearth.so(_ZN5earth6client11Application3runEiPPc+0x156a) [0x55cf6fda]
  ./libgoogleearth.so(_ZN5earth6client11ApplicationC1EiPPcb+0x968) [0x55cf9038]
  ./googleearth-bin [0x804c75d]
  /lib32/libc.so.6(__libc_start_main+0xd2) [0x571bbea2]
  ./googleearth-bin(__gxx_personality_v0+0x4d) [0x804a981]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/rahul/.googleearth/crashlogs/crashlog-1A841BED.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions."

---

### Post by OrkanSpec on 2006-11-04
Kubuntu 6.10 amd64
Google Earth ver 4.0.2091
It works fine.

This program is a 32bit application and searches for 32bit libraries in /usr/lib32.

I have installed the following packages for 32bit compatibility:
linux32, ia32-libs-sdl, ia32-libs-gtk, ia32-libs-kde, ia32-libs-openoffice.org, lib32ncurses5.
If you install them, you should be running Google Earth without any problems.

Good luck!

---

### Post by saladasalad on 2006-11-04
Google Earth for amd64 is in the PLF repos.

---

### Post by kleeman on 2006-11-05
I've noticed that this program can segfault for various versions of the nvidia drivers. I use the latest beta drivers (9626),

---

### Post by cisbrane on 2006-11-05
i tired the amd64 in teh PLF, and well it said i missed that libXrender thing still, so i don't really know why they have that amd64 thing. 

I'm gonna try and install thoose 32 bit libs..

---

### Post by Samir33 on 2006-11-07
Ok people, tried on Ubuntu 6.10 amd64. I installed all neccesery libs. (ia32* & lib32*). GooleEarth installed fine. But when I try to run it, it gets stuck on splash screen, without any error messages... Very strange. Where does it keep some kind of log?

Aslo, tried installing it both as regular user and superuser, same error, stuck on splash screen. But I aslo tried installing it in 32-bit dchroot environment and it works without problems (but without 3D accel.). I managed to install few other 32-bit apps in this amd64 distro no problems at all.

Anybody has similar error? Maybe ati driver (fglrx) problem? Anybody knows if it is possible to enable 3D accel. in dchroot?!?

---

### Post by OriUbu on 2006-11-07
Try method one from this guide for your ati card worked no probs for me

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

Also google earth is in automatrix along with some more cool apps

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29)

Let us know how you get on.

---

### Post by Case_f on 2006-11-07
> **Samir33 said:**
> Ok people, tried on Ubuntu 6.10 amd64. I installed all neccesery libs. (ia32* & lib32*). GooleEarth installed fine. But when I try to run it, it gets stuck on splash screen, without any error messages... Very strange. Where does it keep some kind of log?

Aslo, tried installing it both as regular user and superuser, same error, stuck on splash screen. But I aslo tried installing it in 32-bit dchroot environment and it works without problems (but without 3D accel.). I managed to install few other 32-bit apps in this amd64 distro no problems at all.

Anybody has similar error? Maybe ati driver (fglrx) problem? Anybody knows if it is possible to enable 3D accel. in dchroot?!?

Same here with the latest fglrx. It seems to me like fglrx issue, because if I put MESA libGL stuff (either directly or via symlink, doesn't matter) into Google Earth directory, it runs just fine - only in software mode, of course, so quite slow. But at least it runs. And running GE in chroot doesn't solve this for me either.

---

### Post by Samir33 on 2006-11-08
Seems that it is fglrx, after all... Edgy amd64 auto-updated fglrx recently (reverted to version 8.28.8 ?!?). Has anyone tried installing newest (or some older version) drivers from ati & check if GoogleEarth works with them?!? ATI's driver seems to cause a lot of trouble in Linux...

@ Case_f: How did you actually "put MESA stuff" into GoogleEarth directory?

offtopic:
Long live The Cure! ;)

---

### Post by Case_f on 2006-11-08
> **Samir33 said:**
> Seems that it is fglrx, after all... Edgy amd64 auto-updated fglrx recently (reverted to version 8.28.8 ?!?). Has anyone tried installing newest (or some older version) drivers from ati & check if GoogleEarth works with them?!? ATI's driver seems to cause a lot of trouble in Linux...

As I've said, I'm using latest fglrx (as in 8.30.3.) And yeah, ATI sucks in Linux :(

> How did you actually "put MESA stuff" into GoogleEarth directory?

Just copy/symlink (symlinking is the 'cleaner' way, I guess) the original MESA libGL.so.1.2 into the GE directory (/opt/google-earth in my case) and then create symlinks to it named libGL.so and libGL.so.1, just like it is in /usr/lib (I don't know if this is really necessary to do, but it doesn't hurt anything, so...). The original MESA libGL is stashed away as libGL.so.1.2.xlibmesa in /usr/lib/fglrx when you install fglrx drivers. This way GE uses the library it finds first - the MESA one - and it works. But as I've said, it runs in software mode this way, so it is quite slow.

> 
Long live The Cure! ;)

;)

---

### Post by Samir33 on 2006-11-08
> **Case_f said:**
> 
Just copy/symlink (symlinking is the 'cleaner' way, I guess) the original MESA libGL.so.1.2 into the GE directory (/opt/google-earth in my case) and then create symlinks to it named libGL.so and libGL.so.1, just like it is in /usr/lib (I don't know if this is really necessary to do, but it doesn't hurt anything, so...). The original MESA libGL is stashed away as libGL.so.1.2.xlibmesa in /usr/lib/fglrx when you install fglrx drivers. This way GE uses the library it finds first - the MESA one - and it works. But as I've said, it runs in software mode this way, so it is quite slow.

In my case, this doesn't work for some weird reason!?! Tried both symlinking / copying... Added execution rights to libGLU.so & libGLU.so.1 too... wtf?!

---

### Post by Case_f on 2006-11-08
It's libGL, not libGLU...

---

### Post by Samir33 on 2006-11-08
Just a typo. But then I tried naming them both libGL.* and libGLU.* since libGLU.so.1 library is part of the GE installation and it's already inside GE  directory... What GE version you are using? It's 4.0.2414 here...

EDIT: I also tried to try to run xorg using "vesa" driver. GE Freezes again! This is very odd. I really don't know what to do. Maybe it's fglrx kernel module conflict (I didn't uninstalled fglrx module when I ran xorg in vesa mode). ](*,)

---

### Post by Case_f on 2006-11-08
It says 4.0.2413 (beta). Dowloaded just a few days ago (Saturday I guess).

---

### Post by Samir33 on 2006-11-14
Ok, I made it work! But it's unusable! 

First, I had to remove **xorg-driver-fglrx** and **linux-restricted-modules-*** completely to make it run! Damn ati! I hope AMD do something about this Linux driver situation, otherwise I will never buy / recommend to anyone any ATI graphics chips... :mad: 
I tried GoogleEarth in two ways, first with **vesa** driver, it ran, with 'software OpenGL' warning, pretty slow... Then I tried with **radeon** driver (reverse-engineered Open source r300 driver) and it was - slower! And it had friezed my machine for few times. Funny, but this freeze situation happens only with GoogleEarth. Other OpenGL stuff (like Ubuntu screen savers) seems to run fine, even the acceleration seems average, but slower than **fglrx**...
I also noticed that this **radeon** driver is much stable and seems faster  in 2D than **fglrx**, I think I'll stick to it for a while... Btw, my card is Mobility X700.

Damn ATI...

---

### Post by Case_f on 2006-11-14
Yes, GE with radeon driver is much slower than with fglrx and those MESA libs here too. Funny, but yes.

---

### Post by Mongoose on 2006-11-15
I've tried GoogleEarth on an ATi card recently and had garbage in the frame buffer.  I just had to resize the context to get it to clear, and ran fine after that.  Too bad my laptop doesn't have Nvidia GPU like my workstation.  =)

---

### Post by rutger83 on 2006-11-15
> **Case_f said:**
> Same here with the latest fglrx. It seems to me like fglrx issue, because if I put MESA libGL stuff (either directly or via symlink, doesn't matter) into Google Earth directory, it runs just fine - only in software mode, of course, so quite slow. But at least it runs. And running GE in chroot doesn't solve this for me either.

Google earth does run with fglrx 8.26.xx. As soon as you update to 8.29.xx or 8.30.3 it will hang on the splash screen. AMD really isn't always improving their drivers. Also, this 8.26.xx driver gives me MUCH higher fps in glxgears -printfps.

---

### Post by Case_f on 2006-11-15
Thanks, will try. But it runs with 8.30.3 just fine in 32bit Edgy.

---

### Post by dillbertdabomb on 2006-11-16
I look up something as simple as google earth - and am led here again! 
 
Yes it worked on windows for me and i have an amd64

---

### Post by Samir33 on 2007-01-11
any luck with new 4 release version?!?

---

### Post by Nangineer on 2007-01-12
I have installed the 32-bit compatibility packages mentioned on page 1 of this thread, and I downloaded the latest version on 64-bit Edgy. It works fine here.

---

### Post by Thingymebob on 2007-03-21
Hangs on startup with 8.34.8 is it anything to do with this?:
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge")

737-20868: Linux Distibutions with Modified XOrg X Servers May Not Be Compatible with the 3D Driver

    The information in this article applies to the following configuration(s):

        * XOrg 6.8.2
        * Linux

    Attempting to install the Driver on distributions that have updated certain 3D components outside of the stock XOrg 6.8.2 may result in the driver improperly initializing 3D applications.

    ATI Engineering has been advised of this issue and is investigating it. Any updates will be published when they become available.

---

### Post by saneone on 2007-03-21
I didn't encounter any problems runinng Google Earth or Google Picasa. I installed Google Earth form a third party repository. My OS is Edgy Eft amd64.

Google Earth:
[[img]http://img379.imageshack.us/img379/9246/snapshot16uv7.th.png[/img]](http://img379.imageshack.us/my.php?image=snapshot16uv7.png)

Google Picasa:
[[IMG]http://img463.imageshack.us/img463/3037/snapshot17tv7.th.png[/IMG]](http://img463.imageshack.us/my.php?image=snapshot17tv7.png)

---

