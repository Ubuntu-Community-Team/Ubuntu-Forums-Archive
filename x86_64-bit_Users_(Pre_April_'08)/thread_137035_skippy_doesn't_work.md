---
title: "skippy doesn't work"
date: 2006-02-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by bato on 2006-02-27
Hi,
I have a hp compaq nx 6125 with amd turion64 and I 'm trying to install skippy.
I have already installed skippy on my workstation without problems, but on my laptop it dosen't work well.

I have installed by synaptic then I copied skippy-deault from tarball on [http://thegraveyard.org/skippy.php](http://thegraveyard.org/skippy.php) into my /home/bato/.skippyrc, finally I edited this file and set Keysym=Scroll_Lock.

> skippy &

and it start but when I press scroll lock it got this error:> 
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  2 (X_ChangeWindowAttributes)
  Resource id in failed request:  0x0
  Serial number of failed request:  103
  Current serial number in output stream:  105

I try with other key [F11, F12] too but the same error occours.

Any ideas?

---

### Post by alesdoc on 2006-02-27
I've an HP NX6125 too. I don't try to intall skippy yet.

Have you read the wiki page about it?

[https://wiki.ubuntu.com/Skippy?highlight=%28skippy%29](https://wiki.ubuntu.com/Skippy?highlight=%28skippy%29)

---

### Post by bato on 2006-02-27
Hi alesdoc,
I didn't read that wiki but I discovered that I did the same like the wiki explain.
So when (and if) you try skippy let me know if it works for you please.
Thanks

PS. Have you installed the ati driver (fglrx)? I saw [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584) but I don't try it yet, I only setted NoAccel in xorg.conf and it works but I'd like to know if driver ati works well in this laptop

---

### Post by alesdoc on 2006-02-27
The Driver ATI works properly but:

-> If you installa new kernel you have to follow the same howto again

-> Some problem with some fonts....for istance i can not start emacs

-> The touch-pad doesn't work fine...you can not use the scrolling for example.

---

