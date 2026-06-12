---
title: "Installing 32bit packages without chroot"
date: 2005-07-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tamir on 2005-07-21
Hi,

if you have no choice, and you have to install 32bit package like win32codecs,
please do it with ```
dpkg --force-architecture
``` and not with chroot.
it can make your life easier  ;-)

---

### Post by Jet2k5 on 2005-07-21
How ill this apply to Firefox and flash?  And all those other diffty plugins that are not available for 64-bit?

---

### Post by Tamir on 2005-07-22
[QUOTE=Jet2k5]How ill this apply to Firefox and flash?  And all those other diffty plugins that are not available for 64-bit?[/QUOTE]
 Yes, it should. for example: if you are running mplayer, you should install the win32codecs and 32bit of mplayer. mplayer 64bit with win32codecs will not work.

with firefox - 32bit version of firefox + flashplayer (32bit).

---

### Post by negatory on 2005-07-22
But is it possible to force the arch and install the 32bits debs and they will be working? (In firefox and flash for example and in Mplayer and w32codecs...)
Thanks.
Pedro Carrico

---

### Post by Tamir on 2005-07-22
[QUOTE=negatory]But is it possible to force the arch and install the 32bits debs and they will be working? (In firefox and flash for example and in Mplayer and w32codecs...)
Thanks.
Pedro Carrico[/QUOTE]
 Ofcource! Don't ever forget that you amd64 supports 32bit too!

---

### Post by Jet2k5 on 2005-07-22
That is one of the beuties of AMD64.  Backward compatability with 32-bit code :)

---

### Post by DancingSun on 2005-07-22
Is there a way to list the 32-bit only packages in Synaptic?  That way we will be able to install the 32-bit backport packages like OOo2 beta!

---

### Post by negatory on 2005-07-22
But won't the libraries be broken?I'm a little skeptical about that...just yesterday I downloaded the 32bit binary for NVU and it kept on crashing in my system but it works fine inside the chroot.
I've installed 32bit applications before, mostly games, that work fine but I think they just need simple libraries like openGL or some of the X libraries...
If we can force the arch what's the need for a chroot?The programs that we install are supposed to look for libs in the /lib (wich is a symlink to /lib64) will the 64bit libs work on 32bits programs?
I just have little doubts, that's all...please help me clear things out.
Thanks.
Pedro Carrico

---

### Post by Jet2k5 on 2005-07-23
Good point.  How do you play games in cedega?  Or 64-bit?  Just downlod them and play them, or do you have to set up a chroot system to play games?

---

### Post by negatory on 2005-07-23
Most games work "out of the box" (America's Army),others have the 64bit binaries also (UT2004) and some have to be pointed to the correct libraries (Doom 3).I think that they'll all work under a chroot if you've got the base system with correct drivers and configuration...so I think.
Pedro Carrico

---

### Post by Chareos on 2005-08-01
So, Which line should I exactly type to get installed firefox + flash + java runtime in 32 bit version ?

And, of course, what to type to get back if something goes wrong ?

---

### Post by NetDiver on 2005-08-07
Hi Tamir,

thanks for the info about installing 32bit packages.
But I would also like to know how it works exactly.
An example for 32bit firefox and flash would be nice!

---

