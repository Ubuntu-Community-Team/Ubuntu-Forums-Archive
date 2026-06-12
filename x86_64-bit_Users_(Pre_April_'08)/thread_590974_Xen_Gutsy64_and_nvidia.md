---
title: "Xen Gutsy64 and nvidia"
date: 2007-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by lexii on 2007-10-25
Hi,

I'm having troubles getting Xen as Dom0 in Gutsy64 running with nvidia. I have the same problems as wout.wepsait.com describes in [this post]("http://ubuntuforums.org/showthread.php?t=560720"). 

Everything works fine without nvidia (restricted modules), but with nvidia drivers activated I get a kernel crash (SCRL+NUM lock flashing) as soon as the initscripts start the  X-Server. I have the same effect on two different machines (one Laptop and one Desktop, both with Core2Duo).

After searching the forums and the net I couldn't find any references...Is it just me having these problems?

---

### Post by thearthur on 2007-10-30
I have this same problem on a ThinkPad T61.
 when i boot into single user mode i can verify that the nvidia kernel loads.

---

### Post by parann0yed on 2007-11-01
I've been having problems also. After enabling the restricted modules and rebooting, I get the blank screen and am unable to get even a virtual console.  The only way out is to revert to an older, non-xen kernel.   I even went so far as trying installing with envy.

Viewing the failure log from envy, I understood the nvidia binary drivers do not yet work with the xen kernels.  I'd be very interested in knowing if/when they will be supported.  Overall, the newest version of ubuntu has been great, however I've also had problems with firefox on java/flash sites.

---

### Post by nelsonb73 on 2007-11-02
This worked for me [http://thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p]("http://thinkwiki.org/wiki/Install_Ubuntu_Gutsy_Gibbon_on_a_T61p")

---

### Post by ttthebear on 2007-11-07
have the same problem.

Going to attempt to do something like this

[http://www.debian-administration.org/articles/493]("http://www.debian-administration.org/articles/493")

If I manage to get it working I will post it.

---

