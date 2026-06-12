---
title: "YamiPod on AMD64"
date: 2005-10-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by bicchi on 2005-10-27
Not sure if anyone has heard of YamiPod, a program to manage the iPod under linux. The program seems to be wanting to use the 32 bit version of some of the libraries and I have an AMD64 machine.  
Here is the error message: 
./YamiPod: error while loading shared libraries: libcups.so.2: cannot open shared object file: No such file or directory

I do have CUPS installed and those libraries are in my: /usr/lib directory. Has anyone with an iPod and offcourse an AMD64 machine given this program a try. On YamiPod's website they claim that the program works with Ubuntu 5.04 and 5.10 but it must be for the 32 bit release.
YamiPod also seems to be part of the Future Ubuntu [Universe Candidates]("https://wiki.ubuntu.com/UniverseCandidates").

Here is a link to [YamiPod]("http://www.yamipod.com/main/modules/home/").

---

### Post by gpw797 on 2005-10-27
> On YamiPod's website they claim that the program works with Ubuntu 5.04 and 5.10 but it must be for the 32 bit release.

Works on 32 bit version 5.10 here, but it is slow (I have fast machine). I do music management in amarok then sync in yamipod

---

### Post by RSX311 on 2005-10-29
yeah, I have the same error msg when I run yamipod on m y AMD64 machine.  Maybe it's not compiled for our platform yet?

---

### Post by bicchi on 2005-10-30
[QUOTE=RSX311]yeah, I have the same error msg when I run yamipod on m y AMD64 machine.  Maybe it's not compiled for our platform yet?[/QUOTE]

I have [filed a bug]("http://www.yamipod.com/main/modules/newbb/viewtopic.php?topic_id=200&forum=3") on Yamipod's forum website. I have also contacted the main programmer for Yamipod and he tells me that the program is been created with REALbasic and from what I can tell [here]("http://ubuntuforums.org/showthread.php?t=71952") there are problems with REALbasic and AMD64. There also seems to be a solution for REALbasic to work on AMD64 from the [Gentoo forums]("http://forums.gentoo.org/viewtopic-t-379650-highlight-gentoolkitdev.html?sid=2714ff1142ee9e14808e17b422082256").

Perhaps we need to install and reference the 32 bit libraries of CUPS and any other dependencies that Yamipod might need.

---

### Post by bicchi on 2006-06-05
This is what I ended up doing in order to get it to run on Dapper AMD64. I downloaded the i386 package (32 bit version) of  [libcupsys2]("http://packages.ubuntu.com/dapper/libs/libcupsys2") and extracted the .deb file. I didn't installed the package I just copied the file needed in this case libcups.so.2 to the directory /usr/lib32/

The program is painfully slow while reading all the songs in my iPod but seems to work ok once its done.

---

