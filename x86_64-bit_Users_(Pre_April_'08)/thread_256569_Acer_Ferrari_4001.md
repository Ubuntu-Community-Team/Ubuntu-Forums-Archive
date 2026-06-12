---
title: "Acer Ferrari 4001"
date: 2006-09-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by MissAR on 2006-09-13
G'day everyone!

While this is my *VERY* first post, I'm not entirely green to this, I have some wonderful help from a good friend, who happens to be the IT manager at my workplace. 

SO, about me and my system, then onto my question. I am a longtime Windows hater, but i found it a bit intimidating to reconfig my own pc by myself to an OS i had no idea how to use. Now i have two computers, my desktop (the family computer) and my 'Rari, my own personal beast. As yet my desktop remains soley a Windows machine, and my Ferrari is entirely stock, save that it runs Kubuntu.

And, now, FINALLY (:-D ) on to my question. I have lost access to Tibs (IT mgr) for the day, gosh forbid he actually has to work, and it happens to be on my day off!! So i want to install my WLAN and have it working on Kubuntu. I read through one older post, about someone else's Acer Travelmate ([http://www.ubuntuforums.org/showthread.php?t=110749]("http://www.ubuntuforums.org/showthread.php?t=110749")), and i tried what redsmoke put in for code 
 
> redsmoke@ubuntu:~$ uname -r

i got 
> alex@TheRari:~$ uname -r
2.6.15-26-386


so i tried to do the sudo command he posted as the next step and got this

> alex@TheRari:~$ sudo apt-get install linux-headers-2.6.15-26-386
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.15-26
The following NEW packages will be installed:
  linux-headers-2.6.15-26 linux-headers-2.6.15-26-386
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 7759kB of archives.
After unpacking, 79.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-headers-2.6.15-26 2.6.15-26.46 [6903kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main linux-headers-2.6.15-26-386 2.6.15-26.46 [856kB]
Fetched 7759kB in 1m5s (118kB/s)
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 2 during global destruction.
Selecting previously deselected package linux-headers-2.6.15-26.
(Reading database ... 73341 files and directories currently installed.)
Unpacking linux-headers-2.6.15-26 (from .../linux-headers-2.6.15-26_2.6.15-26.46_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.15-26-386.
Unpacking linux-headers-2.6.15-26-386 (from .../linux-headers-2.6.15-26-386_2.6.15-26.46_i386.deb) ...
Setting up linux-headers-2.6.15-26 (2.6.15-26.46) ...

Setting up linux-headers-2.6.15-26-386 (2.6.15-26.46) ...


then, upon seeing that it had done something, followed his instructions two steps further and got:

> alex@TheRari:~$ wget [http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.7.tar.gz](http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.7.tar.gz)
--08:57:17--  [http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.7.tar.gz](http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.7.tar.gz)
           => `ndiswrapper-1.7.tar.gz'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 175,061 (171K) [application/x-tar]

100%[====================================>] 175,061      108.19K/s

08:57:20 (107.96 KB/s) - `ndiswrapper-1.7.tar.gz' saved [175061/175061]

alex@TheRari:~$ tar xvzf ndiswrapper-1.7.tar.gz
ndiswrapper-1.7/
ndiswrapper-1.7/AUTHORS
ndiswrapper-1.7/ChangeLog
ndiswrapper-1.7/INSTALL
ndiswrapper-1.7/Makefile
ndiswrapper-1.7/README
ndiswrapper-1.7/ndiswrapper.spec
ndiswrapper-1.7/version
ndiswrapper-1.7/ndiswrapper.8
ndiswrapper-1.7/utils/
ndiswrapper-1.7/utils/Makefile
ndiswrapper-1.7/utils/ndiswrapper
ndiswrapper-1.7/utils/loadndisdriver.c
ndiswrapper-1.7/utils/ndiswrapper-buginfo
ndiswrapper-1.7/driver/
ndiswrapper-1.7/driver/divdi3.c
ndiswrapper-1.7/driver/hal.c
ndiswrapper-1.7/driver/iw_ndis.c
ndiswrapper-1.7/driver/iw_ndis.h
ndiswrapper-1.7/driver/loader.c
ndiswrapper-1.7/driver/loader.h
ndiswrapper-1.7/driver/longlong.h
ndiswrapper-1.7/driver/Makefile
ndiswrapper-1.7/driver/misc_funcs.c
ndiswrapper-1.7/driver/ndis.c
ndiswrapper-1.7/driver/ndis.h
ndiswrapper-1.7/driver/ndiswrapper.h
ndiswrapper-1.7/driver/ntoskernel.c
ndiswrapper-1.7/driver/ntoskernel.h
ndiswrapper-1.7/driver/ntoskernel_io.c
ndiswrapper-1.7/driver/pe_linker.c
ndiswrapper-1.7/driver/pe_linker.h
ndiswrapper-1.7/driver/pnp.c
ndiswrapper-1.7/driver/pnp.h
ndiswrapper-1.7/driver/proc.c
ndiswrapper-1.7/driver/usb.c
ndiswrapper-1.7/driver/usb.h
ndiswrapper-1.7/driver/winnt_types.h
ndiswrapper-1.7/driver/wrapper.c
ndiswrapper-1.7/driver/wrapndis.h
ndiswrapper-1.7/driver/wrapndis.c
ndiswrapper-1.7/driver/x86_64_stubs.S
ndiswrapper-1.7/debian/
ndiswrapper-1.7/debian/Makefile
ndiswrapper-1.7/debian/changelog.modules
ndiswrapper-1.7/debian/changelog.source
ndiswrapper-1.7/debian/changelog.utils
ndiswrapper-1.7/debian/control.modules
ndiswrapper-1.7/debian/control.source
ndiswrapper-1.7/debian/control.utils
ndiswrapper-1.7/debian/copyright
ndiswrapper-1.7/debian/dirs.utils
ndiswrapper-1.7/debian/docs
ndiswrapper-1.7/debian/postinst.modules
ndiswrapper-1.7/debian/README.Debian
ndiswrapper-1.7/debian/rules
alex@TheRari:~$                                       

i was thinking, WOW! this is actually working, and continued to follow his instructions

> alex@TheRari:~$ wget [ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip)
--08:59:48--  [ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip)
           => `80211g.zip'
Resolving ftp.support.acer-euro.com... 193.194.129.152
Connecting to ftp.support.acer-euro.com|193.194.129.152|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /notebook/ferrari_4000/driver/winxp64bit ... done.
==> PASV ... done.    ==> RETR 80211g.zip ... done.
Length: 932,277 (910K) (unauthoritative)

100%[====================================>] 932,277      116.96K/s    ETA 00:00

08:59:58 (113.81 KB/s) - `80211g.zip' saved [932277]

alex@TheRari:~$ unzip 80211g.zip
Archive:  80211g.zip
  inflating: WL_T60H906(8.0.10.0,XP64_logo)/bcm43xx.cat
  inflating: WL_T60H906(8.0.10.0,XP64_logo)/bcmwl5.inf
  inflating: WL_T60H906(8.0.10.0,XP64_logo)/BCMWL564.SYS
  inflating: WL_T60H906(8.0.10.0,XP64_logo)/Setup.exe
alex@TheRari:~$       

tried the next two steps:

> alex@TheRari:~$ sudo apt-get install checkinstall
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  installwatch
The following NEW packages will be installed:
  checkinstall installwatch
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 46.1kB of archives.
After unpacking, 225kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe installwatch 0.6.3-2ubuntu1 [11.0kB]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe checkinstall 1.5.3-3ubuntu2 [35.1kB]
Fetched 46.1kB in 0s (62.7kB/s)
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 2 during global destruction.
Selecting previously deselected package installwatch.
(Reading database ... 88588 files and directories currently installed.)
Unpacking installwatch (from .../installwatch_0.6.3-2ubuntu1_i386.deb) ...
Selecting previously deselected package checkinstall.
Unpacking checkinstall (from .../checkinstall_1.5.3-3ubuntu2_all.deb) ...
Setting up installwatch (0.6.3-2ubuntu1) ...
Setting up checkinstall (1.5.3-3ubuntu2) ...
alex@TheRari:~$                           

and got 

> Selecting previously deselected package ndiswrapper-1.7.
(Reading database ... 88607 files and directories currently installed.)
Unpacking ndiswrapper-1.7 (from .../ndiswrapper-1.7_1.7-1_i386.deb) ...
dpkg: error processing /home/alex/ndiswrapper-1.7/ndiswrapper-1.7_1.7-1_i386.deb
 (--install):
 trying to overwrite `/lib/modules/2.6.15-26-386/modules.alias', which is also i
n package linux-image-2.6.15-26-386
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/alex/ndiswrapper-1.7/ndiswrapper-1.7_1.7-1_i386.deb
/var/tmp/YHVnUTRXEOJoPplgHVii/dpkginstall.log (END)              

SO here is where all you wonderful people come in. I have no idea what to do from here. Anyone able to help? Feel free to add me to your IM service, [email]daniquer@hotmail.com[/email] (msn msgr).

Terribly sorry if this looks terrible, or is alot of junk you dont need, but i figured that i would be safer putting it all in that trying to choose what was important!

~A

---

### Post by MissAR on 2006-09-13
ok, i am an idiot. I installed the 32 bit ver of Kubuntu...

*sigh
~A

---

