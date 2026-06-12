---
title: "Enabling VIA Unichrome Direct Rendering in AMD64? [Resolved]"
date: 2007-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by ryan76 on 2007-01-05
Hi all

I've tried various things but I don't know what to do next. Quite a n00b although I may sound like I know what I'm doing. 

I have the S3 Via Unichrome K8M800 graphics card which is set up correctly to play DVDs, so it's working fine. I'm trying to set up 3d rendering so I can use mednafen (NES emulator and yes I own the games). I have a GP32 handheld so I'm trying to test games before I put them on the unit.

I tried the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=124604](http://ubuntuforums.org/showthread.php?t=124604)
but it didn't work. They mention that if you compile the 2.6.16 kernel you can enable Direct Rendering.

uname -r gives me this kernel: 2.6.15-27-amd64-generic

So shouldn't I be able to enable Direct Rendering with this kernel? If so, how? 

I'm at a dead end right now so any help is appreciated.

---

### Post by ryan76 on 2007-01-08
Hi, I have since tried the instructions here: [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Can someone please point me in the right direction? Thanks

---

### Post by ryan76 on 2007-01-19
What a great response. Thanks everyone

---

### Post by Vox754 on 2007-01-19
I don't know what you are talking about. I just wanted to say that I too have a K8M800 board and it works fine for my needs.
Actually, I installed the 64-bit Ubuntu 6.06 but after reading that many things, like flash, win32codecs and so, didn't quite work I decided to install the i386 version for Ubuntu 6.10.

The only problem that I had was that in the "/etc/X11/xorg.conf" it used the "vesa" driver instead of "via". I changed that.
Still there seems to be a lack of support for 3D.
[http://ubuntuforums.org/showthread.php?t=342115&highlight=K8M800](http://ubuntuforums.org/showthread.php?t=342115&highlight=K8M800)

You should get and compile the new kernel as it says.
Good luck.

---

### Post by ryan76 on 2007-01-20
Thanks. I compiled the kernel which supposedly has Via drivers in it and DRI still isn't working.

Latest: Installed Edgy, now DRI works.

---

