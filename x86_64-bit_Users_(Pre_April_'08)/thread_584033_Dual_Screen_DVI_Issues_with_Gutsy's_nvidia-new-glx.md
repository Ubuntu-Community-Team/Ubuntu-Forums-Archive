---
title: "Dual Screen DVI Issues with Gutsy's nvidia-new-glx driver and/or Envy's BLOB driver"
date: 2007-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by MiiJaySung on 2007-10-20
Hi, does anyone have any hints to stop X from randomly hanging while using the nvidia driver. I have two Dell 2001 FP screens on DVI out, and enabling both makes XOrg very unstable. I've tried both the nvidia-new-glx restricted drivers that come with Gutsy and the NVidia BLOB drivers that install via Envy. 

I'm using a 6800GT, which I would expect to be pretty stable given that it's not *that* new. This coupled with the issues (in another post) regarding my motherboard's SATA is driving me mad and is forcing me to use Ubuntu through VMware on Windows which is sub optimal given the fact I work in Linux more than Windows.

Does anyone have any good suggestions here. It appears this has been an issue for a while in general in Linux thanks to Nvidia's stubborness to do anything for these small set of "power users", and their general "screw you" attitute to the situation by not helping the open source community develop quality drivers (which would good gesture seeing as they are unable to pool the human resources to develop a decent closed source driver).

This is really frustrating the hell out of me as it seems there is no easy way to have a Dual DVI setup in Linux that is relatively stable (and ideally painless as well).

---

### Post by MighMoS on 2007-10-24
Unfortunately, as you know, nVidia's drivers are proprietary, so if they don't work, there isn't too much you can do except work *around* the issue.  I've heard  that Dual DVI cards tend to have buggy hardware, which you seem to be experiencing, so bugs have to be worked around in the hardware.</backstory>

A lot of times the computer hasn't crashed, but the drivers have just screwed up X.  

A few things you can try are:
* If you have access to a second computer, try using SSH to remotely connect to the one that crashes. Type in dmesg and if you see anything alarming, that could be the cause of your issue.
* If you don't have access to a second computer, or the first step didn't work, try rebooting, and then looking at the log file /var/log/X.org.0.old (this will be the *last* instance of X, and the last few lines could reveal what's going wrong.
* Use the free nv driver.  It wont have 3d acceleration, but it shouldn't crash either.
* Lastly, if you're up to it (and this is not always easy stuff) I would recommend checking out the nouveau driver.  They're developing a free nVidia driver, and would love some information on how Dual DVI cards work.  Drop into #nouveau on IRC and participate.

---

