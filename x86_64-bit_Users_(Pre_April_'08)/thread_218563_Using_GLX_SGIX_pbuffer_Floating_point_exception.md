---
title: "Using GLX_SGIX_pbuffer Floating point exception"
date: 2006-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Biswarup on 2006-07-18
Hi, I just installed Ubuntu 6.06 LTS on my AMD64 bit machine (ATI Radeon XPRESS 200 series). 
I had some intial problems with X but with the guidelines at [http://www.ubuntuforums.org/showthread.php?t=218013]("http://www.ubuntuforums.org/showthread.php?t=218013") and the method (Method 1: Installing Dapper's Included Driver ( 8.25.18 )) at  [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide"),  I first installed Dapper's Included fglrx Driver ( 8.25.18 ). fglrxinfo gave me the correct output. But fgl_glxgears gives this:

biswarup@naren:~$ fgl_glxgears 
Using GLX_SGIX_pbuffer
Floating point exception
biswarup@naren:~$ 

So, I went ahead with the next method (Method 2: Generating/Installing Ubuntu packages for the 8.26.18 drivers in Ubuntu Dapper Manually) at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide").
Currently fglrxinfo on my system gives this:

biswarup@naren:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200 Series Generic
OpenGL version string: 2.0.5879 ( 8.26.18 )
biswarup@naren:~$ 

But fgl_glxgears still gives me: 

biswarup@naren:~$ fgl_glxgears 
Using GLX_SGIX_pbuffer
Floating point exception
biswarup@naren:~$ 

Has anybody come across the same problem ? I did google for it, but the links actually could not give me a solution. Could somebody please help me out ??

thanks. 
p.s: Am attaching my xorg.conf file (just in case).
p.p.s.: Am a Fedora guy, but I really wanna shift to Ubuntu ! :)

---

### Post by Kilz on 2006-07-18
Ok, I think you have the [right howto]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually") I have a radon xpress 200. I will try and help you, even though video drivers are not my strong point.
I looked over your xorg.conf and there were a few differences. Im attaching mine so you can see them. Im running the 8.26.18 drivers.
I would recommend the 8.26.18 drivers as the 8.25.18 ones have lots of problems for people with radon xpress graphics. 
If you want to try the howto again. Best to have the header files and build essenial installed(it cant hurt). Open a terminal and copy/paste this in.
```
sudo apt-get install build-essential linux-headers-`uname -r`
```
Then follow the howto. Keep an eye out for errors. If you get any copy the terminal output here.

---

### Post by Packard on 2006-07-24
I have the same issue here with my 64bit system. However, 3D is working, try "fgl_glxgears -fbo". Googleearth als oworks fine. So far I haven't found anything about why this floating point exception with fgl_glxgears appears.

---

### Post by spacetree on 2007-02-04
Same problem here

I have also an AMD64 machine, and i must say, im starting to hate ATI cards, some programas didnt work , thing that was resolved putting some directories in the ld.conf file, but the screensavers just dont work, 

I have the same output from fgl_glxgears.

---

