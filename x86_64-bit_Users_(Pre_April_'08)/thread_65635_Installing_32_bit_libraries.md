---
title: "Installing 32 bit libraries"
date: 2005-09-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by redjar on 2005-09-14
I've seen various references in this forum and elsewhere of /lib32 and /lib64 directories coexisting on the same AMD63 Ubuntu box, but haven't seen any documentation or mention of explicitly installing 32 bit libraries along side 64 bit libraries.  Is this possible?  If so, how is this done?

I need to run Real Producer on a AMD64 Ubuntu box.  As far as I can tell, no 64 bit version has been created.  I have it running in a chroot'ed environment but it seems like there should be a more elegant solution.

Thanks.

---

### Post by mlomker on 2005-09-14
From what I've read, chroot is how it is done.  Hopefully we'll have native versions at some point.

---

### Post by redjar on 2005-09-15
I finally found the answer I was looking for.

[This Debian page notes](http://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html#id271960):
[INDENT]There is already a minimal set of IA32 libraries packaged for use in a 64bit Debian system. Simply do an 'apt-get install ia32-libs' and you will be able to run most 32bit binaries within your system.[/INDENT]

I installed the **ia32-libs** package and without any other configuration Real Producer appears to run fine.  This may not be the case with other 32-bit apps that depend on more libraries.

I tested this on both Hoary and Breezy AMD64.

(note: at the end of the install, it complains: "grep: /etc/ld.so.conf: No such file or directory")

---

### Post by Ceriel Nosforit on 2005-09-16
[QUOTE=redjar]I finally found the answer I was looking for.

[This Debian page notes](http://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html#id271960):
[INDENT]There is already a minimal set of IA32 libraries packaged for use in a 64bit Debian system. Simply do an 'apt-get install ia32-libs' and you will be able to run most 32bit binaries within your system.[/INDENT]

I installed the **ia32-libs** package and without any other configuration Real Producer appears to run fine.  This may not be the case with other 32-bit apps that depend on more libraries.

I tested this on both Hoary and Breezy AMD64.

(note: at the end of the install, it complains: "grep: /etc/ld.so.conf: No such file or directory")[/QUOTE]
 Nice. Thank you, rejdar for linking that. I installed it and got a total of zero errors or warnings. 

The thing I'm wondering about now is,  is safe to --force dpkg to install a 32 bit .deb?

---

### Post by mlomker on 2005-09-16
[QUOTE=redjar]I installed the **ia32-libs** package and without any other configuration Real Producer appears to run fine.  This may not be the case with other 32-bit apps that depend on more libraries.
[/QUOTE]

Ah.  I just installed that the other day to use mplayer32.  I guess it adds support for more than I realized.

Just tried RealPlayer and no dice.

---

### Post by prospectofdeath on 2005-09-18
Has anyone seen this yet?

```
sudo apt-get install ia32-libs
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  ia32-libs
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8816kB of archives.
After unpacking 1253kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 72932 files and directories currently installed.)
Preparing to replace ia32-libs 1.4ubuntu1 (using .../ia32-libs_1.4ubuntu2_amd64.deb) ...
Unpacking replacement ia32-libs ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_1.4ubuntu2_amd64.deb (--unpack):
 unable to create `./usr/lib32/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_1.4ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` 

So far Breezy on amd64 w/ati hasn't been as much fun as I thought it would be.

---

### Post by mlomker on 2005-09-18
Was that from following my [ATI how-to?](http://www.ubuntuforums.org/showthread.php?p=348911)

I noted that they'll be some *fun* with that at the end of the how-to.  Follow the instructions for backing up the file.  After that you can just **apt-get install --force-yes whateverpackage** and then copy the replaced file back over again after the installation completes.

The bad news is that I've heard from a couple people that can't get the Breezy driver to work, either.  This might be a routine that at least some ATI users have to live with for a while.

---

### Post by rplantz on 2005-09-18
[QUOTE=redjar]I finally found the answer I was looking for.

[This Debian page notes](http://alioth.debian.org/docman/view.php/30192/21/debian-amd64-howto.html#id271960):
[INDENT]There is already a minimal set of IA32 libraries packaged for use in a 64bit Debian system. Simply do an 'apt-get install ia32-libs' and you will be able to run most 32bit binaries within your system.[/INDENT]

I installed the **ia32-libs** package and without any other configuration Real Producer appears to run fine.  This may not be the case with other 32-bit apps that depend on more libraries.

[/QUOTE]

I did the library install with Synaptic.

I have a bunch of assembly language programs written for IA32 (for a textbook I've written). I use the --32 option for the assembler (gas) and -m32 option for the loader/linker. (I simply pass the .o files to gcc and it goes directly to ld, automatically linking the required libraries.)

The programs run just fine, with no chroot required.

I'm guessing the differences (chroot or no) have to do with static vs. dynamic linking. Need to dig out my Levine book (Linkers & Loaders) and see if I can figure this out.

Bob

---

### Post by prospectofdeath on 2005-09-20
[QUOTE=mlomker]Was that from following my [ATI how-to?](http://www.ubuntuforums.org/showthread.php?p=348911)[/QUOTE]

Yeah, it was just after following your ATI suggestion.

I ended up re[apt-get]ting the fglrx and restricted modules and ran fglrxconfig and my ATI card started working perfectly.

Ultimately I gave up on the amd64 version of Breezy because I wanted a Flash plug-in for Firefox. When they release a 64-bit version of Flash I'll upgrade.

---

### Post by mlomker on 2005-09-20
> Ultimately I gave up on the amd64 version of Breezy because I wanted a Flash plug-in for Firefox. When they release a 64-bit version of Flash I'll upgrade.

Yes, you should definitely use the included drivers if they work.

---

