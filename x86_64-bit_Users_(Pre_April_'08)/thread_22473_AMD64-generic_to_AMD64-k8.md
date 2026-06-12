---
title: "AMD64-generic to AMD64-k8"
date: 2005-03-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by mthaddon on 2005-03-27
Can someone advise on moving from amd64-generic kernel to amd64-k8. I have discovered that this is more tailored to my system. I currently have most things working nicely (Nvidia drivers, WiFi, etc.).

Should it just be as simple as installing (I'm using th 2.6.10-5 kernel and am very happy with it so far):

linux-image-2.6.10-5-amd64-k8
linux-headers-2.6.10-5-amd64-k8
linux-restricted-modules-2.6.10-5-amd64-k8 

and then installing/reinstalling nvidia-glx and ndiswrapper? Also, any comments on whether this move is worthwhile would be appreciated.

Thanks, Tom

---

### Post by Pse on 2005-03-28
You should have no problems in doing so. I've done it, and booted first time without any issues.
In any case, should you have any problems, the Debian installer will automagically create the correct menu.lst entries for GRUB so you can still boot your old kernel...=)

---

### Post by songochain on 2005-03-29
[QUOTE=mthaddon]Can someone advise on moving from amd64-generic kernel to amd64-k8. I have discovered that this is more tailored to my system. I currently have most things working nicely (Nvidia drivers, WiFi, etc.).
 
Should it just be as simple as installing (I'm using th 2.6.10-5 kernel and am very happy with it so far):
 
linux-image-2.6.10-5-amd64-k8
linux-headers-2.6.10-5-amd64-k8
linux-restricted-modules-2.6.10-5-amd64-k8 
 
and then installing/reinstalling nvidia-glx and ndiswrapper? Also, any comments on whether this move is worthwhile would be appreciated.
 
Thanks, Tom[/QUOTE]
U will not have problems if u install that kernel, i suggest u to use a k8 kernel.
Of course u have to recompiled ndiswrapper,nvidia drivers... If something is wrong u can choose your old kernel without any problems. Also u can probe to compile your own kernel (there're a lot of modules in a kernel-image that arent necessary)

---

### Post by negatory on 2005-03-29
I've done this and no worries here!It installed the latest kernel and updated GRUB and worked just fixe!

Pedro Carrico

---

### Post by mthaddon on 2005-04-01
This worked a treat. X didn't come up first time, as I have nvidia and obviously this needed updating.

As it happened, there was a bunch of updates waiting for me, including nvidia-glx. All I did was sudo apt-get upgrade from the console and then rebooted, and here I am happily back in GUI mode running amd64-k8 kernel.

God I love Ubuntu. Definitely my best linux experience so far!!

---

### Post by kks on 2005-04-01
How does one get the kernel-source-2.6.10-4-amd64-generic in the first place. I am unable to get get DRI support for NDIDIA.
#glxinfo |grep rendrer
OpenGL renderer string: Mesa GLX Indirect
#ls /usr/X11R6/lib64/modules/dri |grep nvidia
NULL

Some advice please. I am nee to ubuntu. 

kks

---

### Post by MarsDude on 2005-04-02
[QUOTE=mthaddon]Can someone advise on moving from amd64-generic kernel to amd64-k8. I have discovered that this is more tailored to my system. I currently have most things working nicely (Nvidia drivers, WiFi, etc.).

Should it just be as simple as installing (I'm using th 2.6.10-5 kernel and am very happy with it so far):

linux-image-2.6.10-5-amd64-k8
linux-headers-2.6.10-5-amd64-k8
linux-restricted-modules-2.6.10-5-amd64-k8 

and then installing/reinstalling nvidia-glx and ndiswrapper? Also, any comments on whether this move is worthwhile would be appreciated.

Thanks, Tom[/QUOTE]

I have moved... just replacing the linux-blah-generic packages with the k8 ones.

This does expose a big naming flaw in ubuntu (and they're not alone). Amd64 implies an amd processor... but as you can see from the different amd64 kernels... it is not nescesarily so. x86_64 is a much better option. you'd have x86_64-generic , k8 or whatever.

---

### Post by wmcbrine on 2005-04-02
TTBOMK, the AMD64 name is a tribute to AMD, for inventing the arch, and a slap at Intel, for failing to acknowledge that their "EM64T" (or whatever it's called today) is actually a copy of AMD's arch. (Nothing wrong with the copying, especially since they have cross-licensing agreements; it's the non-acknowledgement that has some people annoyed.)

---

### Post by mthaddon on 2005-04-05
Just in case anyone's interested, I just tested glxgears, and it jumped up a nice 300 fps for me from avg 1700 to avg 2000.

This was amd64-k8 compared to amd64-generic, and also with newer a nvidia module (7167 vs 6629, I believe), so it could have been either of these that affected the performance. 

Whatever it is, I'm more than happy...

---

### Post by dickysan on 2005-04-29
I have upgraded to K8 as well.  Everything seems to be working well with the exception of ndiswrapper.  When I try to recompile ndiswrapper using
make distclean
make 
make install

make and make install kick back errors with something to the effect of a vaild path to the k8 modules not being found (at work exact error not on hand).  What do I need to do to correctly recompile the ndiswrapper?

when I run modprobe ndiswrapper I get a fatal error


Thanks for any help

---

### Post by rsw on 2005-05-16
when i tried moving to the k8 image, nvidia-glx would not install to it, instead only installing the module back in the generic kernels tree. How did you guys get around this? 

Installing the nvidia driver from nvidia's site results in the xorg6.8.2-no-symbols-found bug (meaning you have to reinstall the nvidia driver every reboot). So I'm stuck using the nvidia-glx package until a newer version of xorg hits ubuntu-x86_64 :(

---

### Post by Chareos on 2005-05-17
ehi, I'm having this exact problem right now !


With out-of-the-box Hoary kernel installed nvidia from Synaptic -- all ok.

Then tried Ubuntu kernel 2.6.11 ... no nvidia drivers (missing restricted ?)

Then tried compile a my own kernel (all ok) and installed in the linux way and in dpkg way... both times same problem: Synaptic's nvidia drivers nod't get loaded (missing module, of course) and if I install 'em by the nvidia's way each reboot I get the symbol error.



So there is no way to install nvidia drivers to any kernel other than Ubuntu 2.6.10 ?

(damn, I *must* use a recent 2.6.11 cause fixes me a problem with videocard...)

---

### Post by arunsub on 2005-05-17
1. What's the difference between generic and K8 and what's the advantage of using K8?
2. Is there a K8 kernel available for 32 bit Linux? I have Athlon 64 2800+ and I'm using 32bit Ubuntu. The reason is I can't use win32codec, flash player etc, so I went to 32 bit from 64 bit.

Thanks.

---

### Post by aramazan on 2005-05-17
[QUOTE=mthaddon]Can someone advise on moving from amd64-generic kernel to amd64-k8.[/QUOTE]I've fallen back to generic kernel due to powernowd hard freeze problem as reported in: [https://bugzilla.ubuntu.com/show_bug.cgi?id=10668](https://bugzilla.ubuntu.com/show_bug.cgi?id=10668)
I'm on generic kernel almost for a week now and no freezes so far. I'm surprised no one here has hit this problem.

---

### Post by rsw on 2005-05-17
i'd like to know how the ubuntu dev's are making the nvidia-glx package for 2.6.10-5. They must be using a patch to get around the no-symbols bug :/  Ive not messed with debian src packages, anyone have a howto out there or info on breaking them apart to see the innards? :)

---

### Post by etitor on 2005-06-23
[QUOTE=dickysan]I have upgraded to K8 as well.  Everything seems to be working well with the exception of ndiswrapper.  When I try to recompile ndiswrapper using
make distclean
make 
make install

make and make install kick back errors with something to the effect of a vaild path to the k8 modules not being found (at work exact error not on hand).  What do I need to do to correctly recompile the ndiswrapper?

when I run modprobe ndiswrapper I get a fatal error


Thanks for any help[/QUOTE]

So, dickysan, have you ever got your ndiswrapper working under k8 Ubuntu? I dont want to go back to 64 generic, but I need to wake up my wireless lan card.

---

