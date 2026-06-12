---
title: "[SOLVED] ATI Config - What am I doing wrong?"
date: 2007-07-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-07-07
[B]charles@K8N-Neo4-Platinum-SLI:~$ aticonfig --initial=dual-head
Found fglrx primary device section
Found fglrx secondary device section
screen layout section corrupted 
aticonfig: parsing the command-line failed.
charles@K8N-Neo4-Platinum-SLI:~$ aticonfig --initial=dual-head
Found fglrx primary device section
Found fglrx secondary device section
screen layout section corrupted 
aticonfig: parsing the command-line failed.
charles@K8N-Neo4-Platinum-SLI:~$ [/B]

I'm trying to activate the second head in my ATI Card.  What am I doing wrong?  How can I tell if the driver is properly installed?

---

### Post by crjackson on 2007-07-07
Is this going to be another -0- reply thread?

---

### Post by crjackson on 2007-07-08
I can't seem to get any help here.  Could someone point me in the right direction?  If there is a better forum site to ask this question in please let me know.

---

### Post by crjackson on 2007-07-08
[SIZE="6"][FONT="Arial Black"]**HELLO! Can someone help please?**[/FONT][/SIZE]

---

### Post by jocko on 2007-07-09
Patience! People are still sleeping in here in europe!

Have you tried adding sudo before the command:
```
sudo aticonfig --initial=dual-head
```
If that doesn't help, try to start with a fresh copy of /etc/X11/xorg.conf:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And then run aticonfig again.

---

### Post by crjackson on 2007-07-24
[B]charles@K8N-Neo4-Platinum-SLI:~$ aticonfig --initial=dual-head --screen-layout=above
Found fglrx primary device section
Found fglrx secondary device section
screen layout section corrupted 
aticonfig: parsing the command-line failed.
charles@K8N-Neo4-Platinum-SLI:~$ 
[/B]

---

### Post by John.Michael.Kane on 2007-07-24
If your trying to run dual monitors you may want to look at one of these.

[ATI Big-Desktop]("http://ubuntuforums.org/showthread.php?t=301941&highlight=ATI+x800XL")

[HowTo: Dual Monitors (Xinerama/TwinView/MergedFB/Big-Desktop)]("http://ubuntuforums.org/showthread.php?t=221174")

---

### Post by crjackson on 2007-07-24
Thanks SD - I don't have dual monitors right now.  I just wanted to get the dual head feature enabled and ready.  Could it be that the feature won't enable until a second monitor is attached?

---

### Post by John.Michael.Kane on 2007-07-24
It "might" rely on there being two monitors hooked up, as the resolution will be spread out across the two monitors not just one you currently have.


This is a guess. If your sure the second monitor will have the same specs as your current one then you should be able to use your current monitor while it's plugged into he second video port to set up the dual config. 

Note: Make sure you comment out the second dual config using # so it's not pass during the boot process.

hope it helps.

---

### Post by crjackson on 2007-07-24
> **SD-Plissken said:**
> It "might" rely on there being two monitors hooked up, as the resolution will be spread out across the two monitors not just one you currently have.


This is a guess. If your sure the second monitor will have the same specs as your current one then you should be able to use your current monitor while it's plugged into he second video port to set up the dual config. 

Note: Make sure you comment out the second dual config using # so it's not pass during the boot process.

hope it helps.

I may do that this weekend.  I have about 10 monitors around the house I can try.  A new ATI driver was released yesterday.  I just installed it and so far so good.  I have no idea what it changes or fixes though.

---

### Post by kidguayas on 2007-08-23
I have similar problem. I was able to use aticonfig and do the configuration.  However, when I restart the computer, I don't get to extended desktop desire. Does anyone have an idea?

---

### Post by crjackson on 2007-08-23
> **kidguayas said:**
> I have similar problem. I was able to use aticonfig and do the configuration.  However, when I restart the computer, I don't get to extended desktop desire. Does anyone have an idea?

Sorry, I gave up on it to work on other issues.  It's not a priority for me.

---

### Post by kidguayas on 2007-08-23
I just fix it thanks, anyways

---

### Post by crjackson on 2007-08-23
> **kidguayas said:**
> I just fix it thanks, anyways

Well don't leave me hanging.  How did you fix it?  I would like to know also...

---

### Post by kidguayas on 2007-08-23
try this: sudo aitconfig --initial dual-head --screen-layout=left

---

### Post by revchris on 2007-10-09
Yes, You need to have "sudo" in front of "aticonfig"

---

### Post by crjackson on 2007-10-24
> **kidguayas said:**
> try this: sudo aitconfig --initial dual-head --screen-layout=left

Thanks - I guess it's working because it reports "Nothing to do"

---

