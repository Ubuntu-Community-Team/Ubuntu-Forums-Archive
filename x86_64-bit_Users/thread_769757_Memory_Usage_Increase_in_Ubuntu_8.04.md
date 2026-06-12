---
title: "Memory Usage Increase in Ubuntu 8.04?"
date: 2008-04-26
forum: x86 64-bit Users
---

### Post by ClamChowder on 2008-04-26
Has anyone noticed a large increase in memory usage after upgrading to 8.04? For me, the memory usage for the system (with no applications running) is almost twice as large as 7.10. The system also feels more sluggish than 7.10. Can anyone help explain this? 

Also, I have been unable to get the memory usage for several applications in the System Monitor using the processes tab. For Firefox, evolution, kword, gnome-panel, nautilus, and several other applications, the memory usage shows up as 17179869180.1 GiB, which I find to be rather ridiculous and untrue.

Is anyone else seeing this? Any advice? Thanks in advance!

---

### Post by dokdoom on 2008-04-26
If you run top does it display the same memory usage as the gui?

---

### Post by eznet on 2008-06-24
I am getting the same error in the Gnome System Monitor, though top does not show the same values.

---

### Post by soxs on 2008-06-25
7.10 notracker
8.04 tracker

this my be the diffrence
Fix: simply disable tracker from System->Preferences->Session

---

### Post by TenPlus1 on 2008-06-25
Most of the new features in 8.04 Hardy are disabled on my desktop so I can reclaim well-needed memory...  Things like tracker/pulse-audio and a host of services and sessions are disabled so my system sits at 90mb usage on desktop :)

Also, the gnome-bar is not 20-26mb because of the timezone and weather functions it now contains, so this is adding to the memory also, even if oyu dont use them...

---

### Post by soxs on 2008-06-25
Btw.. totally free memory is wasted memory..

---

### Post by stchman on 2008-06-25
> **ClamChowder said:**
> Has anyone noticed a large increase in memory usage after upgrading to 8.04? For me, the memory usage for the system (with no applications running) is almost twice as large as 7.10. The system also feels more sluggish than 7.10. Can anyone help explain this? 

Also, I have been unable to get the memory usage for several applications in the System Monitor using the processes tab. For Firefox, evolution, kword, gnome-panel, nautilus, and several other applications, the memory usage shows up as 17179869180.1 GiB, which I find to be rather ridiculous and untrue.

Is anyone else seeing this? Any advice? Thanks in advance!

If you are going form 32 bit Gutsy to 64 bit Hardy then yes you will use more memory.  When I was running 32 bit I could not get the memory usage up to 500MB.  Now it routinely goes over 900MB using 64 bit.

64 bit OS and apps have larger pointers and arrays.

---

### Post by eznet on 2008-06-25
Not to be too blunt here, but did you all read the initial post?  System Monitor was reporting multiple programs to be using **_17179869180.1 GiB_** of memory - I don't care what your system is, what its processor is and how many of them it has or even how many programs you are running for that matter, it is not going to use 17179869180.1 GiB of memory.  
To my knowledge, there isn't a system in existence, certainly no personal desktop, that has 17179869180.1 GiB of memory in it - hence, the reporting of such is a bug and not a manifestation of any real increased utilization of memory.:lolflag:
I do, however, think that this bug relates to xserver-xgl.  I use my System Monitor quite often and never noticed this bug until installing it.  I installed xserver-xgl because of [screen flickering and random freezing]("http://ubuntuforums.org/showthread.php?p=5263277") issue.  Unfortunately, the bugs that accompanied xserver-xgl were more difficult to cope with than the flickering.
Going to hunt bug reports...

---

