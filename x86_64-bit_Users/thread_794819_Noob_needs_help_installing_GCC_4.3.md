---
title: "Noob needs help installing GCC 4.3"
date: 2008-05-15
forum: x86 64-bit Users
---

### Post by MrDoomMaster on 2008-05-15
Hi,

I have been a windows user for YEARS, and it hasn't been until now that I've finally decided to try out Ubuntu. Let me tell you, this is completely different. I have a hard time figuring out how to do things.

My first goal was to get ndiswrapper installed, since I read online that it can potentially get my D-Link DWA-556 wireless NIC working. So, in the process of compiling ndiswrapper, I find that it fails to compile because various STL library headers cannot be found. So, I go to the GCC website and find that libstdc++ is now part of the GCC package, so I just download the whole GCC 4.3 and try to compile it. However, GCC too has too many dependencies and has very confusing configuration options. I would like so much just to be able to tell it to build and everything happen automatically. I noticed that a couple of C library files could not be found when running 'configure' on GCC, so I looked into getting glibc installed. However, again, building glibc fails too! I just don't know what is going on. glibc says it cannot find stdio.h, sys/types.h, and similar files.

At this point I'm kind of hoping there is a batch set of libraries somewhere in a single download I can grab that has all of the dependencies required to build GCC. Once I have GCC installed, I'm hoping that will be enough to get ndiswrapper compiled and installed, so I can start using my wireless card.

Oh, and **I don't have internet on my Ubuntu computer**, not sure if that will matter or not. I've been having to transfer files from my laptop to my linux (ubuntu) box. I hope someone can help, Microsoft has really spoiled me and I am ripping my hair out trying to adjust to Linux. I'm getting very discouraged :(

---

### Post by jespdj on 2008-05-15
Is there a special reason why you need GCC version 4.3?

Maybe you're making it much more difficult than necessary. Try installing the basic build tools (including GCC and the header files for C and C++) instead of manually compiling GCC 4.3:
```
sudo apt-get build-essential
```

---

### Post by Sef on 2008-05-15
> Oh, and **I don't have internet on my Ubuntu computer**, not sure if that will matter or not. I've been having to transfer files from my laptop to my linux (ubuntu) box. I hope someone can help, Microsoft has really spoiled me and I am ripping my hair out trying to adjust to Linux. I'm getting very discouraged (Bold added by mod.)

You could go to [packages.ubuntu.com]("http://packages.ubuntu.com"). You can download the packages and check the dependencies and download those as well.

---

### Post by WalkingMist on 2008-05-20
> Is there a special reason why you need GCC version 4.3?

Yes, I do need gcc 4.3 to compile the nightly build of  deluge-torrent client. 

I tried to "apt-get install", but I am not sure if I am using the correct package name so it can't find what I wanted to install.

Can someone point out the correct package name to use to get gcc 4.3 installed?

Thanks!!

---

### Post by thotmos on 2008-05-20
[http://packages.ubuntu.com/hardy/devel/build-essential]("http://packages.ubuntu.com/hardy/devel/build-essential")

---

