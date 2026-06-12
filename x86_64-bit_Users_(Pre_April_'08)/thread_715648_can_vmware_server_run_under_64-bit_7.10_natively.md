---
title: "can vmware server run under 64-bit 7.10 natively?"
date: 2008-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by citybird on 2008-03-05
I have been checking the forums and the web and found this info on VMwares website:

```
VMware Server 1.0 includes:

Support for 32-bit and 64-bit Operating Systems

    * Full support for 32-bit and 64-bit FreeBSD 6.0 as guest operating systems.
    * Experimental support for Red Hat Enterprise Linux 3.0 Update 8 and Red Hat Enterprise Linux 4.0 Update 4.
    * Experimental support for 64-bit Ubuntu 6.x as host and guest operating systems.
``` 

Has anyone found a way to get VMware Server to run under 64-bit Gutsy native?
Has anyone tried the new VMware 2.0 Beta under 64-bit Gutsy native?

Thanks.

---

### Post by wiresquire on 2008-03-05
If I get you right, you mean running vmware server as a host on Ubuntu AMD64 ?

If so, yes you can. I run Vista 32bit as a guest on Ubuntu AMD64 Vmware Server 1.0x. Only when I have to ;-)

There's a good guide [here]("http://www.ubuntugeek.com/how-to-install-vmware-server-in-ubuntu-710-gutsy-gibbon.html"). And you may need to add the ia32-libs as mentioned [here]("http://www.jameslittle.me.uk/installing-vmware-on-ubuntu-gutsy/").

I haven't tried 2.0x as I believe it's still in beta. There is a lot of talk in the vmware forums about the new console etc.

One thing to note. There's no 3D acceleration support in VMWare server, so if you are thinking of running games, or even eye candy for the desktop, you are better off looking at VMWare Player (or workstation, but that's a license fee!)

---

### Post by citybird on 2008-03-05
Right I am about to install AMD64 on my machine but I was wondering if there was a 64 bit version of the server that didn't need the 32bit libs to run.

As for games This will be for running many copies of Diablo 2: LOD which doesn't need 3D support.

Currently VMware bogs down at 3 guest os's on my machine because I run out of ram on the 32bit version. I maxed out my motherboard at 8gigs of ram but the 32bit version only uses 2-3 gigs.

---

### Post by Kilz on 2008-03-05
> **citybird said:**
> Right I am about to install AMD64 on my machine but I was wondering if there was a 64 bit version of the server that didn't need the 32bit libs to run.

As for games This will be for running many copies of Diablo 2: LOD which doesn't need 3D support.

Currently VMware bogs down at 3 guest os's on my machine because I run out of ram on the 32bit version. I maxed out my motherboard at 8gigs of ram but the 32bit version only uses 2-3 gigs.

Just a question from a D2 addict. Why would you need 3 or more instances running at once?

---

### Post by dgetsman on 2008-04-03
[FONT="Verdana"]I just attempted to get a vmware server running on the 64-bit AMD ubuntu 7.10 distribution on a machine that I just built for serving vmware machines at my organization.  Documentation for the problem I ran into doesn't seem to have hit high enough google ratings to be easily found yet.  Anyway I ran into the problem where the following appears while running the vmware server installation script:

[FONT="Fixedsys"]The correct version of one or more libraries needed to run VMware Server may be missing. This is the output of ldd /usr/bin/vmware:[/FONT]
linux-gate.so.1 => (0xffffe000)
libm.so.6 => /lib32/libm.so.6 (0xf7f93000)
libdl.so.2 => /lib32/libdl.so.2 (0xf7f8f000)
libpthread.so.0 => /lib32/libpthread.so.0 (0xf7f76000)
libX11.so.6 => not found
libXtst.so.6 => not found
libXext.so.6 => not found
libXt.so.6 => not found
libICE.so.6 => not found
libSM.so.6 => not found
libXrender.so.1 => not found
libz.so.1 => /usr/lib32/libz.so.1 (0xf7f60000)
libc.so.6 => /lib32/libc.so.6 (0xf7e16000)
/lib/ld-linux.so.2 (0xf7fc6000)[/FONT]

[FONT="Verdana"]It confounded me for quite a bit due to the fact that the above libraries were indeed installed.  Part of my problem was probably also the fact that this is my first time using a 64-bit linux installation, I wasn't even aware that separate libraries were needed.

Anyway, as can be found [here]("http://www.jameslittle.me.uk/installing-vmware-on-ubuntu-gutsy/"), simply installing the ia32-libs package with the following:[/FONT]
[FONT="Fixedsys"]sudo apt-get install ia32-libs[/FONT] should fix this.

Hope this helps anybody that was running their head into the same brick wall as myself.

---

### Post by TpyKv on 2008-04-03
Thanks dgetsman!!

---

