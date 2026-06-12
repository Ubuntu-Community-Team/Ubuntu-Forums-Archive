---
title: "Boot problems!! System unstable at startup"
date: 2008-06-10
forum: x86 64-bit Users
---

### Post by indikid on 2008-06-10
Hi folks, need some help. Of lately my Ubuntu 8.04 seems to be running into some problems while booting. The system boots to the login screen and then crashes and automatically reboots... This process goes on in a loop. Tried restarting several times and came up with the same problem. Then I pressed Esc while booting and entered the Gurb boot menu and found 3 ubuntu kernels:

Ubuntu 8.04, Kernel 2.6.24 -18 -generic

Ubuntu 8.04, Kernel 2.6.24 -18 -(recovery Mode)

Ubuntu 8.04, Kernel 2.6.24 -17 -generic

Ubuntu 8.04, Kernel 2.6.24 -17 -(recovery Mode)

Ubuntu 8.04, Kernel 2.6.24 -16 -generic

Ubuntu 8.04, Kernel 2.6.24 -16 -(recovery Mode)

Ubuntu 8.04, Memtest 86+


I logged into the last one < Ubuntu 8.04, Kernel 2.6.24 -16 -generic > and was able to boot without any problem.

Now, what I'd like to know is --

>>>> How do i get Ubuntu to load the last kernel? i.e. [Ubuntu 8.04, Kernel 2.6.24 -16 -generic]

>>>> What are the other kernels? Do I need them??? i.e. - 

Ubuntu 8.04, Kernel 2.6.24 -18 -generic

Ubuntu 8.04, Kernel 2.6.24 -18 -(recovery Mode)

Ubuntu 8.04, Kernel 2.6.24 -17 -generic

Ubuntu 8.04, Kernel 2.6.24 -17 -(recovery Mode)

>>>> Can I delete these kernels?

>>>> How do I delete them?

I'm not that used to Ubuntu yet, still learning and have a long way to go so will need detailed explanations. 

Any help is greatly appreciated.... Thanks in advance**[B][B]**[/B][/B]

---

### Post by peitschie on 2008-06-10
Hi!

That sounds like quite a curler as far as problems go!

Ok, first thing is first... the easiest way to get rid of the other versions of the kernel is to uninstall them, but I wouldn't recommend doing this just yet!  It sounds like the latest one has screwed up somewhere along the way.

First, I'd try a reinstall of the latest kernel version.  This can be done by gooting the working version, then opening synaptic (System > Administrator > Synaptic... see here for more documentation about this: [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)).

Once this is open, click the "Reload" button in the top left hand corner to reload all the packages (just in case there is an update available.  Then, click on "Mark all upgrades".  Apply this and see if anything updates and installs (I ask as I know there is a new kernel coming down the line, but I don't know if it is released yet).

If this doesn't install a new kernel, then do a search for linux-image-2.6.24-18.  Right-click on the packages with green squares next to them and hit-reinstall.  Then hit apply again.  Let this complete, reboot your system, and come back and tell us if it helped or not :)

---

### Post by indikid on 2008-06-10
> **peitschie said:**
> Hi!

That sounds like quite a curler as far as problems go!

First, I'd try a reinstall of the latest kernel version.  This can be done by gooting the working version, then opening synaptic (System > Administrator > Synaptic... see here for more documentation about this: [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)).

Once this is open, click the "Reload" button in the top left hand corner to reload all the packages (just in case there is an update available.  Then, click on "Mark all upgrades".  Apply this and see if anything updates and installs (I ask as I know there is a new kernel coming down the line, but I don't know if it is released yet).

If this doesn't install a new kernel, then do a search for linux-image-2.6.24-18.  Right-click on the packages with green squares next to them and hit-reinstall.  Then hit apply again.  Let this complete, reboot your system, and come back and tell us if it helped or not :)

Hi Peitschie, Thanks for the help but not sure if it worked... I ran synaptic and reinstalled the Linux-image-2.6.24-18 and rebooted. Now the system is booting to the command line. Tried to do the normal boot but didn't work. In the recovery mode it shows that Gnome display manager has failed. Ubuntu kernel 2.6.24-16 has also come up with a gnome display failure and loads to the command prompt.... any ideas on how to go about this...? I'm kinda lost now.... 

Should I just try to uninstall kernel 2.6.24-18 completely and then update the system from kernel 2.6.24-17? -or am I talking complete nonsense! :) -- If that made any sense how do I go about it???

I'm currently using Kernel 2.6.24-17.

---

### Post by bpl07 on 2008-06-10
> **indikid said:**
> 
Now, what I'd like to know is --

>>>> How do i get Ubuntu to load the last kernel? i.e. [Ubuntu 8.04, Kernel 2.6.24 -16 -generic]

>>>> What are the other kernels? Do I need them??? i.e. - 

>>>> Can I delete these kernels?

>>>> How do I delete them?

I'm not that used to Ubuntu yet, still learning and have a long way to go so will need detailed explanations. 

Any help is greatly appreciated.... Thanks in advance**[B][B]**[/B][/B]

You don't need to delete them.  Ideally you'd like to use the most recent one, but since it's not working, it's a good thing you have the old ones to fall back on.  You could just use -16 or -17 until -19 comes out.

To set ubuntu to load -16 or -17 automatically, you need to edit your boot file:

```
sudo gedit /boot/grub/menu.lst
```

The first line that isn't commented out (doesn't start with a #) should be:

```
default         0
```

This line tells grub to load the first entry by default.  To load -17 automatically, change that number to 2.  To load -16 automatically, change that number to 4.  Save the file and restart.  Check system monitor when you log in to ensure you're using the correct kernel.

---

### Post by philinux on 2008-06-10
If you need a gui then startupmanager can do this easily without editing files.

---

