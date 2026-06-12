---
title: "Installing 32-bit third party apps on 64-bit Ubuntu"
date: 2007-04-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by jsym on 2007-04-27
After making a clean 64-bit 7.04 install, I ran into a number of problems running a 32-bit program that ran without difficulties on previous versions and I didn't recall having to do anything special to make that happen.  It's sorted out now and I thought that I would make this post since I couldn't seem to find one that specifically addressed the issues I was having, but rather many that almost did.  It is my hope that I can save someone, sometime a long night of hair pulling.

The program I was having trouble with was S-Plus 7, but I imagine that anyone who might need to install a 32-bit piece of software not available from the repositories might have the same difficulty.

[SIZE="3"]The short version:[/SIZE]

The basic install (at least from the alternate install CD) didn't include the necessary 32-bit libraries.  Install **ia32-libs** and **lsb-core** (and all their dependencies) via either synaptic or apt-get and everything will be fine.

[SIZE="3"]The long version:[/SIZE]

1.  If you try to run an executable from the terminal and see a message like:
```
bash: ./[NAME OF FILE YOU TRIED TO RUN]: no such file or directory found
```
and you are in the right directory and the file is there then you likely have your 64-bit system looking *only* for 64-bit executables.  The solution?  Install **lsb-core** (The Linux Standard Base, which is a library that third party vendors can rely on to be stable and consistent across time when developing their applications).  Once installed your machine will recognize the 32-bit executables.

2.  If you try to run an executable from the terminal and see a message like: 
```
[Some directory structure] error while loading shared libraries:[NAME OF SOME LIBRARY]: cannot open shared object file: No such file or directory
```
and you can see that the missing file (in my case it was libstdc++.so.5 or libX11.so.6) *does* exist on your system then you likely have your 32-bit program (in my case S-Plus) looking for a 32-bit library that doesn't exist on your 64-bit system.  Install **ia32-libs** (runtime libraries for the ia32/i386 architecture, configured for use on an amd64 or ia64 Debian system running a 64-bit kernel).  Once installed your program will have the right libraries to make it happy.

3.  I also found out that the ***file*** command can be quite helpful in such situations as it provides information that is not available by simply choosing ***properties*** from the desktop file browser; specifically, whether it is a 32-bit or a 64-bit file.  For example:
```
$ file HOSTINFO 
HOSTINFO: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), stripped

$ file /usr/lib/libstdc++.so.5
/usr/lib/libstdc++.so.5: symbolic link to `libstdc++.so.5.0.7'

$ file /usr/lib/libstdc++.so.5.0.7 
/usr/lib/libstdc++.so.5.0.7: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), stripped
```

**NOTE:** There are other 32-bit libraries that you might require for your specific application as well (i.e. ia32-sun-java6-bin.  Do a search in synaptic for "ia32" to find them all.

---

### Post by rufius on 2007-04-27
Why use the 64 bit release anyway? 64 Bit has more problems with third party than 32 bit, it uses more memory, and there's no noticeable performance gain unless you're doing high-level floating point math. But if you're doing high-level floating point math, why aren't you doing it on a POWER chip, Opteron, Xeon, or a UltraSPARC T1? I'd say save yourself the trouble and install 32 bit. Most users will never need more than that.

---

### Post by Kilz on 2007-04-27
Hi, 
I have a question about the lsb-core. As I understand it, its the linux standard base package. I just took a look at the package and it seems to install to /usr/lib, which is a location for 64bit libraries. How dose it help running 32bit applications?

> **rufius said:**
> Why use the 64 bit release anyway? 64 Bit has more problems with third party than 32 bit, it uses more memory, and there's no noticeable performance gain unless you're doing high-level floating point math. But if you're doing high-level floating point math, why aren't you doing it on a POWER chip, Opteron, Xeon, or a UltraSPARC T1? I'd say save yourself the trouble and install 32 bit. Most users will never need more than that.

Because some of us would prefer to run a 64bit operating system on our 64bit hardware. There is a general performance improvement. There is also a large speed improvement if you are doing 3d rendering, encoding/ripping and editing video. 
The 64bit version has a few, very few problems with third party applications, for the most part the common problems have been worked around long ago. To the point that a lot of us that run the 64bit version know the line about application problems to be a lot of FUD. This topic seems to be talking about how to improve the ability of the few, very few 32bit applications that are needed, and can pretty easily be installed. So that you have the best of both worlds. A 64bit operating system and performance where you can, and still have a few 32bit proprietary application where they are not avilable as 64bit versions.
As for the last comment. I remember some people saying the same thing about 16 bit, and why do you need to move to 32bit computers. I have a feeling someone will say the same thing when 128bit computing finally arrives.

---

### Post by jsym on 2007-04-27
> **rufius said:**
> Why use the 64 bit release anyway? ... I'd say save yourself the trouble and install 32 bit. Most users will never need more than that.

Why do I use 64-bit?
1. I am doing high-level floating point math.
2. I don't have a POWER chip, Opteron, Xeon, or a UltraSPARC T1.
3. I can.

;-)

---

### Post by jsym on 2007-04-27
> **Kilz said:**
> Hi, 
I have a question about the lsb-core. As I understand it, its the linux standard base package. I just took a look at the package and it seems to install to /usr/lib, which is a location for 64bit libraries. How does it help running 32bit applications? 

All I know is what it says in the readme file (/usr/share/doc/lsb-core/README.Debian.gz).  I believe that the relevant bits are the following:
> This package provides the Linux Standard Base on Debian systems.  The
LSB is a specification for allowing the same binary package to be used
on multiple distributions.

[Bunch of stuff about installing and package layout]

This package implements the LSB specification by:

- depending upon packages that implement OS services required by the
  LSB, including libraries and programs.

- including the correct symlink to the dynamic linker.

- providing the LSB init script functionality.  Some of the LSB init
  functionality cannot be implemented without cooperation from other
  packages or changes in policy for sarge+1; however, the remainder is
  provided here.

The intent of this package is to provide a best current practice way
of installing LSB packages on Debian using the Intel and PowerPC
32-bit architectures with the Linux kernel ("ia32" and "ppc32").  Its
presence does not imply that I or the Debian project believe that
Debian fully complies with the Linux Standard Base, and should not be
construed as a statement that Debian is LSB-compliant.

The specification is available at [http://www.linuxbase.org/spec/](http://www.linuxbase.org/spec/)

[Bunch of stuff about deviations from design decisions and compliance testing]

---

### Post by Tanker Bob on 2007-04-27
> **jsym said:**
> Why do I use 64-bit?
1. I am doing high-level floating point math.
2. I don't have a POWER chip, Opteron, Xeon, or a UltraSPARC T1.
3. I can.

;-)
Sign me up for #3.  :)

I'm with Kilz on this one.  I have a screaming 64-bit PC, I should have a 64-bit OS to go with it.  The ONLY issue I have on Feisty now is with my scanner, and this thread may solve that problem for me--I'll let you know tonight.  Thanks, jsym, for pointing the way.

---

### Post by Tanker Bob on 2007-04-27
> **Tanker Bob said:**
> Sign me up for #3.  :)

I'm with Kilz on this one.  I have a screaming 64-bit PC, I should have a 64-bit OS to go with it.  The ONLY issue I have on Feisty now is with my scanner, and this thread may solve that problem for me--I'll let you know tonight.  Thanks, jsym, for pointing the way.

Nope, didn't work.  Scanner still an issue, but that was true in 32-bit Edgy.

---

### Post by rufius on 2007-04-29
> **jsym said:**
> Why do I use 64-bit?
1. I am doing high-level floating point math.
2. I don't have a POWER chip, Opteron, Xeon, or a UltraSPARC T1.
3. I can.

;-)

Good point then :). I ask the question only because I've found that most users never need to use it. Since you do, 'tis justified :).

---

