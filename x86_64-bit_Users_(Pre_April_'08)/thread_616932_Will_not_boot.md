---
title: "Will not boot"
date: 2007-11-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Maintech on 2007-11-18
I am trying to boot 7.10 live 64. I get a kernel panic at the very beginning. I've tried loading with "noapic nlapic" but what really seems to be the issue is it can't seem to find my hard drives. This is what I am running:

Abit IP35 motherboard
Intel Q6600 Quad-Core
4 x 1 Gig DDR2
Nvidia GeForce 8800
Lite-On DVDRW
4 x 250 Gig SATA 2

I have SuSE installed as dual boot but I dislike SuSE and have used Ubuntu for most of my linux needs. I will not list the reasons I dislike SuSE here in this post but they are (for me) good reasons. Mandriva also gives the same issue as Ubuntu. Kernel panic ... can't find VFS. 

Any help would be greatly appreciated.

---

### Post by gsiliceo on 2007-11-18
I dont know about your problem other than sometimes blacklisting devices fixes this but your box is pretty impressive :D

---

### Post by Maintech on 2007-11-19
Surely there is someone out there with the new Intel chipset. I mainly need to know what to enter in the boot parameters to tell the OS what chipset/hard drive controller I am using. I have been unable to find anything that details what the correct boot parameter would be.  :confused:

---

### Post by John.Michael.Kane on 2007-11-19
> **Maintech said:**
> Surely there is someone out there with the new Intel chipset. I mainly need to know what to enter in the boot parameters to tell the OS what chipset/hard drive controller I am using. I have been unable to find anything that details what the correct boot parameter would be.  :confused:

The issue you are having seems to be a known problem on these forums. most workarounds for this issue require the user to have their drives boot in ide mode. I'm not sure if the board you have will allow for that.

[http://ubuntuforums.org/showpost.php?p=3683910&postcount=10](http://ubuntuforums.org/showpost.php?p=3683910&postcount=10)

[http://ubuntuforums.org/showpost.php?p=3372889&postcount=47](http://ubuntuforums.org/showpost.php?p=3372889&postcount=47)

---

### Post by Maintech on 2007-11-19
> **SD-Plissken said:**
> The issue you are having seems to be a known problem on these forums. most workarounds for this issue require the user to have their drives boot in ide mode. I'm not sure if the board you have will allow for that.

[http://ubuntuforums.org/showpost.php?p=3683910&postcount=10](http://ubuntuforums.org/showpost.php?p=3683910&postcount=10)

[http://ubuntuforums.org/showpost.php?p=3372889&postcount=47](http://ubuntuforums.org/showpost.php?p=3372889&postcount=47)

Ahhh. Thanks. I have an IDE cd/dvd and SATA hard drives. Great!! No Ubuntu. Wonder why SuSE and Fedora will install just fine but Ubuntu won't?? I had SuSE (which I dislike) installed and replaced it with Fedora (which I don't like much either but is better than SuSE). I guess I'm stuck with Fedora until Ubuntu can determine why their OS won't install like some other linux will.:evil:

---

### Post by John.Michael.Kane on 2007-11-19
> **Maintech said:**
> Ahhh. Thanks. I have an IDE cd/dvd and SATA hard drives. Great!! No Ubuntu. Wonder why SuSE and Fedora will install just fine but Ubuntu won't?? I had SuSE (which I dislike) installed and replaced it with Fedora (which I don't like much either but is better than SuSE). I guess I'm stuck with Fedora until Ubuntu can determine why their OS won't install like some other linux will.:evil:


Sorry I could not be of more help on this issue. At very least you should take notes of any errors etc, and file a bug report so that a fix can be implemented by the kernel dev's provided it's even possible.

---

