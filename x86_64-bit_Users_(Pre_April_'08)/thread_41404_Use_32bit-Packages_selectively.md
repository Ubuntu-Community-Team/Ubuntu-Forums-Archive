---
title: "Use 32bit-Packages selectively"
date: 2005-06-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Cornered_Rat on 2005-06-13
Hello NG,

I'm currently thinking about switching to Ubuntu (from Gentoo) - I liked Gentoo very much and still do, but I have to get some serious work done and therefor need a system that has a *stable tree*, *security updates* on normal days and *predictable update cycles* (=> Ubuntu).

My question is: Is there a possibility to use amd64-Ubuntu, but tell apt to use x86-repositories for selected packages? These would include:

- firefox
- flash
- java
- opera
- mplayer / xine
- realplayer
- w32codecs
- wine (?)

I found a lot of information on, say, w32codecs'ing Ubuntu, but all information applied to x86 only.

Greetings,

Dirk

---

### Post by wiraone on 2005-06-13
This is where you need the chroot 32bit environment..  Here is the link on how to setup chroot.

[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

I'm half way of getting my 32bit environment to work. Up till now, I've got firefox32 with flash to work just fine .. I need to get openoffice to work in 32bit since I couldn't setup printer with the OO which came with the stock Ubuntu64.

---

### Post by Cornered_Rat on 2005-06-14
wiraone, Thank You for Your reply, but that's exactly what I **don't** want. I know I can run many 32bit-compiled binaries if I install emul-libs. That way I can have a 32bit Firefox running on my 64bit-machine without chroot. 

I would like to know whether there is a way to tell apt (or synaptic or something) to use a 32bit-compiled package-repository for a selected bunch of programs.

Like this:

/etc/exceptionlist:
###########
mozilla-firefox
java
mplayer
xine

/etc/apt.config:
##########
if [apt-get "package"] and ["package" is element of "exceptionlist"] then
use [ftp://somehost/](ftp://somehost/)**32bit-ubuntu**/main
else
use [ftp://somehost/](ftp://somehost/)**64bit-ubuntu**/main

I don't want to mess with chroots, I basically want the system to "just work (tm)" as advertised on ubuntus homepage. The exceptionlist would be a viable solution, I think. If there's an apt-guru out there - could You shed a little light on this?

Greetings,

Dirk

---

### Post by wiraone on 2005-06-14
Do let me know if you could get this to work .. I love to do the same thing too :) It is surely a hassle to setup chroot environment .. but since I'm half way thru .. I guess I need to live with it..

---

### Post by Cornered_Rat on 2005-06-14
Hm, it looks like it could be achieved with *pinning*. 

If You have a /etc/sources.list

deb *server/**amd64path*** main
deb *server/**x86**path* main

apt would by default use the packages from amd64. But if You put into the file */etc/apt/preferences* the following:

Package: mozilla-firefox
Pin: server/amd64path
Pin-Priority: 600

apt would reverse the priorities for this package only.

Could somebody confirm?

Greetings, 

Dirk

---

### Post by kLy on 2005-07-25
Would this actually be possible thought? Paths to repositories have the form:

[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

don't they? They don't include the architecture, just the path to the repository. In this case the architecture is autodetected and not something that you can specify, right?

It seems to really annoy me that every distro that supports amd64, sees it like a separate architecture, like SPARC or PPC that they HAVE to compile packages specifically for since it's not compatible with x86. But any AMD64 machine with the right emul settings in the kernel should be able to work seemlessly with i386 code as well, right? So why not have the amd64 distros come with a decent set of 32bit library files and then anything that isn't available in 64bit code (like wine or flash) will automatically resort to the 32bit version, since it WILL work with amd64? And allow amd64 users to choose which version of a package they want (for instance wanting a 32bit firefox for compatibility with 32bit flash) since it can natively use 32 or 64bit code?

As it stands amd64 users have to resort to a 32bit chroot or manually getting 32bit .deb files and doing a dpkg --force.

It would make the inevitable migration to 64bit much easier. Even 64bit Windoze is willing to support 32bit code out of the box. Linux easily can, but from what I have seen the distros just don't want to. Or am I not getting the right picture here?

kLy

---

### Post by Pse on 2005-07-25
We still have to wait for multiarch to get rid of these problems.
I run without a chroot environment set up, but I've had to manually install every 32-bit package I needed. Mplayer (for Win32 codecs), Opera (for Flash), OO.org 2 are running fine here, but I had to search every freakin' dependency that wasn't satisfied by the standard ia32-libs (BTW, ia32-libs 1.4 includes many improvements). Plus, I had to modify some scripts to point each program to the right library path. It's not hard if you know how to handle yourself with libs and scripts, but it could be somewhat difficult for someone new... Right now, the easiest way is setting up a chroot...

---

### Post by H3g3m0n on 2005-07-31
I too was thinking about switching from Gentoo to Ubuntu and ran into the same problem.

On gentoo you can emerge a firefox-bin package with a 32bit precompiled firefox, there is also a unofficial ebuild around for a 32bit mplayer and special set of w32codecs and an emu32-mplayer package. In the end I think its just a limitation of the Ubuntu system, its designed more of ease of use rather that for experinced linux users. Since gentoo does every thing from the source if there a problem or something that needs tweaking you can edit the source from scratch if need be, if a package is out of date often all that you need to do is rename the ebuild file and it will grab and compile the latest version. Unfortunatly compiling from source has its own problems, waiting for the compile to be finshed (openoffice took me 16 hours) and heaps of problems with compile errors although i think it encourages people to fix the buggy code and submit patches.

I might look at manually installing the mplayer32 packages and compiling a 32bit firefox, if i get lucky i might beable to figure out how to make .deb files.

EDIT: Just had a thought, might be worth installing Gentoo's Portage system onto Ubuntu, its fairly portable, seems it runs on OSX and theres even a dodgy unusable one for windows (cygwin) =P [http://forums.gentoo.org/viewtopic-t-125553.html](http://forums.gentoo.org/viewtopic-t-125553.html)

EDIT2: This thread shows how to force 32bit packages to be installed [http://www.ubuntuforums.org/showthread.php?t=50895](http://www.ubuntuforums.org/showthread.php?t=50895)

---

### Post by bukagedi on 2005-08-01
There is no need to look for 32bit version of firefox and java - native AMD64 are working fine.
wine - 32 bit version will fail, because it is related to kernel. I tried to compile it from sources, but got nothing.

---

### Post by tseliot on 2005-08-04
[QUOTE=Cornered_Rat]
...
I found a lot of information on, say, w32codecs'ing Ubuntu, but all information applied to x86 only.

Greetings,

Dirk[/QUOTE]

If you want to use win32 codecs (for audio and video files) in Ubuntu 64bit you can use my HOWTO (it's easy).
It's here:

[http://ubuntuforums.org/showthread.php?t=54399](http://ubuntuforums.org/showthread.php?t=54399)

---

