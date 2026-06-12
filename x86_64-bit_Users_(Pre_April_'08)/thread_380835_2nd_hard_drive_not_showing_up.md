---
title: "2nd hard drive not showing up"
date: 2007-03-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by Zawn on 2007-03-10
Hey, total linux noob here. After hours of trial and error, searching the forums, searching google, I finally got ubuntu 6.10 installed on my machine. I got past all the black screen when trying to install, setting the video card drivers to vesa without being able to boot into ubuntu, and updating the video drivers, without having to post anything. But now I need help getting my 2nd hard drive to show up. It has all my music on it and that's basically half of my computers use.

I assumed that when I go to places>computer that it would show up but it doesn't. It showed up when I went to install ubuntu, and It's not a dead drive, so I don't quite understand why it's not there now. Ideas?

Also, a question about wine, which I know doesn't belong here but I'll throw it up for idea's anyways. I'm trying to install on my 64 bit OS here and every time i try this hack from the wine wiki:

```
cd ~/Desktop 
sudo dpkg --force-architecture -i wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb
```

I get this error back


```
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 106789 files and directories currently installed.)
Preparing to replace wine 0.9.32~winehq0~ubuntu~6.10-1 (using wine_0.9.32~winehq0~ubuntu~6.10-1_i386.deb) ...
Unpacking replacement wine ...
dpkg: dependency problems prevent configuration of wine:
 wine depends on libartsc0 (>= 1.5.0-1); however:
  Package libartsc0 is not installed.
dpkg: error processing wine (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine
```

Here are my specs:
AMD 3400+
1.2 Gigs of ram
Abit Radeon 9800 XT
ASUS mobo
Abuntu 6.10

---

### Post by John.Michael.Kane on 2007-03-10
If your mounting a non ntfs drive ie: just for storage read this:
[**Mounting Linux Partitions/Drives**]("http://www.psychocats.net/ubuntu/mountlinux")

For ntfs mounting you can use one of these methods:
[ **Mounting Windows Partitions**]("http://www.psychocats.net/ubuntu/mountwindows")
[**ntfs-3g how to**]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntsf-3g")

For wine you can try this:
[**Install wine to 64 bit**]("http://www.ubuntuforums.org/showthread.php?t=185557")

And if you need the codecs for movie play back ect look here:
[**Gstreamer**]("http://www.ubuntuforums.org/showpost.php?p=2205606&postcount=3")
[**Howto Install 32 bit Firefox with Flash w/sound and Java for AMD64**]("http://www.ubuntuforums.org/showthread.php?t=202537&highlight=java")

---

### Post by Zawn on 2007-03-10
I tried all of these, none of them worked, i'll probably be wiping and returning to windows, linux is just to hard and uncooperative.

---

### Post by Kilz on 2007-03-11
> **Zawn said:**
> I tried all of these, none of them worked, i'll probably be wiping and returning to windows, linux is just to hard and uncooperative.

Yes for those that have trouble reading and following instructions it can be.

---

### Post by John.Michael.Kane on 2007-03-11
> **Zawn said:**
> I tried all of these, none of them worked, i'll probably be wiping and returning to windows, linux is just to hard and uncooperative.

Just telling us it's too hard ect is not going to allow you get the help you need.

If you still wish to use ubuntu please post any error msg or issue your having.

---

### Post by ztirffritz on 2007-03-11
I'm having a similar problem. The drive is mounted and it is accessible if I navigate to /mnt/brain, but I want a link or an icon on the desktop.  How do I do that.

---

### Post by ztirffritz on 2007-03-11
> **Zawn said:**
> I tried all of these, none of them worked, i'll probably be wiping and returning to windows, linux is just to hard and uncooperative.

It is important that you learn the difference between "different" and "difficult".  You know Windows, but to someone who only knows Linux or Mac OS Windows doesn't work very well or make sense either.

---

