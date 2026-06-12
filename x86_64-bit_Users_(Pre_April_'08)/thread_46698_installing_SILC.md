---
title: "installing SILC"
date: 2005-07-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by dnk777 on 2005-07-05
Hi,
i've got ubuntu 64 and I tried to install SILC client on ubuntu64 and i got error because it's not i386 architecture but amd64...so i tried --force-architecture switch but it doesn't help....i'm a total beginner and i have no idea what's the problem. can anybody help me please? do i need to compile it myself for 64 bit from the sources? (how?) or... ? (i hope it's something simple...i've heard that ubuntu is Linux for Human Beings)

# dpkg -i silc-client_1.0.1-1_i386.deb dpkg: error processing silc-client_1.0.1-1_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 silc-client_1.0.1-1_i386.deb

# dpkg --install --force-architecture s ilc-client_1.0.1-1_i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package silc-client.
(Reading database ... 58054 files and directories currently installed.)
Unpacking silc-client (from silc-client_1.0.1-1_i386.deb) ...
dpkg: dependency problems prevent configuration of silc-client:
 silc-client depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
dpkg: error processing silc-client (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 silc-client

# silc
silc: error while loading shared libraries: libperl.so.5.8: cannot open shared o bject file: No such file or directory

---

### Post by FluffyElmo on 2005-07-05
libsilc and silky (a gtk+ gui for silc) are both available in the amd64 Universe repository. Uncomment the entry for the Universe repository in /etc/apt/sources.list then try apt-get update then apt-get install silky.

Or you can just use Synaptic to enable Universe and install them...

Hope this helps!

---

### Post by dnk777 on 2005-07-07
nah, i'd like / i'm trying to instal the classical SILC client (for shell...the one from SILC web - silcnet.org)...

((no silky no GUI...i'd puke))

---

