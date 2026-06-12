---
title: "Bug in Gutsy"
date: 2007-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by go_beep_yourself on 2007-11-23
I am surprised this isn't fixed yet. If I use the mouse scroll button to change the volume in with the icon in the gnome panel, then I will get a muted icon when the sound is not muted.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=51095&d=1195797852[/IMG]

---

### Post by Kilz on 2007-11-23
Did you report your bug on launchpad? Because posting it here to us users will never see anything ever done about it.

---

### Post by azbarcea on 2007-11-23
I don't use Gnome, but KDE, but let me take a guess:

First, I'm not sure is a bug: the Icon (button) shows you not the state of the volume, but **what happens if u click on it**. I find this feature annoying too, because it can be found in many other apps. (like amarok), It shows you not the STATE, but what will happen if you click on it!

Second, I'm sure u can change this in some config file, if you really want to. I'll search for this config and I'll tell you if it really bugs you, but please confirm it!

---

### Post by go_beep_yourself on 2007-11-23
Does this happen to anyone else?

---

### Post by david_2001 on 2007-11-23
> **go_beep_yourself said:**
> Does this happen to anyone else?
No, but I'm not using gutsy.  I am running gnome 2.20.1 though.

---

### Post by go_beep_yourself on 2007-11-23
> **david_2001 said:**
> No, but I'm not using gutsy.  I am running gnome 2.20.1 though.

What are you using?

---

### Post by david_2001 on 2007-11-23
Arch Linux

---

### Post by go_beep_yourself on 2007-11-24
> **david_2001 said:**
> Arch Linux

Is that a distro where everything is compiled from source code like Linux from Scratch and Gentoo?

---

### Post by macaholic on 2007-11-24
Same thing happens to me (Ubuntu gutsy 64 bit), but I don't really care, I just use the volume keys on my keyboard.

---

### Post by azbarcea on 2007-11-26
> Does this happen to anyone else?

In my KDE it doesn't. Have u fixed it, because otherwise I'll install an Ubuntu Gutsy VM and we'll find out what's happening ... so please reply!

---

### Post by rsambuca on 2007-11-26
Mine never does that.  Try re-installing the gnome volume control.

---

### Post by david_2001 on 2007-12-01
> **go_beep_yourself said:**
> Is that a distro where everything is compiled from source code like Linux from Scratch and Gentoo?
No, it's a binary distribution.  It's like Slackware but with better package management 8)

---

### Post by Kilz on 2007-12-01
Who installs a whole distro for the sake of not having to right click on the volume icon and deselecting mute? No distro is perfect. No operating system is perfect.

---

### Post by go_beep_yourself on 2007-12-01
> **Kilz said:**
> Did you report your bug on launchpad? Because posting it here to us users will never see anything ever done about it.

Yes, and it was marked as a duplicate.

---

### Post by Rhubarb on 2007-12-01
I'm running Ubuntu Gutsy 64 bit here, my volume control works perfectly here.
When I scroll down to no volume, it is muted, when I start scrolling up, the volume goes up and is (and displays as) unmuted as it should.

---

### Post by david_2001 on 2007-12-02
> **Rhubarb said:**
> I'm running Ubuntu Gutsy 64 bit here, my volume control works perfectly here.
When I scroll down to no volume, it is muted, when I start scrolling up, the volume goes up and is (and displays as) unmuted as it should.
It took a bit of searching (I've never found Launchpad intuitive to use) but I think that the problem is related to a bug described at [https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/151877](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/151877).  It seems that it only afflicts those with certain types of sound hardware.

---

### Post by bpazolli on 2007-12-02
It happens to me. I am running 7.10 but it seems to flicker back and forth as I scroll and I can't get it to stay at the muted position so I can get it to show correctly. Seems pretty simple bug though. Seems to be worst when scrolling fast.

---

