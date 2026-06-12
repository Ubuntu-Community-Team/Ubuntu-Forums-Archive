---
title: "What non-64bit kernel to use with AMD64"
date: 2006-07-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by daou on 2006-07-07
[10 Tips for new Ubuntu users]("http://www.unix-tutorials.com/go.php?id=595") says

> Ubuntu will install a 386 kernel for x86 machines, which probably isn't what you'd want if you've got a Pentium II or better CPU. The 386 kernel is compiled to work with just about any x86 CPU, but extensions that appear in later CPUs can give your system a boost, if they're taken advantage of. To replace the kernel, open Synaptic or Adept and search for linux-image. You'll see several choices. Pick the one that best suits your CPU -- probably the linux-image-686 package for Pentium II and later CPUs, and linux-image-k7 for later AMD processors. Note that if you're using the AMD64 line (or Intel's x86-64 CPUs) you should be using the amd64 images.

I am using an AMD64 3000+ CPU. Is the page referring to 64-bit kernels when they recommend the "amd64 images" for AMD64 users?
I would rather not get into the 64-bit OS hell after playing with WinXP x64. Which non-64bit kernel should I be using with my CPU? I am currently running the i386 version.

---

### Post by chadk on 2006-07-07
> **daou said:**
> [10 Tips for new Ubuntu users]("http://www.unix-tutorials.com/go.php?id=595") says



I am using an AMD64 3000+ CPU. Is the page referring to 64-bit kernels when they recommend the "amd64 images" for AMD64 users?
I would rather not get into the 64-bit OS hell after playing with WinXP x64. Which non-64bit kernel should I be using with my CPU? I am currently running the i386 version.

I'm using the K7 kernel on an AMD64.

---

### Post by tseliot on 2006-07-07
> **chadk said:**
> I'm using the K7 kernel on an AMD64.

Yep, that's the right (i.e. optimised) kernel to use

---

### Post by daou on 2006-07-07
I installed the k7 kernel but my gdm refuses to start. Does this have something to do with the new nvidia drivers and xorg.conf editing I've done for the 386 kernel?

---

### Post by Lil_Eagle on 2006-07-07
A lot depends on which version of the AMD64 you have.  With me, the K7 kernel also gives a lot of problems.  The i386 version of Mepis works (mostly).  The i386 version of Ubuntu didn't work at all on this machine, but the apparent modifications done by the Mepis team fixed most of the problems.  However, I don't really like the changes to KDE that Mepis did.  Therefore, I run the AMD64 kernel, and all my apps are also 64-bit.

The only exception is that I have a 32 bit browser because the 64-bit version crashes on occasion.  It makes no difference whether it is Firefox or Konqueror.  It may be related to the plug-ins because konqueror will at least show a sigterm 11 screen pointing to the nsplugins, but firefox will just hang, eventually KDE will catch it and ask to terminate it.

Needless to say, I'm still searching for a stable 64-bit browser that can handle some of the media that I encounter.  Until then, I'll just use the 32 bit version of firefox.

I would recommend the AMD64 version of Ubuntu or Kubuntu.  It is by far the most stable 64-bit version I have tested, and it seems that the ubuntu team has gone out of their way to support it.

---

### Post by daou on 2006-07-07
The xorg log says that it failed to load the nvidia kernel module.

---

### Post by daou on 2006-07-07
K7 works like a charm now. Reinstalled the NVIDIA drivers.

Is it safe to remove all the old kernels? According to Synaptic I have the following kernels on my system:

linux-image-2.6.15-23-386
linux-image-2.6.15-25-386
linux-image-2.6.15-25-k7
linux-image-386
linux-image-k7

---

### Post by hajk on 2006-07-07
Yes. Assuming that you're now running the k7 kernel, remove (purge) everything in your list ending in "386".

---

### Post by BIGtrouble77 on 2006-07-07
I have had very few issues with the 64bit default kernel in Dapper.  Can't say the same for breezy.  The key has been getting repo support so that common packages that already support 64bit are readily available.  I've had no issues with the AMD enhanced 32bit kernel either.

The key factor that makes 64bit doable now is automatix- makes things very easy to setup.  

There are many 32bit packages that will install and run perfectly fine with the 64bit kernel as long as you force the install.  I have opera(with flash), skype and cedega running this way.  You can also install the nvidia drivers with 32bit compatibility so that things like cedega will still work.  

I'm at the point now where everything on my system is working perfectly.  I could only achieve that with Gentoo before Dapper came out.

---

### Post by daou on 2006-07-07
Correction... K7 isn't working properly. Now I've lost sound ](*,). Is this a bug or do I need to download some sort of drivers?

Edit: I have a DFI Lanparty nF4 SLI-DR mobo, integrated sound (NVIDIA CK804)

---

### Post by wmcbrine on 2006-07-07
> **daou said:**
> I would rather not get into the 64-bit OS hell after playing with WinXP x64.You may have drawn the wrong inference from your experience. Linux has been 64-bit far longer than Windows has, and far more thoroughly. That's one of the beauties of open source -- you can build it for whatever hardware you've got a compiler for. Even now, the handful of things people complain about in 64-bit Linux -- Flash, Win32 codecs, etc. -- are all due to closed source that hasn't been ported. But the bulk of the OS is Free, and 64-bit, and works great.

I believe you can also run a 64-bit kernel with a 32-bit user space. Otherwise, if there's a 32-bit kernel with k8 optimizations (?), I'd take that over k7.

---

### Post by Zifnab on 2006-07-08
Don't know which specific kernel options are available for 32-bit x86, but if there's one called i686 that should be perfect, given the purported problems some people have with the K7-specific kernel (based only on the posts in this thread).

---

### Post by daou on 2006-07-09
> You may have drawn the wrong inference from your experience.

I might give the x64 kernel a shot on a new partition. At least Win x64 was more stable than its 32-bit cousin (especially under a +55% overclock ;) ). We'll see if Linux x64 proves this to a be a rule or an exception. I'm assuming of course that the x64 version of Ubuntu requires a new install instead of a simple kernel upgrade. Correct me if I'm wrong.

> I believe you can also run a 64-bit kernel with a 32-bit user space.

Does anyone have experience with this?

> Don't know which specific kernel options are available for 32-bit x86, but if there's one called i686 that should be perfect

Isn't i686 optimized for Intel chips? Doesn't that defeat the purpose of upgrading an i386 platform to i686 with AMD64?

---

