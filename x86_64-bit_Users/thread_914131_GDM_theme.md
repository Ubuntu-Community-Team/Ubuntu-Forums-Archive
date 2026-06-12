---
title: "GDM theme"
date: 2008-09-08
forum: x86 64-bit Users
---

### Post by michaelkahl on 2008-09-08
I've been having problems on my work machine getting GDM themes to stick.  I've had both 32 and 64 bit running on the same machine.  Since I've only had this issue in 64 bit I thought I'd post the fix incase other users are experiencing the same issue.  I found this in an old archived post, 
**posted by YetZero**

"Whoah, I got it. Usually as you run gdmsetup you're actually editing the file /etc/gdm/gdm.conf-custom, as I ran xgl I edited the file and deleted it for starting xorg again. So if the changes don't stay when you edit gdmsetup, it's most likely that you don't have a gdm.conf-custom file. The solution is to copy the default gdm.conf into a gdm.conf-custom:

Code:

sudo cp /etc/gdm/gdm.conf /etc/gdm/gdm.conf-custom

That worked for me."

---

