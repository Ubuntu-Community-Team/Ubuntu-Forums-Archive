---
title: "Is there a different ubuntu 64bit edition???"
date: 2006-08-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by dkariotis on 2006-08-09
Hi everybody. I just got into Linux community and installed the Dapper Drake(probably32bit) on my AMD64 laptop. I thought that there is one Dapper Drake release which "recognises" the 64 bit architecture. When i tried to install the nvidia-glx to make my video card(nvidia GeForce Go 5700) work properly, I received a message "Wrong architecture".
Is there an 64bit release of Dapper Drake which i should have istalled??
Where can i find it?
Thank you in advance for your time

---

### Post by kaffelars on 2006-08-09
There is a different version of Ubuntu for 64-bit processors. The software that comes with that version is compiled to take advantage of the 64-bit CPU.

To find it, go to [http://www.ubuntu.com/download]("http://www.ubuntu.com/download")
and pick your nearest mirror. 
You then get a list of versions, you want the one called "**64-bit PC (AMD64) desktop CD**".

Good luck :)

---

### Post by ubunick on 2006-08-09
As far as I know, there is a 64-bit version (I'm using it..) on the Downloads page via Ubuntu.com.

Enjoy.

---

### Post by tzulberti on 2006-08-09
To see if you are using ubuntu 64 do the following: when the grubs loads, see it is says Ubuntu (.... amd64). You could read the file /boot/grub/menu.lst to see this. If it does not says amd64 or 64 architecture, then you are using ubunt 32

---

### Post by a-musing amazon on 2006-08-09
Also be aware that the installation disk contains kernel and applications which are generic AMD64. These should work on any AMD64 processor.

Once you have these running you can also select the most appropriate flavour of AMD64 for your kernel and your ATI/NVIDIA video drivers (which use kernel drivers). There are, for example k8 and SMP (for x2) versions that contain optimisations for your particular CPU(s).

If you install these they will also be added as seperate options on your grub boot menu.

---

### Post by dkariotis on 2006-08-09
Thank you all. I'll be happy to have you around.

---

### Post by VirtuAlex on 2006-08-09
You can easily see what kernel are you running by
```
uname -r
```
Guys also forgot to inform you that you may as well pretend that your processor is not 64bit and use regular i386 ubuntu and all 32bit drivers. But you did not ask that. By the way, what is wrong with using nvidia-glx from repositories? It should not complain about architecture.

---

### Post by Lonthong on 2006-08-10
> **a-musing amazon said:**
> 
Once you have these running you can also select the most appropriate flavour of AMD64 for your kernel and your ATI/NVIDIA video drivers (which use kernel drivers). There are, for example k8 and SMP (for x2) versions that contain optimisations for your particular CPU(s).

If you install these they will also be added as seperate options on your grub boot menu.

Hello,
I installed Ubuntu 64 bit on to my laptop (Turion X2 + ATI X1100)
I already upgraded to latest ATI proprietary driver (my card was identified as X200 - which is quite true).
I also successfully installed Firefox32 bit with flash & Java plugins
I also managed to get WM9 file to work with Mplayer 32

Since you mentioned about CPU optimization (For my case = smp) which I don't know about (total new to linux). Can you advise where/which howto to look & read???

Thanks

---

### Post by RAOF on 2006-08-10
You don't need to care about SMP.  All of the amd64 kernels have SMP enabled (except, perhaps, the generic one.  Anyone want to jump in on that?)

---

### Post by Lonthong on 2006-08-10
> **RAOF said:**
> You don't need to care about SMP.  All of the amd64 kernels have SMP enabled (except, perhaps, the generic one.  Anyone want to jump in on that?)

uname -r gave me this: 2.6.15-26-amd64-generic
What is the non-generic one?

---

### Post by RAOF on 2006-08-10
> **Lonthong said:**
> uname -r gave me this: 2.6.15-26-amd64-generic
What is the non-generic one?

The **linux-amd64-k8** package.  Install that, and you get a (definitely) SMP kernel.

---

### Post by kaffelars on 2006-08-11
I installed the 64 bit edition yesterday (on a Pentium D 920) with the generic AMD64 kernel. The Gnome system monitor chows 2 CPU's, so it seems like SMP works fine out of the box :)

---

### Post by a-musing amazon on 2006-08-11
AFAIK both the AMD64-generic and AMD64-k8 are SMP enabled (the generic wouldn't be generic if it didn't work on all AMD64 architectures). However there is a AMD64-k8-SMP kernel in the repositories. This had the appropriate optimisation flags set when the kernel was compiled so as to make best use of your multi-core CPU.

How much improvement in performance you actually see with a typical desktop usage I can't say (I have a plain Athlon64 3000+ and use the AMD64-k8 kernel).

---

### Post by Lonthong on 2006-08-12
> **a-musing amazon said:**
> AFAIK both the AMD64-generic and AMD64-k8 are SMP enabled (the generic wouldn't be generic if it didn't work on all AMD64 architectures). However there is a AMD64-k8-SMP kernel in the repositories. This had the appropriate optimisation flags set when the kernel was compiled so as to make best use of your multi-core CPU.

How much improvement in performance you actually see with a typical desktop usage I can't say (I have a plain Athlon64 3000+ and use the AMD64-k8 kernel).

Right, SMP is enabled with Amd64 generic. I saw it somewhere in my system.
Which is better for Turion X2: generic or AMD64-k8??

---

### Post by Realos on 2006-08-12
Hi Lonthong,

> **Lonthong said:**
> Hello,
I installed Ubuntu 64 bit on to my laptop (Turion X2 + ATI X1100)
I already upgraded to latest ATI proprietary driver (my card was identified as X200 - which is quite true).
I also successfully installed Firefox32 bit with flash & Java plugins
I also managed to get WM9 file to work with Mplayer 32


I have been trying to install 3D desperately on "Ubuntu 6.06 i386".

I also have a Turion 64 X2 TL-50 (Fujitsu-Siemens Amilo Pa 1510) with ATI Mobility Radeon X1100 video card. I have not been able to enable 3d so far. 

I have been following instructions from following site:

[HTML]http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide[/HTML]


Would you please share your way of installation? That may be helpful to more people.

cheers,

---

### Post by kaffelars on 2006-08-13
I don't think this thread is the best to ask regarding 3D issues. You should probably look around, or make a new one.

However, if you *do* find a working solution, please let me know :)
I have an X600 that doesn't want to do OpenGL ](*,)

---

### Post by Lonthong on 2006-08-15
> **Realos said:**
> Hi Lonthong,



I have been trying to install 3D desperately on "Ubuntu 6.06 i386".

I also have a Turion 64 X2 TL-50 (Fujitsu-Siemens Amilo Pa 1510) with ATI Mobility Radeon X1100 video card. I have not been able to enable 3d so far. 

I have been following instructions from following site:

[HTML]http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide[/HTML]


Would you please share your way of installation? That may be helpful to more people.

cheers,


I also followed that exact instruction (method 2). 
If I remember correctly, I also successfully followed method 1 but then later on I made mistakes with other installation stuff (compiz) and I just  reinstalled the whole things and followed method 2 directly.
Edit: I never tried 6.06_i386. I installed 6.06_amd64 if that made any difference at all....

---

### Post by MetalMusicAddict on 2006-08-15
For anyone wondering. The K7, 32-bit kernels have SMP enabled also. Works great on my 4600 AM2.

---

### Post by Lonthong on 2006-08-15
> **RAOF said:**
> The **linux-amd64-k8** package.  Install that, and you get a (definitely) SMP kernel.

Searching synaptic, I found these 3 packages that have version 2.6.15-26:
linux-headers-2.6.15-26-amd64-k8
linux-restricted-modules-2.6.15-26-amd64-k8
linux-image-2.6.15-26-amd64-k8

Which one should I install or should I install them all?? Sorry, newbie question

---

### Post by RAOF on 2006-08-15
> **Lonthong said:**
> Searching synaptic, I found these 3 packages that have version 2.6.15-26:
linux-headers-2.6.15-26-amd64-k8
linux-restricted-modules-2.6.15-26-amd64-k8
linux-image-2.6.15-26-amd64-k8

Which one should I install or should I install them all?? Sorry, newbie question

None of them.  You should install the **linux-amd64-k8** package.  That will install the latest -k8 kernel, keep it up to date, and make sure your restricted drivers stay up to date, too.

---

### Post by Lonthong on 2006-08-15
> **RAOF said:**
> None of them.  You should install the **linux-amd64-k8** package.  That will install the latest -k8 kernel, keep it up to date, and make sure your restricted drivers stay up to date, too.

There are 2 packages.
First I tried linux-amd64-k8-smp but one of the Turion core kept running at full speed. Uninstalled & tried linux-amd64-k8, result was the same, i.e. one core running constantly at top speed - no dynamic throtling.
so I just went back with the generic kernel. While I am just browsing like now, cpu load is max 15% per core. 

I am dual booting Ubuntu64 & Win Xp. It seemed that my fan spinned at lower rpm in Ubuntu.

---

